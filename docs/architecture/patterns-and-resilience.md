# Design Patterns and Resilience

**Version:** 0.1 · **Status:** Draft (GestC03–04, implementation GestC09–13)

## 1. CQRS
**Commands** (which change state) are separated from **queries** (which read prepared views).
- `access-policy-service`: commands to create and modify roles, areas and rules.
- `access-event-service`: queries over events through read views.
- Reads are **eventually consistent**: a revocation must propagate quickly. That is why policy caches have a short lifetime (TTL) and revocations are published as events.

## 2. Event-driven architecture
Initial catalog (to be completed in GestC03):

| Event | Producer | Consumers |
|---|---|---|
| `credential.revoked` | identity-service | access-policy-service, access-control-service |
| `policy.updated` | access-policy-service | access-control-service |
| `access.granted` | access-control-service | access-event-service |
| `access.denied` | access-control-service | access-event-service |
| `door.opened` | access-control-service | access-event-service |

Every event carries a unique identifier, timestamp, type, version and minimal data.

## 3. Queues and DLQ
- Each consumer reads from its own queue.
- A message that fails after a defined number of attempts moves to the **dead-letter queue (DLQ)**.
- An alarm notifies when the DLQ has messages, and a process (for example a Lambda) allows them to be reprocessed.

## 4. Transactions and consistency (outbox)
To save a database change and publish its event safely, the **outbox** pattern is used: the event is stored in the same transaction and a separate process publishes it afterwards. Consumers are **idempotent** (they ignore an event already processed). Pending: clarify the scope of "transaction alone".

## 5. Circuit breaker
Protects synchronous calls, mainly `access-control-service` → `access-policy-service`.
- States: closed, open and half-open.
- Initial thresholds (to be calibrated with k6): open after 50% failures in a short window; try again after a few seconds.
- With the circuit open, the failure policy from ADR-0005 applies.

## 6. Read views
Dashboard queries use **views** (or materialized views) in the events database, with indexes for the usual filters (area, door, date range). Querying write tables directly is avoided.

## 7. Hash
- **Consistent hashing:** distributes keys (for example doors or WebSocket connections) across several instances, so that adding or removing an instance moves few keys. Whether it is really needed with few instances will be evaluated.
- **Hashing of credentials and secrets:** passwords and tokens with algorithms designed for that (for example bcrypt or Argon2), never in plain text.
- **Audit integrity:** optionally, each record includes the hash of the previous one to detect tampering.

## 8. WebSocket
The dashboard receives events in real time. Details in `frontend.md`. With several service instances, it must be decided how connections are distributed (session affinity or hashing).
