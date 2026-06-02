# Software Testing Architecture & Taxonomy Reference

A comprehensive, hierarchical index mapping out every testing methodology from the reference architecture chart, complete with isolated definitions for each branch and an integrated ascii flowchart.

---

## 🗺️ Software Testing Classification Flowchart

This flowchart outlines the structural pathways from the original architecture diagram, mapping high-level methodologies down to specific execution types.

```text
                        [ Software Testing Types ]
                                    │
                  ┌─────────────────┴─────────────────┐
                  ▼                                   ▼
             [ Manual ]                          [ Automated ]
                  │                                   │
                  └─────────────────┬─────────────────┘
                                    │
                  ┌─────────────────┴─────────────────┐
                  ▼                                   ▼
           [ Functional ]                     [ Non-Functional ]
                  │                                   │
      ┌───────────┼───────────┐           ┌───────────┼───────────┐
      ▼           ▼           ▼           ▼           ▼           ▼
   [Unit]    [Integration] [System]   [Acceptance] [Security] [Performance] [Usability/Comp]
      │           │           │           │           │           │              │
      ▼           ▼           ▼           ▼           ▼           ▼              ▼
   (White-     (Gray-      (Black-     (Alpha       (Direct    (Load Testing) (Exploratory
    Box)        Box)        Box)        Testing)    Testing)       │             Testing)
                              │           │                       ├──► Stress    │
                              ├──► E2E    ├──► Beta               ├──► Scalabil. ├──► Browser
                              ├──► Smoke  └──► UAT                ├──► Spike     └──► Accessib.
                              ├──► Sanity                         ├──► Endurance
                              ├──► Regres.                        └──► Soak
                              └──► UI
```

---

## 🏗️ 1. Root Methodology Execution

* **Software Testing Types**: The broad discipline of executing a program or application with the intent of finding software bugs and verifying compliance with requirements.
* **Manual**: Tests executed manually by a human QA tester interacting directly with software UI and logs without utilizing automation scripts.
* **Automated**: Tests executed programmatically by software tools running pre-written scripts, code assertions, or test automation frameworks.

---

## ⚙️ 2. Functional Testing Branch

Verifies that the software application operates in strict compliance with defined functional business requirements, inputs, and expected behavioral specifications.

### Unit Testing Scope
* **Unit Testing**: Isolating and testing the smallest testable units of source code—such as individual methods, classes, or functions.
* **White-Box Testing**: A code-level validation methodology where the tester has full visibility into the internal software logic paths, control structures, and source loops.

### Integration Testing Scope
* **Integration Testing**: Verifying that separate software modules, databases, components, or third-party API configurations interact seamlessly when combined.
* **Gray-Box Testing**: A hybrid strategy where the tester has partial knowledge of internal code structures, database schemas, or system architecture layouts.

### System Testing Scope
* **System Testing**: Evaluating the fully integrated, end-to-end software application as a unified whole against initial project prerequisites.
* **Black-Box Testing**: Testing software functionality exclusively from an end-user perspective, with zero visibility into or knowledge of the underlying source code structure.
* **End-to-End Testing**: Tracking and verifying continuous data flows and holistic journeys from the very first user interaction through back-end servers and database updates.
* **Smoke Testing**: Executing a rapid, high-level suite of basic functionality tests to verify that a freshly deployed software build is stable enough to proceed with deeper testing.
* **Sanity Testing**: A quick, highly focused test suite executed immediately following a code change to verify that a specific bug fix or localized revision works properly.
* **Regression Testing**: Re-running existing test scripts to guarantee that recent code alterations, performance optimizations, or framework updates did not inadvertently break pre-existing features.
* **User-Interface (UI) Testing**: Verifying Front-end layout elements, buttons, input fields, forms, and typography scale, render, and execute actions accurately per design wireframes.

### Acceptance Testing Scope
* **Acceptance Testing**: Validating if the application satisfies final user needs and contract terms to determine deployment readiness.
* **Alpha Testing**: Internal end-to-end quality validation performed exclusively by the company’s internal developers and software QA engineers within a controlled laboratory environment.
* **Beta Testing**: Releasing a polished, pre-release version of the application to a restricted pool of real-world end-users to gather authentic user feedback.
* **UAT (User Acceptance Testing)**: The final verification checkpoint where business stakeholders, clients, or targeted product users validate that delivery satisfies business expectations.

---

## ⚡ 3. Non-Functional Testing Branch

Evaluates the overall operational traits, behavioral characteristics, environmental limits, and performance parameters of the software build.

### Security Testing Scope
* **Security Testing**: Probing application layers to evaluate data protection systems, authentication boundaries, permission configurations, and vulnerability safeguards against potential security exploits.

### Performance Testing Scope
* **Performance Testing**: Evaluating application speed, system responsiveness, infrastructure stability, and resource usage metrics across multiple load configurations.
* **Load Testing**: Monitoring system behavior, execution delays, and hardware metrics under predictable, everyday target user volumes.
* **Stress Testing**: Intentional over-loading of software infrastructure beyond official design capacities to identify its breaking threshold and verify system error recovery behaviors.
* **Scalability Testing**: Checking the platform's capacity to adjust resources programmatically (such as dynamically scaling memory or database sizes) to support increasing transaction volumes.
* **Spike Testing**: Evaluating how structural workloads and servers recover when concurrent client traffic volumes surge drastically and instantaneously.
* **Endurance Testing**: Applying a sustained, typical operational volume threshold over extended runtime windows to inspect the platform for slow server performance degradation.
* **Soak Testing**: Long-horizon execution profiling under heavy loads to track memory leaks, connection pool issues, or gradual server resource starvation over time.

### Usability and Compatibility Testing Scope
* **Usability and Compatibility Testing**: Confirming user-friendliness, seamless device-matching layout rendering, and accessibility tool compliance across target runtimes.
* **Exploratory Testing**: An unscripted, highly creative manual testing methodology where testing exploration and test case design occur simultaneously based on QA expertise.
* **Browser Testing**: Validating the styling layout consistency, viewport sizing, and script executions of web pages across distinct browser variations (e.g., Chrome, Safari, Firefox).
* **Accessibility Testing**: Ensuring digital interfaces comply with strict assistive standard tools (such as high-contrast requirements or screen reader accessibility) for individuals with disabilities.
