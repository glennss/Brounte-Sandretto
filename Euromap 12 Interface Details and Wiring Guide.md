````markdown name=EUROMAP12_Interface_Details.md
# Euromap 12 Interface Details for Brounte Robot to Sandretto IMM

This document outlines the Euromap 12 interface signals for connecting a Brounte Robot to a Sandretto Series 8 Injection Moulding Machine (IMM). The information is based on standard Euromap 12 signal definitions and a specific IMM wiring diagram provided by the user.

**User Note:** Please upload the physical image files (referenced as Image 1, 2, 3, and 4 in the original conversation) to this repository for complete documentation. You can then link them within this Markdown file if desired.

## 1. Euromap 12 Standard Signal Definitions Summary
(Derived from user-provided images of Euromap 12 documentation)

### Signals: IMM to Robot (Handling Device)

| Plug Contact No. | Signal Designation                             | Brief Description                                                                 |
|------------------|------------------------------------------------|-----------------------------------------------------------------------------------|
| 1, 9             | Emergency stop of machine                      | IMM E-stop activated; causes handling device E-stop. Current <= 6A.             |
| 2                | Mould open position (handling device)          | Mould is open sufficiently for robot entry.                                       |
| 3, 11            | Safety devices of machine                      | IMM safety guards are operative. Current <= 6A.                                   |
| 4                | Ejector back position                          | Ejector fully retracted.                                                          |
| 5                | Ejector forward position                         | Ejector fully advanced.                                                           |
| 6 (optional)     | Core pullers in position 1                     | Core pullers are set, free for handling device approach.                          |
| 7 (optional)     | Core pullers in position 2                     | Core pullers are set for part removal.                                            |
| 8 (optional)     | Reject                                         | Current part is a reject.                                                         |
| 10               | Enable operation with handling device (Auto)   | IMM is in semi-auto/auto mode, ready for robot interaction.                       |
| 12               | Mould closed                                   | Mould is fully closed.                                                            |
| 13,14 (optional) | Intermediate mould opening position            | Mould is at a defined intermediate open position.                                 |
| 15 (optional)    | No part available                              | (Not recommended for future applications)                                         |
| 16               | Handling device reference potential            | Corrected vs older Euromap 12. Reference for signals from IMM to Robot.           |

### Signals: Robot (Handling Device) to IMM

| Plug Contact No. | Signal Designation                             | Brief Description                                                                 |
|------------------|------------------------------------------------|-----------------------------------------------------------------------------------|
| 17               | Enable mould closure                           | Robot is clear, IMM can close mould.                                              |
| 18, 26           | Mould area free                                | Handling device is outside mould area. Current <= 6A.                             |
| 19, 27           | Emergency stop of handling                     | Handling device E-stop activated; causes IMM E-stop. Current <= 6A.               |
| 20               | Handling device operation mode                 | Indicates robot's operational mode.                                               |
| 21               | Enable ejector back                            | Robot requests IMM to move ejector back.                                          |
| 22               | Enable ejector forward                           | Robot requests IMM to move ejector forward.                                       |
| 23 (optional)    | Enable movement of core pullers to position 2  | Robot requests IMM to move core pullers for part removal.                         |
| 24 (optional)    | Enable movement of core pullers to position 1  | Robot requests IMM to move core pullers for robot approach.                       |
| 28 (optional)    | Enable full mould opening                      | Robot has taken part, mould can continue opening.                                 |

### Reserved / Manufacturer Dependent / Other

| Plug Contact No. | Signal Designation                             | Brief Description                                                                 |
|------------------|------------------------------------------------|-----------------------------------------------------------------------------------|
| 25               | Reserved for future use by EUROMAP             | -                                                                                 |
| 29               | Reserved for future use by EUROMAP             | -                                                                                 |
| 30               | Not fixed by EUROMAP, manufacturer dependent   | -                                                                                 |
| 31               | Not fixed by EUROMAP, manufacturer dependent   | -                                                                                 |
| 32               | Injection moulding machine reference potential | Corrected vs older Euromap 12. Reference for signals from Robot to IMM.           |

## 2. IMM Specific Wiring Diagram Reference

A crucial piece of information for the wiring was the IMM-specific wiring diagram snippet (referred to as Image 4 in the conversation). This diagram provided exact pin assignments for the Harting connectors on the Sandretto IMM and clarified reference potentials and power supply pins. **It is highly recommended to upload this image to the repository and consult it directly.**

## 3. Consolidated Wiring Diagram (Robot to IMM)

This wiring map combines the robot controller terminals (as understood from Image 1 of the conversation) with the Euromap 12 standard and the IMM-specific diagram (Image 4).

### Signals FROM IMM TO ROBOT (Robot Inputs)

