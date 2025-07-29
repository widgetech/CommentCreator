# Testing Application (TA) – Architecture Overview

The Testing Application (TA) is a separate system designed to automatically validate and stress-test the Main Application (MA).

---

## 1. Full Workflow Diagram

```mermaid
graph TD

    %% Testing Application
    subgraph TA [Testing Application (TA)]
        A1[Test Orchestration<br><i>Schedules & triggers tests</i>]
        A2[Input Generator<br><i>LLM generates inputs & edge cases</i>]
        A3[Validation Engine<br><i>Rule-based + LLM semantic checks</i>]
        A4[Reporting & History<br><i>Stores results & dashboards</i>]
    end

    %% Main Application
    subgraph MA [Main Application (MA)]
        B1[Input Module<br><i>Django/React UI</i>]
        B2[Processing/Fetcher<br><i>Validates & parses input</i>]
        B3[AI Analysis Module<br><i>CrewAI agents (topic detection, fact check, response gen)</i>]
        B4[Output Module<br><i>Returns JSON + user output</i>]
    end

    %% Flow
    A1 --> A2
    A2 -->|Generates test cases| B1
    B1 --> B2 --> B3 --> B4
    B4 -->|Collects output| A3
    A3 -->|Logs pass/fail + metrics| A4

    %% Optional CI/CD
    subgraph CI [CI/CD Pipeline]
        C1[Deploy Trigger]
    end

    C1 -->|Triggers test run| A1

    %% Classes
    classDef ta fill:#e0f7fa,stroke:#006064,stroke-width:2px;
    classDef ma fill:#fff3e0,stroke:#bf360c,stroke-width:2px;
    class A1,A2,A3,A4 ta;
    class B1,B2,B3,B4 ma;
```

---

## 2. TA Core Modules

1. **Test Orchestration Module** – Manages scheduling and triggering of test runs.
2. **Input Generator** – Uses an LLM to create diverse test cases and edge cases.
3. **Validation Engine** – Combines rule-based validation with LLM semantic and factual checks.
4. **Reporting & History** – Stores test results, failures, and trends.

---

## 3. Interaction with Main Application

- The TA interacts with the MA via its API endpoints.
- Runs scheduled or CI/CD-triggered test cases.
- Logs and reports failures without modifying the MA.

---

## 4. Future Expansion Hooks

- Adversarial input generation
- Auto-healing tests (self-updating test cases)
- CI/CD gatekeeping for deployments

---

➡️ Return to [`README.md`](README.md)
