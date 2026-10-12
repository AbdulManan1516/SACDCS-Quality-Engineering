# SACDCS Quality Engineering Lab – Deliverables Checklist

## Task 1: Requirement Extraction
- [ ] 10 Functional Requirements (FR-001 to FR-010)
  - [ ] Command validation
  - [ ] Safe Mode entry
  - [ ] Chamber correction
  - [ ] Obstacle handling
  - [ ] Communication with multiple robots
  - [ ] Operator authentication
  - [ ] Role-based authorisation
  - [ ] Event logging
  - [ ] Railway crossing control
  - [ ] Status reporting
- [ ] 5 Non-Functional Requirements (NFR-001 to NFR-005)
  - [ ] Performance (time limits, response)
  - [ ] Security (authentication, encryption)
  - [ ] Scalability (20+ robots)
  - [ ] Reliability (uptime, fault tolerance)
  - [ ] Usability (web portal, remote control)
- [ ] 4 High-Risk/Safety Requirements (SR-001 to SR-004)
  - [ ] Safety-critical (Safe Mode, battery, thermal)
  - [ ] Real-time (Safe Mode within 3 seconds)
  - [ ] Link-dependent (low-bandwidth, delay)
  - [ ] Railway-crossing related (barrier, train detection)
- [ ] Requirements table with: Req. ID | Requirement | Type | Priority | Verification Method

---

## Task 2: Change Requests & Traceability Matrix
- [ ] Version-controlled change log (CR-01, CR-02, CR-03)
  - [ ] Old requirement text
  - [ ] Modified requirement text
  - [ ] Reason for change
  - [ ] Version number
  - [ ] Status (Approved, Implemented, Verified)
- [ ] Explanation of why each CR improves measurability/testability
- [ ] Multi-layer RTM: Requirement → State → Operation → Constraint → Test Case → Risk Level
- [ ] At least 10 test cases with:
  - [ ] Test ID (TC-001 to TC-010+)
  - [ ] Preconditions
  - [ ] Steps
  - [ ] Expected result
  - [ ] Risk level
- [ ] Coverage of:
  - [ ] Command received and authenticated
  - [ ] Role authorisation
  - [ ] Execution and status reporting
  - [ ] Event logging
  - [ ] Safe Mode entry (CR-01)
  - [ ] 20 simultaneous robots (CR-02)
  - [ ] Chamber correction
  - [ ] Communication loss
  - [ ] Railway crossing
- [ ] Regression tests identified for each CR

---

## Task 3: State Modelling & Transition Verification
- [ ] State definitions (7 states)
  - [ ] S-001: IDLE (meaning, entry, exit)
  - [ ] S-002: NAVIGATING (meaning, entry, exit)
  - [ ] S-003: AVOIDING_OBSTACLE (meaning, entry, exit)
  - [ ] S-004: DELIVERING (meaning, entry, exit)
  - [ ] S-005: RETURNING (meaning, entry, exit)
  - [ ] S-006: SAFE_MODE (meaning, entry, exit)
  - [ ] S-007: LINK_LOST (meaning, entry, exit)
- [ ] Event definitions with state vs. event distinction
  - [ ] DeliveryRequest
  - [ ] DestinationReached
  - [ ] ObstacleDetected
  - [ ] ObstacleCleared
  - [ ] CriticalBattery
  - [ ] ChamberError
  - [ ] LinkLost
  - [ ] LinkRestored
- [ ] State Transition Table with:
  - [ ] Current State
  - [ ] Event
  - [ ] Next State
  - [ ] Requirement ID
  - [ ] Valid? (Y/N)
  - [ ] Verification evidence
- [ ] Transition verification analysis:
  - [ ] IDLE → DELIVERING (invalid, direct delivery)
  - [ ] Missing AVOIDING_OBSTACLE exit (stuck)
  - [ ] AVOIDING_OBSTACLE → DELIVERING (invalid, unsafe)
  - [ ] CriticalBattery in AVOIDING_OBSTACLE (missing transition)
  - [ ] CriticalBattery in DELIVERING (missing transition)
- [ ] Safe Mode entry within 3 seconds (CR-01 enforcement)
- [ ] Mermaid state diagram (GitHub-compatible)

---

## Task 4: Operation Identification & Schemas
- [ ] Identification of at least 12 operations (Op-001 to Op-012+)
  - [ ] Sensor self-check
  - [ ] Batch profile loading
  - [ ] Environmental correction
  - [ ] Recovery verification
  - [ ] Protection response (vibration, door, thermal)
  - [ ] Batch removal safety check
  - [ ] Command authorisation
  - [ ] Obstacle detection and avoidance
  - [ ] Safe Mode entry
  - [ ] Railway crossing check
  - [ ] Event logging
  - [ ] Emergency power switch
- [ ] Complete Operation Schemas for at least 6 operations:
  - [ ] Operation Name
  - [ ] Description
  - [ ] Inputs
  - [ ] Outputs
  - [ ] Reads (from sensors/state)
  - [ ] Changes (state changes)
  - [ ] Sends/Alerts (to operator/system)
  - [ ] Assumes (precondition)
  - [ ] Result (postcondition)
- [ ] Chamber state changes demonstrated (2+ operations)
- [ ] Sensor verification requirement explained (environmental recovery, batch removal safety)

---

## Task 5: Constraints, Formalisation & Violations
- [ ] At least 12 precise system constraints (C-001 to C-012+)
  - [ ] Constraint ID
  - [ ] English description
  - [ ] Why necessary
- [ ] Formalisation of at least 8 constraints using:
  - [ ] Logical operators (∧, ∨, ¬, →)
  - [ ] Temporal operators (within 3 seconds)
  - [ ] Quantifiers (∀, ∃)
- [ ] Coverage of:
  - [ ] Robot safety (IDLE before delivery, not delivering during obstacle avoidance)
  - [ ] Railway barriers (train detection, barrier state, robot entry)
  - [ ] Chamber-door interlocks (no delivery with open door)
  - [ ] Environmental recovery (temperature/humidity correction within time limit)
  - [ ] Vibration suspension (must stabilise before resuming)
  - [ ] Operator permissions (authentication and role-based control)
  - [ ] Sensor failure (graceful degradation, Safe Mode)
  - [ ] Communication loss (Link Lost state, operator alert)
  - [ ] Power loss (emergency power or safe shutdown)
- [ ] At least 8 realistic violation scenarios with:
  - [ ] Variable values
  - [ ] Violation description
  - [ ] Detection method
  - [ ] Expected response (alarm, stop, alert, log, Safe Mode)
- [ ] All constraints are testable and precise

---

## Cross-Reference Validation
- [ ] All Req. IDs (FR, NFR, SR) referenced in tests exist
- [ ] All State IDs (S-xxx) referenced in transitions exist
- [ ] All Operation IDs (Op-xxx) referenced in schemas exist
- [ ] All Constraint IDs (C-xxx) referenced in violations exist
- [ ] All Test IDs (TC-xxx) traceable to requirements
- [ ] No circular dependencies in RTM

---

## Output Files
- [ ] README.md (main deliverable with all tasks)
- [ ] DELIVERABLES_CHECKLIST.md (this file)
- [ ] Optional: Separate markdown files for each task (if needed)

---

## Quality Assurance
- [ ] Professional Markdown formatting
- [ ] Consistent ID naming conventions throughout
- [ ] Natural, clear, concise writing suitable for university
- [ ] All sub-questions addressed
- [ ] No invented unsupported behaviour
- [ ] Mermaid syntax validated
- [ ] Logical expressions validated
- [ ] All RTM references verified