| IMM Harting Pin | IMM Signal Name                         | Robot Input Terminal (中文) | Robot Input Terminal (English)         |
|:---------------:|:---------------------------------------:|:--------------------------:|:--------------------------------------:|
| 1, 9            | EMERGENCY STOP                          | 急停入                      | Emergency Stop Input                   |
| 2               | MOULD OPEN                              | 开模完                      | Mould Open Position                    |
| 3, 11           | SAFETY DEVICES                          | 安全门                      | Safety Door                            |
| 4               | EJECTOR RETRACTED                       | 顶退停                      | Ejector Retract                        |
| 5               | EJECTOR ADVANCED                        | 顶进停                      | Ejector Advance                        |
| 6 (optional)    | CORE-PULLERS FREE FOR HANDLING          | 入芯停                      | Core Puller Position 1                 |
| 7 (optional)    | CORE-PULLERS IN POSITION TO REMOVE      | 出芯停                      | Core Puller Position 2                 |
| 8 (optional)    | REJECT                                  | 不良品                      | Reject (Defective Part)                |
| 10              | AUTOMATIC                               | 全自动                      | Automatic Mode                         |
| 12              | MOULD CLOSED                            | 关模完                      | Mould Closed                           |
| 13 (optional)   | MOULD OPENING                           | 中板模                      | Intermediate Mould Opening             |
| 16              | INJECTION MOULDING MACHINE REF. POT.    | 公共端                      | Common (Robot Input Reference)         |

### Signals FROM ROBOT TO IMM (Robot Outputs)

| IMM Harting Pin | IMM Signal Name                         | Robot Output Terminal (中文) | Robot Output Terminal (English)        |
|:---------------:|:---------------------------------------:|:---------------------------:|:--------------------------------------:|
| 17              | ENABLE MOULD CLOSURE                    | 可关模                       | Enable Mould Closure                   |
| 18              | MOULD AREA FREE                         | 安全区                       | Mould Area Free                        |
| 19 (from robot) | EMERGENCY STOP (Handling E-Stop)        | 急停出                       | Emergency Stop Output                  |
| 21              | ENABLE EJECTOR RETRACTION               | 可顶退                       | Enable Ejector Back                    |
| 22              | ENABLE EJECTOR ADVANCE                  | 可顶进                       | Enable Ejector Forward                 |
| 30 (optional)   | MOULD FINAL OPENING ENABLE              | 可开模                       | Enable Full Mould Opening              |
| *Robot Output Power & Common (see notes below)*         |                                 |                              |                                        |

### Power and Commons for Robot Outputs (Connected to IMM Female Harting Connector)

| IMM Harting Pin | IMM Function for Robot Outputs          | Robot Connection Point (General)       |
|:---------------:|:---------------------------------------:|:--------------------------------------:|
| 26 (or 32)      | 0V Reference for Robot Outputs          | 公共端 (Robot Output Common)           |
| 27              | +24V Supply for Robot Outputs           | Robot Outputs +24V Supply (if needed)  |

**Note on IMM Female Pin 19 & 27 (Emergency Stop):** The IMM diagram shows its Female Pin 19 for \'\'\'EMERGENCY STOP\'\'\' (from Robot) and Pin 27 as \'\'\'+24V\'\'\'. The Euromap standard lists 19 & 27 for \'\'\'Emergency stop of handling\'\'\'. Ensure your robot\'s E-Stop output is correctly wired, typically as a normally closed contact that opens on E-Stop, often interrupting a +24V signal.

## 4. Crucial Safety and Wiring Notes

*   **Consult Official Manuals:** This document is a guide based on provided information. **ALWAYS consult the official manuals for both your Brounte Robot and the Sandretto IMM before making any electrical connections.**
*   **Verify Voltage and Signal Types:** Ensure that the voltage levels (e.g., 24V DC) and signal types (e.g., dry contact, PNP, NPN) are compatible between the robot and the IMM for all signals.
*   **Qualified Personnel:** Electrical wiring should be performed by a qualified technician or engineer familiar with industrial control systems and safety standards.
*   **Optional Signals:** Connect optional signals only if both your robot and IMM support and require them for your specific application.
*   **Robot Output Configuration:** The exact wiring of robot outputs (e.g., `可关模`) depends on whether they are dry relay contacts, PNP, or NPN outputs.
    *   If **dry relay contacts**: One side of the relay connects to the IMM signal pin (e.g., Pin 17), the other side to the +24V supplied by the IMM (e.g., Pin 27 on the IMM Female connector).
    *   If **PNP outputs**: The robot output common typically connects to 0V (e.g., Pin 26/32 on IMM Female), and the signal output provides +24V (sourced from IMM\'s +24V via the robot\'s internal circuits).
    *   Consult your robot\'s manual for its specific output configuration.

This document should serve as a good starting point for understanding and implementing the Euromap 12 interface between your machines.
