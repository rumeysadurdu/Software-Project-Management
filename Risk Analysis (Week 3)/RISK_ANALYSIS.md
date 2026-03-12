# Risk Analysis – The Unforeseen
**Project:** The Unforeseen | **Team:** U97 Unity Takımı | **Engine:** Unity 3D | **Date:** March 2026

---

## 1. Risk Identification

The following risks have been identified for *The Unforeseen*, a 3D puzzle/mystery game developed in Unity where players act as a medium solving puzzles to connect clients with deceased loved ones.

### 1-1. Risk Assessment and Management

| Risk ID | Risk Description | Probability | Impact | Risk Level | Owner |
|---------|-----------------|-------------|--------|------------|-------|
| R-01 | Team member unavailability / dropout | Medium | High | **HIGH** | Scrum Master |
| R-02 | Unity version incompatibility between team members | Medium | Medium | **MEDIUM** | Developers |
| R-03 | Puzzle mechanics not functioning as intended | Medium | High | **HIGH** | Developers |
| R-04 | 3D asset quality below target / asset import failures | High | Medium | **HIGH** | Design Team |
| R-05 | Scene performance issues / low FPS on target hardware | Medium | High | **HIGH** | Developers |
| R-06 | Dialogue system bugs or incorrect story branching | Low | High | **MEDIUM** | Developers |
| R-07 | Scope creep causing sprint overruns | High | Medium | **HIGH** | Product Owner |
| R-08 | Loss of project files / version control conflicts | Low | Critical | **HIGH** | All Members |
| R-09 | Storyline inconsistency / unresolved scenario decisions | Medium | Medium | **MEDIUM** | Product Owner |
| R-10 | Build / export errors preventing final release | Low | High | **MEDIUM** | Developers |
| R-11 | Audio/SFX missing or mismatched with game events | Medium | Low | **LOW** | Design Team |
| R-12 | Target audience age-appropriateness issues (10+) | Low | Medium | **LOW** | Product Owner |

---

### 1-2. Mitigation / Preventive Actions

| Risk ID | Mitigation / Preventive Action |
|---------|-------------------------------|
| R-01 | Cross-train all developers on core systems; document all code; maintain updated Trello backlog so any member can pick up tasks. Keep weekly check-ins via Discord. |
| R-02 | Lock Unity version at project start (record in README); all members use same LTS version. Use `.vsconfig` and shared `.vscode` settings already present in repo. |
| R-03 | Prototype each puzzle mechanic in an isolated test scene before integrating into main build; write unit tests for puzzle state transitions. |
| R-04 | Define art style guide early; use Unity's FBX/OBJ import pipeline with consistent scale settings; keep backup copies of source assets in `/Assets`. |
| R-05 | Profile scenes with Unity Profiler during Sprint 2 & 3; apply LOD (Level of Detail) groups; limit real-time lighting and use baked lighting where possible. |
| R-06 | Use a dedicated dialogue management asset (e.g., Yarn Spinner or custom ScriptableObject system); review all story branches before each sprint review. |
| R-07 | Enforce strict Definition of Done in each sprint; Product Owner gates new features until core mechanics are stable; use MoSCoW prioritisation on backlog. |
| R-08 | All members commit daily to GitHub; use `.gitignore` to exclude large binary files; store large assets via Git LFS or external drive backup. |
| R-09 | Finalise storyline document in Sprint 1 retrospective; all story decisions recorded in Game Design Document (`GameDesignDocument` file in repo). |
| R-10 | Perform test builds on target platform (PC/Windows) at the end of each sprint; include build step in sprint review checklist. |
| R-11 | Create a sound asset checklist linked to each game event; assign one team member as audio lead from Sprint 2 onward. |
| R-12 | Review content (themes of death, supernatural) against PEGI 7/12 guidelines; avoid graphic depictions; confirm 10+ rating is maintained. |

---

### 1-3. Risk Matrix

```
         │  LOW Impact  │ MEDIUM Impact │ HIGH Impact  │ CRITICAL Impact
─────────┼──────────────┼───────────────┼──────────────┼────────────────
  HIGH   │              │  R-04, R-07   │  R-03, R-05  │
Prob.    │              │               │              │
─────────┼──────────────┼───────────────┼──────────────┼────────────────
 MEDIUM  │  R-11        │  R-02, R-09   │  R-01        │
Prob.    │              │               │              │
─────────┼──────────────┼───────────────┼──────────────┼────────────────
  LOW    │              │  R-06, R-10,  │              │  R-08
Prob.    │              │  R-12         │              │
─────────┴──────────────┴───────────────┴──────────────┴────────────────

  LEGEND:  🟢 LOW   🟡 MEDIUM   🟠 HIGH   🔴 CRITICAL
```

