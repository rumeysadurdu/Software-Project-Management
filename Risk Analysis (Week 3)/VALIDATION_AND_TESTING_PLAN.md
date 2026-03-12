# Validation & Testing Plan – The Unforeseen
**Project:** The Unforeseen | **Team:** U97 Unity Takımı | **Engine:** Unity 3D | **Date:** March 2026

---

## 1. Overview

This document defines how *The Unforeseen* will be systematically tested and validated before release. Testing covers gameplay mechanics, dialogue systems, puzzle logic, performance, and user experience to ensure a polished 3D mystery/puzzle experience for the 10+ target audience.

---

## 2. Testing Methodology

### 2.1 Testing Types

| Testing Type | Description | Tool / Method |
|-------------|-------------|---------------|
| **Unit Testing** | Test individual C# scripts and methods in isolation | Unity Test Runner (EditMode tests) |
| **Integration Testing** | Verify that puzzle systems, dialogue manager, and scene transitions work together | Unity Test Runner (PlayMode tests) |
| **System / End-to-End Testing** | Play through full game loop from start to end | Manual playthroughs by team members |
| **Regression Testing** | Re-run tests after each code change to ensure nothing is broken | Run Unity Test Runner suite before each commit |
| **Performance Testing** | Measure FPS, memory usage, and load times | Unity Profiler, Frame Debugger |
| **User Acceptance Testing (UAT)** | External players from the target audience test the game | Peer testing sessions, feedback forms |
| **Exploratory Testing** | Testers freely explore the game to find unexpected bugs | Unscripted sessions with testers |

---

## 3. Test Cases

### 3.1 Core Gameplay – Puzzle Mechanics

| Test ID | Test Case | Steps | Expected Result | Pass Criteria |
|---------|-----------|-------|-----------------|---------------|
| TC-01 | El Falı Puzzle – Correct Answer | Interact with hand reading mechanic; select correct symbol | Puzzle completes, story advances | Scene transitions to next stage |
| TC-02 | El Falı Puzzle – Wrong Answer | Select incorrect symbol | Error feedback shown, retry allowed | Player is not softlocked |
| TC-03 | Yapboz (Jigsaw) – Completion | Place all pieces correctly | Puzzle completion animation plays | Story event triggers |
| TC-04 | Yapboz – Piece Interaction | Drag and drop a puzzle piece | Piece follows cursor, snaps to slot | No physics glitches or missed collisions |
| TC-05 | Puzzle Reset | Leave puzzle mid-way and return | Puzzle state preserved | Progress not lost on scene reload |

### 3.2 Dialogue System

| Test ID | Test Case | Steps | Expected Result | Pass Criteria |
|---------|-----------|-------|-----------------|---------------|
| TC-06 | Dialogue trigger on enter | Walk character into dialogue zone | Dialogue box appears with correct text | NPC starts correct conversation |
| TC-07 | Dialogue progression | Click through all lines | Each line advances to next | No skipped or repeated lines |
| TC-08 | Dialogue branching | Reach a choice node | Options display correctly | Selected choice leads to correct branch |
| TC-09 | Dialogue end | Reach final dialogue line | Dialogue closes cleanly | No UI elements remain on screen |

### 3.3 Scene Management

| Test ID | Test Case | Steps | Expected Result | Pass Criteria |
|---------|-----------|-------|-----------------|---------------|
| TC-10 | Scene transition | Complete puzzle trigger | Next scene loads | Load time < 5 seconds; no black screen freeze |
| TC-11 | Scene return / main menu | Press pause → main menu | Main menu loads | All objects destroyed; no memory leak |
| TC-12 | Room scene integrity | Load the main room scene | All 3D objects visible, no missing meshes | No pink/missing material errors |
| TC-13 | Beach scene integrity | Load beach scene | Environment renders correctly | Consistent lighting, no Z-fighting |

### 3.4 Performance

| Test ID | Test Case | Metric | Target |
|---------|-----------|--------|--------|
| TC-14 | Frame rate – main room | FPS in room scene (no action) | ≥ 30 FPS on min-spec PC |
| TC-15 | Frame rate – puzzle active | FPS during puzzle interaction | ≥ 30 FPS |
| TC-16 | Memory usage | RAM during gameplay | < 2 GB |
| TC-17 | Build size | Final exported .exe + data | < 1 GB |
| TC-18 | Load time | Time from launch to main menu | < 10 seconds |

### 3.5 UI / UX

