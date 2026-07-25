# FMEA Risk Lens Framework

## Purpose

The **FMEA Risk Lens** is an original, automotive-electronics-oriented method for making FMEA ratings more consistent, explainable, and useful during design reviews. It preserves the familiar Severity–Occurrence–Detection structure while requiring an evidence statement beside every score.

The framework is designed to solve four recurring problems:

1. ratings selected from memory rather than project evidence;
2. detection controls credited without a clear fault model;
3. high-severity items hidden by a moderate Risk Priority Number; and
4. action lists that do not connect back to architecture or verification.

> **Boundary:** This is a configurable project aid, not an official AIAG-VDA, ISO, or customer-specific ranking table. Tailor the language, escalation rules, and quantitative anchors to the organization and product.

<div align="center">
  <img src="../assets/fmea-risk-lens.svg" alt="FMEA Risk Lens showing severity, occurrence, detection, and response lanes" width="96%">
</div>

---

## The three evidence lenses

### 1. Severity — impact lens

Severity answers:

> **If the failure mode reaches the next level, what is the credible effect at the customer, vehicle, regulatory, or safety-goal level?**

Severity is based on the effect, not on how likely the cause is or how strong the inspection is. Detection improvements do not reduce severity unless the design changes the resulting effect itself.

| Rating | Level | Original rating criterion | Evidence expected |
|---:|---|---|---|
| **10** | Critical safety consequence | The effect could contribute to life-threatening injury or an uncontrolled hazardous vehicle response with little practical opportunity for mitigation | Hazard linkage, vehicle effect, safety-goal relevance, operating scenario |
| **9** | Severe safety or compliance consequence | The effect could contribute to serious injury, loss of a safety-critical function, or major safety-related regulatory noncompliance | Safety analysis, regulatory interface, warning/mitigation assumptions |
| **8** | Primary function lost | The vehicle or product loses a primary function, becomes inoperable, or requires immediate controlled shutdown or recovery | Functional architecture, safe/degraded state definition |
| **7** | Major degradation | A major function is significantly degraded, continued use is restricted, or immediate service is required | Customer/vehicle effect and operational limitation |
| **6** | Functional reduction | A subsystem remains available but with a clear performance, availability, or operating-range reduction | Measured performance boundary and user impact |
| **5** | Customer disruption | The function remains available, but the customer experiences a clear loss of performance, convenience, or confidence | Requirement deviation and customer-visible symptom |
| **4** | Minor deviation | A limited performance deviation exists and a practical workaround is available without material risk | Requirement comparison and workaround description |
| **3** | Nuisance | The effect is noticeable but does not meaningfully reduce the intended function | Observable symptom and no-loss rationale |
| **2** | Trace effect | The effect is barely perceptible and does not change normal use | Measurement result or tolerance comparison |
| **1** | No meaningful effect | No credible customer, vehicle, manufacturing, or downstream functional effect is identified | Analysis showing containment or irrelevance |

### 2. Occurrence — recurrence lens

Occurrence answers:

> **How credible is the cause or failure mechanism in the defined design and operating context?**

A strong occurrence rating is based on evidence such as design margins, supplier capability, process data, reliability prediction, validation results, field returns, or a demonstrated physical mechanism. The score should not be copied between unrelated products.