**Colour-coded summary:**
- 🔴 **Critical (act immediately):** R-08 (file loss)
- 🟠 **High (manage actively):** R-01, R-03, R-04, R-05, R-07
- 🟡 **Medium (monitor):** R-02, R-06, R-09, R-10, R-12
- 🟢 **Low (accept/watch):** R-11

---

## 2. Code Security & Data Privacy

### 2.1 Code Security

**The Unforeseen** is a single-player, offline PC game with no server-side components or online multiplayer. Security scope is therefore limited but still relevant:

| Area | Practice Applied |
|------|-----------------|
| **Source Code Protection** | Repository is public for academic review; sensitive API keys or build credentials must never be committed. Use `.gitignore` to exclude `UserSettings/`, local `.env` files, and Unity Cloud credentials. |
| **Unity Build Security** | Compiled C# assemblies in the final build are obfuscated by Unity's IL2CPP backend (if used). Avoid storing game logic in plain-text config files that can be edited by players to cheat. |
| **Third-Party Assets** | All Unity Asset Store packages used must be reviewed for licence compliance. Packages should not contain malicious scripts; only use packages from verified publishers. |
| **Version Control** | GitHub access is managed via personal accounts. No shared credentials. All contributors must enable 2FA on their GitHub accounts. |
| **Dependency Management** | Unity package versions are locked in `Packages/manifest.json`. Packages are not auto-updated without team review to prevent breaking changes or supply-chain risks. |

### 2.2 Data Privacy

As the game has no network connectivity, user account system, or data collection mechanism, data privacy exposure is minimal.

| Data Category | Status | Action |
|---------------|--------|--------|
| Player personal data | **Not collected** | No registration, login, or telemetry system exists |
| Save files | Stored locally on player's PC | Use `Application.persistentDataPath`; do not expose file path in UI |
| Analytics / telemetry | **Not implemented** | If added in future, must comply with KVKK (Turkey) / GDPR |
| Team member data on GitHub | Public commits contain names/usernames | Acceptable; no private data in commits |

**GDPR / KVKK Compliance Statement:** The current version of *The Unforeseen* does not collect, process, or transmit any personal data. If analytics or cloud saves are introduced in future versions, a privacy policy and opt-in consent mechanism must be implemented.

---

## 3. Implementation Roadmap

### Phase Overview

| Phase | Sprint | Dates (Approx.) | Key Deliverables |
|-------|--------|-----------------|-----------------|
| **Phase 1: Pre-Production** | Sprint 1 | Weeks 1–3 | Game Design Document, core scene setup, character concept, dialogue system prototype |
| **Phase 2: Core Development** | Sprint 2 | Weeks 4–7 | Main puzzle mechanics (el falı, yapboz), 3D environment (room, beach scenes), dialogue demo |
| **Phase 3: Content & Polish** | Sprint 3 | Weeks 8–11 | All puzzle types integrated, star/room scenes, SFX, UI polish, story complete |
| **Phase 4: Testing & Release** | Post-Sprint 3 | Weeks 12–13 | QA testing, bug fixes, final build, GitHub release |

### Milestone Tracker

```
Week 1-2  ▓▓░░░░░░░░░░░░  Game Design Document finalised
Week 2-3  ▓▓▓░░░░░░░░░░░  Base scene & character controller working
Week 4-5  ▓▓▓▓▓░░░░░░░░░  Puzzle mechanics prototyped (el falı demo)
Week 5-6  ▓▓▓▓▓▓░░░░░░░░  Dialogue system integrated (dialog demo)
Week 7    ▓▓▓▓▓▓▓░░░░░░░  Sprint 2 review – playable vertical slice
Week 8-9  ▓▓▓▓▓▓▓▓▓░░░░░  Full environment set (room, beach, yıldız)
Week 10   ▓▓▓▓▓▓▓▓▓▓░░░░  Story complete, all puzzles integrated
Week 11   ▓▓▓▓▓▓▓▓▓▓▓░░░  Sprint 3 review – feature complete build
Week 12   ▓▓▓▓▓▓▓▓▓▓▓▓░░  QA & bug fix cycle
Week 13   ▓▓▓▓▓▓▓▓▓▓▓▓▓▓  Final build & GitHub release
```

### Team Responsibilities by Phase

| Phase | Developers (Meliha, Melike, Mert) | Product Owner (Melis Naz) | Scrum Master (Mustafa) |
|-------|-----------------------------------|--------------------------|------------------------|
| Pre-Production | Scene setup, prototype scripts | Backlog grooming, GDD | Sprint planning, daily scrums |
| Core Development | Puzzle mechanics, dialogue code | Sprint reviews, priority decisions | Blocker removal, burndown tracking |
| Content & Polish | Asset integration, SFX hookup | Content approval, scope decisions | Retrospective facilitation |
| Testing & Release | Bug fixes, build pipeline | Release approval | Final review coordination |

---

*Document prepared for AkademiJam – U97 Unity Takımı | March 2026*
