# Test Plan

**Version:** 0.1 · **Status:** Draft (GestC04; execution GestC13–GestC16)

## 1. Levels
| Level | What it verifies | Tool |
|---|---|---|
| Unit | Authorization rules and each service's logic | Backend framework |
| Integration | A service with its database and queue | Local or QA environment |
| Contract | API and event compatibility (`libs/contracts`) | To be defined |
| End to end | Access request → decision → event → dashboard | Door simulator |
| Load | Performance and limits under heavy use | **k6** |
| Resilience | Behavior under failures | Targeted tests |

## 2. Key cases
- Allowed, denied and conditional access (work order, schedule).
- Credential revocation and its effect on the next access.
- Policy service down: behavior according to ADR-0005.
- A message that fails: it reaches the DLQ and can be reprocessed.
- Duplicate event: it is not processed twice.
- WebSocket connection loss and reconnection.

## 3. Load testing with k6
Scripts live in `tests/load/`.

| Scenario | Goal |
|---|---|
| Smoke | Verify the flow works with 1 user |
| Load | Sustained normal traffic |
| Stress | Ramp up until the limit is found |
| Spike | Sudden increase in requests |

**Initial thresholds (to be calibrated after the first measurements):** p95 latency of the access decision under 500 ms and error rate under 1%.

**Precautions:**
- Large tests consume lab budget; plan them and notify the team.
- Run them from a local machine or a small instance, never against production.
- Record results, configuration and spending.

## 4. Acceptance criteria
The plan is considered fulfilled when the end-to-end flow works in QA, the load thresholds are met or justified, and the tested failures behave as the architecture states.

## 5. Report
Results in `test-report.md` (GestC16).
