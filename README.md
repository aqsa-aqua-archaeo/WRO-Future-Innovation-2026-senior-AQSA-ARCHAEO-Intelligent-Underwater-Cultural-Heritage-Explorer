<div align="center">

# NILEX — Intelligent Underwater Cultural Heritage Explorer

**Team Aqsa Aqua Archaeo · AQSA-Saudi-STEM**

*"Discover the Past. Protect the Future."*

![World Robot Olympiad](https://img.shields.io/badge/World_Robot_Olympiad-2026-1B4F91?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-Future_Innovators%C2%B7Senior-2E86C1?style=for-the-badge)
![Mission](https://img.shields.io/badge/Mission-Robots_Meet_Culture-C0392B?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-4%C3%97EV3_%2B_Arduino_%2B_Camera_%2B_AI_Vision-117864?style=for-the-badge)
![Documentation](https://img.shields.io/badge/Report-20_Sheets_%C2%B7_REV_A-7D3C98?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-In_Development-F39C12?style=for-the-badge)

</div>

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Problem Statement](#problem-statement)
3. [Research Questions](#research-questions)
4. [Design Requirements](#design-requirements)
5. [The Concept](#the-concept)
6. [Idea Development](#idea-development)
7. [System Architecture](#system-architecture)
8. [Mechanical Construction](#mechanical-construction)
9. [Computer Vision & AI Pipeline](#computer-vision--ai-pipeline)
10. [Autonomous Decision-Making](#autonomous-decision-making)
11. [Software Architecture](#software-architecture)
12. [Social Impact](#social-impact)
13. [Real-World Use Case](#real-world-use-case)
14. [Innovation & Business Model](#innovation--business-model)
15. [Responsible AI](#responsible-ai)
16. [Testing & Evaluation](#testing--evaluation)
17. [Roadmap](#roadmap)
18. [Success Metrics](#success-metrics)
19. [The Team](#the-team)
20. [Sources & References](#sources--references)

---

## Project Overview

NILEX is a student-developed robotics concept that connects cultural heritage, robotics, embedded systems, computer vision, and artificial intelligence within a single engineering workflow. The project responds to a real and well-documented challenge: how to explore difficult underwater environments while preserving the evidence and context of submerged cultural heritage. Rather than collecting or disturbing objects, NILEX is designed to observe and document first, producing a repeatable digital record of candidate locations, images, and decisions.

The system integrates four LEGO MINDSTORMS EV3 controllers and an Arduino-based scanning subsystem, dividing the engineering problem into modular, independently testable components. A camera captures candidate objects, and an AI image-analysis pipeline provides visual decision support. Crucially, the AI does not generate uncontrolled robot behavior: every classification result is converted into a small set of predefined, explainable, and safe actions under a non-invasive-first philosophy.

> The goal is not to replace archaeologists. NILEX is a robotic field assistant that collects evidence and supports expert decision-making.

---

## Problem Statement

Submerged cultural heritage — shipwrecks, pottery, tools, sculptures, and structures — constitutes irreplaceable evidence of human history. Its exploration is constrained by conditions that make traditional methods slow, risky, and potentially destructive:

- **Depth** — restricts the duration and safety of human dives.
- **Limited visibility** — complicates manual inspection and documentation.
- **Currents** — destabilize both divers and equipment.
- **Unstable surfaces** — risk damage to fragile materials.
- **Fragile materials** — degrade under direct or repeated contact.
- **Difficult access** — limits how often sites can be visited.
- **Risk to divers** — makes human-first exploration hazardous.

The core constraint identified by the team's research: the problem is not only finding objects — it is protecting fragile materials and the historical information they carry while exploration happens. This insight shaped the entire engineering direction toward sensing, imaging, documentation, and decision support.

---

## Research Questions

Five research questions guided the project from its first sheet to its last. Every requirement and architectural decision traces back to at least one of them.

1. How can underwater exploration become **safer and more repeatable**?
2. How can candidate objects be detected **without immediately disturbing the site**?
3. How can images be documented and analyzed **consistently**?
4. How can a robot **make decisions** from sensor and vision data?
5. How can the system **support archaeologists** rather than making unsupported archaeological claims?

---

## Design Requirements

Eight requirements that every subsystem must satisfy. Each requirement links directly to the research questions above — nothing in the architecture exists without a reason the team can defend.

1. **Scan** a defined area systematically.
2. **Detect** obstacles and potential objects.
3. **Capture** usable images.
4. **Transmit** image data to an AI analysis pipeline.
5. **Convert** AI output into safe, predefined robot actions.
6. **Record** the location and decision for each candidate.
7. **Operate** with a non-invasive-first strategy.
8. **Provide** human override and expert confirmation.

---

## The Concept

NILEX follows one closed engineering loop: **scan → detect → capture → analyze → act only through safe rules**.

The robotic platform sweeps a defined area, identifies regions of interest through its scanning subsystem, positions its camera, and transmits images to the AI pipeline. The AI returns a structured classification with a confidence value, and the decision layer maps that result to one of five predefined safe actions:

- **SEARCH** — continue systematic scanning.
- **INSPECT** — approach a candidate under controlled motion.
- **CONFIRM** — request expert or human authorization.
- **AVOID** — change path safely around an obstacle.
- **CONTINUE** — resume scanning when no candidate is relevant.

### Why This Integration Matters

A camera-only system cannot connect images to movement and sensing decisions; a manual vehicle depends entirely on operator attention; a sensor-only system cannot provide visual evidence. NILEX combines these functions into one workflow, where each stage informs the next and every output is logged.

---

## Idea Development

Four design options were investigated before NILEX was selected:

- **Option A** — A manual remotely operated vehicle controlled entirely by a human. *(Rejected: operator-dependent, no autonomous documentation.)*
- **Option B** — A camera-only underwater inspection robot. *(Rejected: cannot connect images to sensing or movement decisions.)*
- **Option C** — A sensor-based autonomous exploration robot. *(Rejected: cannot provide visual evidence for expert review.)*
- **Option D — NILEX** — An integrated robotic system combining scanning, imaging, AI analysis, and autonomous decision support. *(Selected.)*

**What differentiates NILEX** is not a single component but the integration of several technologies into a workflow designed specifically for cultural-heritage protection:

1. Multi-controller architecture using four EV3 units.
2. Arduino-based scanning subsystem for dedicated processing.
3. AI-assisted image analysis linked to predefined behaviors.
4. Non-invasive-first exploration and documentation.
5. A structured decision interface between AI and robot control.
6. Modular design so future teams can replace subsystems.

The complete engineering loop: **Sense → Move → Detect → Capture → Analyze → Decide → Act → Document**.

---

## System Architecture

### Six-Layer Architecture

The system is organized into six layers, from the physical platform up to documentation:

1. **Physical Platform** — chassis, propulsion, lighting, sensor mounts, camera mount, arm.
2. **Robotic Control** — inspection movement, controlled approach to candidates, left/right propulsion, forward/reverse, turning, encoder-based distance control, navigation states.
3. **Arduino Scanning** — distance/obstacle sensors, environmental readings, safety boundaries, scan-zone information.
4. **Vision & AI** — camera → capture → preprocess → classify → decision.
5. **Decision & Safety** — mission states, communication, event logging, recovery routines, human override interface.
6. **Documentation** — image, AI result, confidence, zone, action, timestamp.

**Safety by separation:** this architecture separates perception from actuation, reducing the risk that a single AI classification error directly causes an uncontrolled physical action.

### Four-EV3 Control Architecture

Complex functions are divided into independent, individually debuggable modules:

- **EV3-1 — Navigation** — locomotion, path following, navigation states.
- **EV3-2 — Sensing** — environmental and obstacle sensing, safety checks.
- **EV3-3 — Inspection** — robotic arm and camera positioning.
- **EV3-4 — Coordination** — mission states, communication, event logging, redundancy.

A modular architecture makes debugging easier: if one subsystem fails, the team can isolate the fault instead of troubleshooting the entire program as one routine. It also supports future expansion — additional sensors or an improved AI interface can be added without rewriting every movement routine.

> Design principle: the AI layer provides decisions; the EV3 controllers execute only predefined, tested actions.

### Arduino Scanning Subsystem

A dedicated embedded controller performs high-frequency sensor processing without placing all sensing tasks on one EV3 unit. The subsystem sweeps the target area, processes readings locally, and passes a compact result to the robot-control layer.

**Data exchanged:** scan zone, detection flag, sensor values, safety flag, timestamp, object distance.

The scanning cycle: (1) start scan → (2) read sensor array → (3) compare with thresholds → (4) estimate object/obstacle region → (5) assign scan-zone identifier → (6) request camera inspection → (7) return result to the coordination layer.

The subsystem is deliberately modular: the same concept could later support depth, temperature, conductivity, or other underwater sensing technologies, depending on final hardware and scientific requirements.

---

## Mechanical Construction

The mechanical design prioritizes stability, visibility, protection, and serviceability:

- **Main structure** — rigid central frame with distributed mass.
- **Electronics** — protected compartment concept for the prototype environment.
- **Modularity** — modular sensor brackets and an adjustable camera mount for repeatable positioning.
- **Propulsion** — controlled by EV3 motor groups with closed-loop encoder feedback for consistent, repeatable movement during scanning.
- **Arm, camera & lighting** — the arm is designed for controlled inspection only; lighting reduces shadows and improves image consistency.

The arm follows a strict operating rule — **observe → interact → classify → confirm** — and is not intended for uncontrolled excavation. Any physical interaction would require conservation protocols and expert authorization.

Key engineering considerations tracked throughout the build: center of mass, water-resistant enclosure, frame stiffness, cable routing, repeatable camera position, field of view, and maintenance access.

---

## Computer Vision & AI Pipeline

### Pipeline — Ten Steps

1. Camera captures candidate image.
2. Image quality check.
3. Crop and normalize the region.
4. Remove irrelevant background.
5. Enhance contrast and visibility.
6. AI model evaluates the image.
7. Model returns class and confidence.
8. Decision layer applies thresholds.
9. Robot receives a safe command.
10. Image and decision are logged.

**Example output:** `Class: POTENTIAL_ARTIFACT · Confidence: 0.87 · Decision: INSPECT` — below threshold → `CONTINUE_SCAN`.

### AI Training Strategy

The dataset strategy accounts for realistic underwater conditions: low-light and blurred imagery, artifact-like samples, multiple orientations, rocks, debris, and sand. Honest metrics and human-in-the-loop review are core commitments: the team will not claim an accuracy value that has not been experimentally measured, and a high-confidence AI result remains a candidate classification — archaeological confirmation stays the responsibility of qualified experts.

---

## Autonomous Decision-Making

Autonomy follows a finite-state model — explainable and testable:

- **STATE 1 — SEARCH:** move through the defined scan path.
- **STATE 2 — DETECT:** evaluate sensor readings; identify a candidate region.
- **STATE 3 — INSPECT:** slow down, position camera, capture images.
- **STATE 4 — ANALYZE:** send the image through the AI pipeline.
- **STATE 5 — DECIDE:** convert AI output into a predefined safe command.
- **STATE 6A — CONTINUE:** no relevant candidate — resume scanning.
- **STATE 6B — AVOID:** obstacle detected — change path safely.
- **STATE 6C — DOCUMENT:** record image, position, confidence, time.
- **STATE 6D — HUMAN CONFIRMATION:** require authorization before any physical interaction.
- **STATE 7 — RETURN:** complete the mission or return to start.

### Decision Mapping

- Obstacle detected → **AVOID**
- Low image quality → **RECAPTURE**
- Low confidence → **CONTINUE_SCAN**
- Potential artifact → **DOCUMENT + INSPECT**
- High-confidence candidate → **DOCUMENT + REQUEST_CONFIRMATION**
- Mission complete → **RETURN**

---

## Software Architecture

Five independent software modules, coordinated by a main loop that never acts on unverified AI output:

- **Navigation** — motor control, encoder feedback, speed profiles, turning routines.
- **Sensing** — sensor reading, filtering, threshold detection, safety checks.
- **Vision** — image capture, preprocessing, AI request/response handling.
- **Decision** — confidence thresholds, state transitions, safety rules, override.
- **Logging** — scan zone, detection event, image reference, AI result, action.

### Main Loop — Pseudo-Code

```text
START
  Initialize EV3 controllers
  Initialize Arduino scanning
  Check safety status
  WHILE mission_active:
      scan_area()
      IF obstacle_detected:
          avoid_obstacle()
      ELSE IF candidate_detected:
          capture_image()
          result = AI_ANALYZE(image)
          IF result == "LOW_CONFIDENCE":
              continue_scan()
          ELSE IF result == "POTENTIAL_ARTIFACT":
              document_candidate()
              move_to_inspection_position()
          ELSE:
              continue_scan()
      log_event()
  IF mission_complete:
      return_to_start()
END
```

The final implementation will use tested block-based and/or embedded code appropriate to the selected hardware. AI output maps to predefined commands rather than arbitrary generated code.

---

## Social Impact

NILEX can reduce the need for people to enter hazardous or difficult environments during the first stage of exploration, and it creates a repeatable digital record of candidate locations and images. The social value is not only finding an object — it is protecting the information about the object and its context.

**Primary beneficiaries:**

- Archaeologists
- Cultural-heritage authorities
- Conservation specialists
- Museums and research institutions
- Marine survey teams

**Secondary beneficiaries:**

- Students and educators
- Museums and visitors
- Researchers
- Local communities connected to heritage sites
- Future generations

**Cultural principle:** a non-invasive-first philosophy — observe, document, analyze, preserve. Any physical intervention must follow expert conservation requirements.

---

## Real-World Use Case

**Submerged Heritage Survey — a seven-phase workflow:**

1. **Mapping** — a heritage team identifies an underwater area that may contain historical remains; NILEX scans the area and records movement and sensor information.
2. **Candidate Detection** — the scanning system identifies an unusual region.
3. **Visual Inspection** — NILEX positions its camera and captures several images.
4. **AI Assistance** — the AI improves image quality and evaluates whether the pattern resembles a potential object or artifact.
5. **Decision** — if confidence is insufficient, scanning continues; if relevant, the robot documents and requests the next authorized action.
6. **Expert Review** — an archaeologist reviews the evidence and determines whether further investigation is justified.
7. **Digital Record** — the final record can include location, images, classification, and inspection notes.

The robot becomes a field assistant: **evidence in, expert decision out**.

---

## Innovation & Business Model

**Six key innovations:**

1. **Multi-controller robotics** — four EV3 controllers divide complex functions into manageable modules.
2. **Dedicated scanning subsystem** — Arduino handles scanning so sensing operates independently.
3. **AI-to-action interface** — AI results convert into a small set of predefined, explainable commands.
4. **Evidence-first workflow** — every candidate is documented with image and context before interaction.
5. **Modular development** — the platform is repaired and upgraded, not replaced.
6. **Human-centered autonomy** — remote expert review via transmitted images and structured information.

**Entrepreneurship:** the platform targets heritage authorities, research institutions, museums, universities, and marine survey organizations, with a value proposition of a modular robotic assistant for safer surveying, documentation, detection, and AI-assisted inspection. Potential service models include research services, educational versions, custom systems, and institutional pilots.

---

## Responsible AI

- AI output is **decision support**; thresholds are explicit and documented.
- Low-confidence cases are **never forced** into a classification.
- Human expertise remains in the **final archaeological decision**.
- Heritage data is handled per authorities' rules; locations are **never disclosed without authorization**.
- Autonomy handles repetitive decisions; experts confirm interpretation and intervention.

> "Autonomy should increase exploration capability without reducing human responsibility."

---

## Testing & Evaluation

### Major Development Challenges

1. Coordinating multiple controllers.
2. Maintaining stable movement while scanning.
3. Synchronizing camera capture with robot position.
4. Obtaining consistent images under changing light.
5. Reducing false detections.
6. Designing a safe AI-to-robot interface.
7. Protecting electronics in the prototype environment.

### Test Plan (A–E)

- **Test A — Navigation:** distance error and repeatability.
- **Test B — Scanning:** detection of known objects and false positives.
- **Test C — Vision:** image quality under different lighting and distances.
- **Test D — AI:** accuracy, precision, recall, and confidence behavior on a documented test set.
- **Test E — Integrated Mission:** successful completion of the complete sequence.

Testing method: **one subsystem at a time, then integrate.** Tracked metrics include navigation repeatability, candidate detection rate, false-positive rate, AI accuracy, and mission completion — targets and protocols are defined before testing, and results are filled in only with verified experimental data.

---

## Roadmap

### Short-Term

1. Complete integrated EV3/Arduino communication architecture.
2. Calibrate all sensors.
3. Improve camera positioning and lighting.
4. Build a controlled underwater test environment.
5. Create and label a project-specific image dataset.
6. Train and validate the AI model.
7. Measure false positives and negatives.
8. Improve navigation repeatability.

### Medium-Term

- Add depth sensing.
- Improve underwater localization.
- Add structured mission logs.
- More robust waterproof enclosure.
- Improve remote monitoring.
- Test multiple object types and conditions.

### Long-Term Vision

- 3D mapping.
- Higher-resolution imaging.
- Sonar or acoustic sensing.
- Improved localization.
- Expert teleoperation.
- Conservation-aware manipulation.
- Digital heritage visualization.

---

## Success Metrics

Success will be measured across technical and social dimensions:

**Technical:** scan coverage · navigation repeatability · mission completion · response time · image quality · detection rate · false-positive rate · AI performance · integration.

**Social & Innovation:** reduced human exposure · documentation quality · explainable decisions · human-in-the-loop safety · modularity · expert usefulness · institutions benefiting.

> Prototype philosophy: each new feature must be tested independently, measured, and integrated only after the team understands its limitations.

---

## The Team

**AQSA-Saudi-STEM** is a student robotics team focused on applying engineering, programming, artificial intelligence, and STEAM thinking to real-world challenges. For WRO 2026, the team selected the protection and preservation of cultural heritage and developed NILEX as an autonomous/semi-autonomous underwater exploration concept.

- **Coach — Mohammed Basuny** — guides the team without driving it: asks the hard questions, ensures every engineering decision is truly the team's, and holds the project to documentation-first standards.
- **Student — Leen Adel** — Mechanical · Propulsion · Testing: chassis, propulsion, and arm design; waterproofing tests; structural stability measurements after every change.
- **Student — Sara Sultan** — AI Vision · Arduino · Software: AI pipeline and Arduino scanning subsystem; threshold tuning, camera positioning, and test documentation.

**Team working principle:** Research → Define → Design → Build → Program → Test → Measure → Improve.

No judgment without a measurement, a test, or a defined rule behind it.

---

## Sources & References

1. World Robot Olympiad Association. *WRO 2026 – Future Innovators Mission: "Robots Meet Culture."* Official mission document.
2. WRO. *WRO 2026 – Future Innovators Information for Teams & Coaches.* Official project-report template and competition guidance.
3. WRO. *WRO 2026 Season page.* Official category and season information.
4. WRO. *Future Innovators category information and general rules.*
5. UNESCO. *Underwater Cultural Heritage* — official information and international framework for the protection of underwater cultural heritage.
6. UNESCO. *2001 Convention on the Protection of the Underwater Cultural Heritage.*
7. Team-generated survey: *"Survey on Using Robots to Discover and Protect Submerged Cultural Heritage."*
8. Team engineering documentation: NILEX prototype design, testing records, code versions, sensor calibration logs, and AI validation results.

---

## Document Information

- **Document ID:** WRO-FI-2026 · Revision REV A
- **Structure:** 5 sections · 20 sheets — Idea & Research · System & Mechanics · Software & AI · Impact & Innovation · Evaluation & Roadmap
- **Before final submission:** replace all planned metrics with measured experimental results, add final robot photographs, insert actual survey statistics, and document the final hardware and software configuration. Verify the latest international rules and any national-organizer adaptations.

<div align="center">

*Discover carefully. Document accurately. Protect responsibly.*

**Evidence-First · Non-Invasive-First · Human-in-the-Loop · Modular · Explainable**

</div>
