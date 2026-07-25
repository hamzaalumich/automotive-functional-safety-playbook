# Software and Integration Evidence

## Software safety intent

Software evidence must show that safety requirements are correctly implemented, timing and state behavior are controlled, interfaces reject invalid information, and lower-integrity or non-safety elements cannot interfere with safety-related behavior.

## Evidence stack

| Level | Typical evidence |
|---|---|
| Requirements | Completeness, consistency, testability, traceability |
| Architecture | Partitioning, interfaces, state machines, scheduling, resource budgets |
| Unit design | Defensive behavior, data validity, control flow, numerical limits |
| Implementation | Coding rules, static analysis, reviews, complexity, tool confidence |
| Unit verification | Requirements-based tests, boundary tests, structural coverage where applicable |
| Integration | Interface tests, timing, communication faults, resource contention |
| System verification | Fault response, degraded state, end-to-end timing, diagnostics |

## Freedom from interference

Potential interference channels include:

- memory overwrite or corruption;
- execution-time overrun;
- task starvation or priority inversion;
- shared peripheral misuse;
- communication buffer exhaustion;
- common operating-system service failure;
- clock, reset, or power-management interaction; and
- uncontrolled calibration or diagnostic access.

Evidence may include memory protection, timing analysis, partitioning, interface contracts, resource monitoring, scheduler analysis, integration stress tests, and fault injection.

## Safety communication behavior

Safety-related communication mechanisms may address:

- corruption;
- repetition;
- loss;
- insertion;
- incorrect sequence;
- delay;
- masquerading; and
- inconsistent sender/receiver state.

End-to-end protection can include CRC, sequence counters, data identifiers, timeout monitoring, freshness checking, plausibility, and source authentication where required by coordinated safety and cybersecurity concepts.

## Watchdog design

A watchdog should supervise meaningful execution, not only periodic toggling. Strong implementations may use:

- time-window monitoring;
- challenge-response sequences;
- program-flow checkpoints;
- independent clocking;
- task-level deadline monitoring;
- external hardware supervision; and
- controlled reaction and restart logic.

Verification should demonstrate detection of representative hangs, timing violations, incorrect flow, and failed reaction paths.

## Integration evidence

Integration testing should prove that the implemented hardware and software cooperate to achieve the safety behavior. Key evidence includes:

- signal scaling and boundary behavior;
- startup and shutdown sequences;
- timing under worst-case load;
- network timeout and corruption response;
- sensor plausibility and fallback;
- output disable and feedback confirmation;
- reset and recovery behavior;
- diagnostic latching and clearing rules; and
- behavior under multiple or sequential faults.

## Back-to-back and model-based evidence

Where models or generated code are used, back-to-back testing compares defined representations using controlled vectors, tolerances, and acceptance criteria. It supports equivalence claims but does not replace requirements-based verification or system-level fault-response testing.