| Test ID | Test Case | Expected Result |
|---------|-----------|-----------------|
| TC-19 | Main menu buttons | All buttons clickable and responsive |
| TC-20 | Pause menu | ESC opens pause menu; resume works |
| TC-21 | Text readability | All dialogue and UI text legible at 1920×1080 |
| TC-22 | Controller/mouse input | Mouse click and keyboard inputs register correctly |

---

## 4. Validation Methods

### 4.1 Functional Validation
Each puzzle mechanic is validated against the Game Design Document specification. A mechanic is considered validated when it behaves exactly as documented in `GameDesignDocument` and passes all associated test cases (TC-01 through TC-09).

### 4.2 Story & Narrative Validation
The storyline is validated by the Product Owner (Melis Naz Tanrıverdi) who reviews each dialogue node against the agreed script. All client story arcs must be completable without dead ends or missing transitions.

### 4.3 Performance Validation
Unity Profiler reports are generated for each major scene at the end of Sprint 2 and Sprint 3. Any scene failing the 30 FPS threshold triggers a mandatory optimisation task added to the backlog.

### 4.4 User Acceptance Testing (UAT)
At least **5 external testers** from the target audience (age 10+, PC gamers, puzzle/mystery fans) play a complete session. Feedback is collected via a structured form covering:
- Fun factor (1–5 scale)
- Puzzle clarity (1–5 scale)
- Story engagement (1–5 scale)
- Any bugs or confusing moments (open text)

---

## 5. Performance Evaluation

| Metric | Measurement Method | Acceptable Threshold |
|--------|-------------------|---------------------|
| FPS | Unity Profiler – Avg FPS over 1-minute play session | ≥ 30 FPS on integrated GPU |
| Crash rate | Number of crashes in 10 playthroughs | 0 crashes |
| Puzzle completion rate | % of testers who complete all puzzles without help | ≥ 70% |
| Story comprehension | % of testers who understand the ending | ≥ 80% |
| Bug count (post-UAT) | Number of P1/P2 bugs remaining | 0 critical, ≤ 3 minor |
| Average UAT score | Mean score across fun/clarity/engagement | ≥ 3.5 / 5.0 |

---

## 6. Test Schedule

| Phase | Testing Activity | Responsible |
|-------|-----------------|-------------|
| Sprint 1 | Unit tests for dialogue trigger scripts; scene load smoke test | Developers |
| Sprint 2 | Integration tests for puzzle + dialogue flow; UAT prototype session with 2 testers | Developers + Product Owner |
| Sprint 3 | Full regression suite; performance profiling; final UAT with 5 testers | All team members |
| Pre-Release | Final build test on clean Windows machine; export validation | Scrum Master + Developers |

---

## 7. Success Criteria

The project **The Unforeseen** will be considered **successful** when ALL of the following criteria are met:

### 7.1 Functional Success Criteria
- [ ] All puzzles (el falı, yapboz, and additional mechanics) are fully playable from start to finish without game-breaking bugs
- [ ] The complete story can be experienced in a single playthrough without dead ends, missing dialogue, or broken scene transitions
- [ ] The game runs without crashes for a minimum of 2 consecutive full playthroughs on the target platform (PC/Windows)

### 7.2 Performance Success Criteria
- [ ] Minimum 30 FPS maintained in all scenes on a mid-range PC (Intel Core i5, 8 GB RAM, integrated/dedicated GPU)
- [ ] Build size is under 1 GB
- [ ] Scene load times are under 10 seconds

### 7.3 Quality Success Criteria
- [ ] Zero P1 (critical/game-breaking) bugs in the final build
- [ ] User Acceptance Testing average score of **3.5 / 5.0 or higher** across fun, clarity, and story engagement
- [ ] At least 70% of UAT testers complete all puzzles without external assistance

### 7.4 Project Management Success Criteria
- [ ] All 3 sprints completed with ≥ 85% of planned backlog points delivered
- [ ] Game Design Document is up-to-date and reflects the shipped game
- [ ] Final build and all documentation committed to the GitHub repository

### 7.5 Academic Submission Success Criteria
- [ ] Risk Analysis document uploaded to GitHub repository ✅
- [ ] Validation & Testing Plan uploaded to GitHub repository ✅
- [ ] UML Game Flow Diagram uploaded to GitHub repository ✅
- [ ] Project ready for live GitHub presentation in class ✅

---

*Document prepared for AkademiJam – U97 Unity Takımı | March 2026*