| Rating | Level | Original rating criterion | Evidence expected |
|---:|---|---|---|
| **10** | Persistent | The cause is active in normal conditions and the failure is routinely reproduced | Repeated test or field evidence with normal use conditions |
| **9** | Very frequent | The cause is commonly encountered and requires little combination of conditions | High-frequency data, weak margin, dominant mechanism |
| **8** | Recurrent | The failure repeats across builds, units, environments, or operating cycles | Multi-unit reproduction and cause confirmation |
| **7** | Frequent | The failure occurs in a defined but regularly encountered operating scenario | Scenario frequency and reproduced mechanism |
| **6** | Occasional | A credible cause exists and has appeared in test, production, supplier, or field evidence | Documented events with relevant configuration |
| **5** | Intermittent | The cause is credible but requires a limited combination of conditions or has sparse evidence | Boundary testing, early-life data, mechanism analysis |
| **4** | Infrequent | The cause requires multiple contributing conditions or is strongly reduced by design/process margin | Margin analysis and controlled process evidence |
| **3** | Rare | The cause is physically credible but is expected only near extreme or unusual conditions | Stress analysis, rare-condition exposure, limited evidence |
| **2** | Highly unlikely | The mechanism is difficult to realize within the validated operating envelope | Robust margin, supplier/process capability, no observed events |
| **1** | Remote | No credible cause remains after design review, analysis, and representative validation | Documented prevention evidence and absence of mechanism |

### 3. Detection — control-confidence lens

Detection answers:

> **How confidently will current prevention or detection controls stop the cause or identify the failure before customer or vehicle exposure?**

A low detection score should be awarded only when the control has a defined fault population, test method, timing, coverage rationale, and reaction. “The ECU has diagnostics” is not enough.

| Rating | Level | Original rating criterion | Evidence expected |
|---:|---|---|---|
| **10** | No effective control | No prevention or detection control exists before exposure | Explicit control gap |
| **9** | Field-only discovery | The issue is most likely discovered through customer complaint, field failure, or teardown | Field-detection path only |
| **8** | Weak sampling | Sampling or limited inspection may detect the issue, but escape probability remains high | Sampling plan and known blind spots |
| **7** | Manual dependency | Detection depends heavily on operator judgment, visual inspection, setup, or exact test conditions | Work instruction and human-factor limitation |
| **6** | Partial automated control | An automated control exists but does not cover the complete fault population or operating range | Coverage gaps, test limits, missed-fault analysis |
| **5** | Moderate control | Controls detect many cases, but boundary conditions, timing, or latent faults remain material | Test evidence and residual escape conditions |
| **4** | Robust detection | Automated detection is repeatable, limits are controlled, and reaction is defined | Capability, calibration, thresholds, reaction evidence |
| **3** | Independent detection | A functionally independent monitor detects the fault within the required time and produces a controlled reaction | Independence argument, timing capture, fault injection |
| **2** | Multi-layer control | Independent prevention and detection layers cover the fault with periodic proof or self-test | Layered coverage, proof-test interval, dependency review |
| **1** | Prevention or near-certain control | The cause is prevented by design or automatically detected with validated, near-complete coverage and controlled reaction | Design prevention, validated coverage, configuration control |

---

## Response lanes

The score is not the decision. The **response lane** is the decision.

| Lane | Trigger | Required engineering response |
|---|---|---|
| 🔴 **A — Stop & Escalate** | Severity **9–10**, a possible safety-goal violation, or an uncontrolled hazardous response | Escalate to system/functional-safety leadership; define containment; review safety goal, architecture, safe state, and release impact |
| 🟠 **B — Architecture Action** | Severity **7–8** with weak occurrence or detection control; single-point dependency; inadequate independence; FTTI concern | Change architecture, monitoring, isolation, fault containment, timing, or reaction strategy; update analysis and requirements |
| 🟡 **C — Design Action** | Material design/process risk, worsening trend, incomplete verification, or project-defined RPN/action threshold | Assign corrective action, owner, due date, verification method, and residual rating target |
| 🟢 **D — Control & Monitor** | Low impact with stable prevention/detection evidence and no escalation trigger | Maintain controls, monitor trend, and preserve evidence/configuration |

### RPN use rule

```text
RPN = Severity × Occurrence × Detection
```

RPN may help sort comparable items inside one project, but it must not override:

- a Severity 9–10 escalation;
- a safety-goal linkage;
- a credible single-point path;
- weak independence or common-cause exposure;
- a violated timing assumption; or
- customer/project-specific mandatory action criteria.

