# Fault-Injection Validation

## Purpose

Fault injection is the point where the safety architecture is forced to prove itself. The objective is not merely to trigger a diagnostic code. The objective is to verify the entire chain:

```text
Injected fault
  → physical or logical effect
      → detection
          → confirmation
              → reaction
                  → safe/degraded state
                      → diagnostic evidence
```

## Campaign design

A fault-injection campaign should be derived from:

- safety requirements;
- FMEDA and FMEA fault modes;
- fault-tree cut sets;
- dependent-failure concerns;
- interface failure modes;
- WCCA boundaries;
- software state and timing analysis; and
- known field or production failure mechanisms.

## Fault families

### Electrical

Open circuit, short to ground, short to supply, pin-to-pin short, increased resistance, leakage, drift, loss of supply, ground offset, clock disturbance, and output-stage stuck conditions.

### Communication

Corruption, message loss, timeout, repetition, delay, reordering, stale data, incorrect identifier, and inconsistent counters.

### Software and timing

Task overrun, missed deadline, frozen state machine, corrupted data, incorrect sequence, failed watchdog service, invalid calibration, and delayed reaction.

### Dependency and common cause

Shared supply collapse, common reset, common sensor failure, thermal stress, communication-bus failure, common requirement defect, or loss of a shared shutdown element.

## Test record anatomy

Every test should identify:

- source requirement and safety goal;
- injected fault and injection location;
- operating state and preconditions;
- equipment and method;
- expected detection behavior;
- expected diagnostic status;
- expected reaction and resulting state;
- maximum allowable timing;
- measured timing and waveform/log evidence;
- released hardware/software/calibration configuration;
- deviations and anomaly references; and
- pass/fail rationale.

## Timing capture

The timing measurement should establish clear reference points:

1. fault physically or logically becomes effective;
2. monitor recognizes the fault;
3. fault is confirmed;
4. reaction command is issued;
5. actuator or output reaches the required safe/degraded state.

Measuring only the diagnostic bit transition may miss delays in the physical output path.

## Coverage strategy

Testing every theoretical fault may be impractical. Coverage should therefore be justified using equivalence classes, representative fault selection, analysis, simulation, circuit topology, boundary conditions, and known limitations. The justification belongs in the campaign plan and safety case.

Use the [Fault-Injection Test Record](../templates/fault-injection-test-record.md) and [Campaign Matrix](../data/fault-injection-campaign-matrix.csv).
