# Release Readiness

## Release is a safety decision

A safety-related release is not only a software build, PCB revision, or production approval. It is a decision that the safety case is sufficiently complete for the intended configuration and context.

## Release dashboard

| Dimension | Release evidence |
|---|---|
| Scope | Item definition and vehicle context are current |
| Risk | HARA, safety goals, and classification rationale are approved |
| Requirements | Safety requirements are allocated, implemented, and traceable |
| Architecture | Safety mechanisms, timing, safe states, and independence are justified |
| Hardware | FMEDA/FTA/DFA/WCCA and hardware verification are current |
| Software | Reviews, analysis, unit/integration results, and timing evidence are current |
| Validation | Fault-injection and vehicle-level safety validation are complete |
| Configuration | Hardware, software, calibration, scripts, and tools are uniquely identified |
| Anomalies | Safety impact is assessed and disposition is approved |
| Suppliers | Assumptions, safety manuals, evidence, and change status are accepted |
| Production | Manufacturing and end-of-line controls protect safety characteristics |
| Operations | Service, update, field monitoring, and recovery obligations are defined |

## Release decision states

### Ready

All required claims are supported, evidence is approved and configuration-correct, and no unresolved anomaly creates unacceptable safety risk.

### Conditionally ready

Release is bounded by explicit limitations, approved deviations, restricted operating conditions, follow-up actions, or controlled production constraints.

### Not ready

A safety claim lacks evidence, a key assumption is unverified, a critical anomaly remains open, or the configuration has changed without completed impact analysis.

## Change reopening logic

A change should reopen affected safety activities when it modifies:

- item scope or operating situation;
- safety goal or requirement behavior;
- threshold, timing, debounce, or fault reaction;
- architecture or independence assumption;
- component, PCB, software, calibration, or supplier element;
- test method or acceptance criteria; or
- production, service, or update process.

## Final review outputs

- approved safety case or safety-case status;
- release configuration record;
- anomaly and deviation disposition;
- assumptions and limitations register;
- confirmation-measure results;
- production and service obligations;
- safety release recommendation; and
- change-control baseline.

Use the [Release Readiness Review](../templates/release-readiness-review.md).