---

## Rating record structure

Each scored line should include more than three integers.

| Field | Required content |
|---|---|
| Function / requirement | The intended behavior and requirement identifier |
| Failure mode | The specific way the function can fail |
| Local effect | Immediate component or circuit effect |
| Next-level effect | Effect on ECU, subsystem, or interface |
| Vehicle/customer effect | Highest credible effect in context |
| Severity rationale | Why the effect maps to the selected rating |
| Cause / mechanism | Physical, systematic, process, software, or interface cause |
| Occurrence evidence | Test, field, process, supplier, reliability, or margin evidence |
| Prevention controls | Design features that reduce the cause |
| Detection controls | Mechanisms that identify the cause or failure before exposure |
| Detection evidence | Coverage, timing, independence, test results, and blind spots |
| Safety relevance | Safety-goal, ASIL, single-point, FTTI, or safe-state linkage |
| Response lane | A, B, C, or D |
| Action and verification | Design action, owner, due date, and evidence required for closure |
| Residual rating | New S/O/D and rationale after verified action |

Use the ready-to-fill [FMEA Risk Review Template](../templates/fmea-risk-review-template.md).

---

## Worked automotive electronics example

### Failure thread

**Function:** Inverter gate-driver shutdown path  
**Failure mode:** Shutdown command cannot disable one power stage  
**Cause:** Shared enable path stuck active following a component short  
**Vehicle effect:** Torque may persist beyond the commanded removal interval

### Initial evaluation

| Lens | Rating | Rationale |
|---|---:|---|
| Severity | **10** | A credible uncontrolled torque path can violate the propulsion safety goal in a relevant operating condition |
| Occurrence | **3** | The short is rare, but physically credible and not eliminated by the original architecture |
| Detection | **8** | The primary controller checks commanded state but lacks independent confirmation that the output stage was actually disabled |

**Initial RPN:** `10 × 3 × 8 = 240`  
**Response lane:** 🔴 **A — Stop & Escalate** because Severity 10 controls the escalation regardless of arithmetic ranking.

### Engineering actions

1. Add an independent hardware disable path that does not share the primary enable node.
2. Monitor gate-driver/output-stage state using feedback independent of the commanded value.
3. Define a shutdown timing budget from fault detection through torque removal.
4. Perform dependent-failure analysis on shared supply, ground, clock, connector, and PCB routing.
5. Inject open, short-to-battery, short-to-ground, stuck-active, and delayed-reaction faults.
6. Capture detection time, reaction time, diagnostic status, and resulting torque state.

### Residual evaluation after verified action

| Lens | Rating | Rationale |
|---|---:|---|
| Severity | **10** | The potential effect remains severe; controls do not change the underlying effect definition |
| Occurrence | **2** | Architecture and component selection reduce the credible initiating path |
| Detection | **2** | Independent feedback, hardware shutdown, proof testing, and fault injection demonstrate layered control |

The residual record should link to requirements, schematic revision, DFA, test procedure, test data, anomalies, and release configuration.

---

## Review prompts

Before approving a rating, ask:

- Is the highest-level effect stated, or only the local component symptom?
- Does the occurrence rating describe the cause in this design, not a generic component reputation?
- Is the detection control independent enough to detect the fault it monitors?
- Is detection timing inside the required fault-tolerant interval?
- Are thresholds, debounce, calibration, power-up, and degraded modes included?
- Has the control been challenged through fault injection or boundary testing?
- Could a shared dependency defeat both the function and its monitor?
- Does the action change the design, or only improve documentation?
- Is the residual score based on completed and verified action rather than planned action?

---

## Ownership statement

The **FMEA Risk Lens**, its response-lane concept, scoring language, diagrams, templates, and examples are original material developed for this repository. They may be adapted for internal project use, but they should not be represented as official ISO, AIAG-VDA, OEM, or regulatory criteria.
