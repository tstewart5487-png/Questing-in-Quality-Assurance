# Software Testing Life Cycle (STLC) & Requirement Analysis Guide

A comprehensive guide covering the structured sequence of QA testing phases and the core principles of requirement decomposition and analysis.

---

## 🧭 Part 1: Software Testing Life Cycle (STLC)

The **Software Testing Life Cycle (STLC)** is a structured sequence of specific phases executed by Quality Assurance (QA) teams to ensure software quality and compliance with requirements.

### 📋 1. Requirement Analysis
QA teams collaborate with stakeholders, developers, and business analysts to identify testable features and clarify ambiguities.
* **Activities**
  * Review functional and non-functional requirements.
  * Identify testing scope and boundaries.
  * Define initial test priorities.
* **Deliverables**
  * Requirements Traceability Matrix (RTM)
  * High-level test scenarios

### 🗺️ 2. Test Planning
A senior QA lead or manager determines the strategic blueprint, resource allocation, and overall timeline for the testing cycle.
* **Activities**
  * Assess project risks and constraints.
  * Estimate testing effort and timelines.
  * Select testing tools and frameworks.
* **Deliverables**
  * Comprehensive **Test Plan** document
  * Effort estimation matrices

### ✍️ 3. Test Design (Test Case Development)
Testers translate high-level requirements into detailed, step-by-step instructions to verify specific software behaviors.
* **Activities**
  * Write detailed manual test cases.
  * Create automated test scripts.
  * Prepare required test data.
* **Deliverables**
  * Approved **Test Cases**
  * Test automation scripts
  * Test data blocks

### 🖥️ 4. Test Environment Setup
The infrastructure, servers, and software conditions are configured to mirror a production environment as closely as possible.
* **Activities**
  * Deploy hardware and network infrastructure.
  * Install testing software and tools.
  * Perform smoke testing to ensure environment stability.
* **Deliverables**
  * Fully operational **Test Environment**
  * Successful smoke test results

### 🚀 5. Test Execution
The engineering team actively runs the designed test cases against the software build to spot discrepancies.
* **Activities**
  * Execute manual and automated test cases.
  * Log found bugs and defects in tracking tools.
  * Track and retest resolved issues.
* **Deliverables**
  * Test execution reports
  * **Bug/Defect logs**
  * Updated RTM

### 🏁 6. Test Closure
The final phase wraps up the cycle by assessing results, documenting metrics, and confirming product release readiness.
* **Activities**
  * Evaluate test completion metrics.
  * Document lessons learned and retrospective notes.
  * Summarize product quality.
* **Deliverables**
  * **Test Summary Report**
  * Finalized quality metrics

---

## 🔍 Part 2: Deep Dive into Requirement Analysis

**Requirement Analysis** is the foundational phase of the STLC. It involves analyzing project requirements to fully understand what the software should do, what it should not do, and how to verify its behavior.

### 📌 Types of Requirements

#### Functional Requirements
* Define what a piece of software can or cannot do.
* Focus on core capabilities, features, and user actions.

#### Non-Functional Requirements
* Describe the software's overall qualities, attributes, and characteristics.
* Focus on operational parameters:
  * **Performance** (speed, responsiveness, scalability)
  * **Security** (data protection, access control)
  * **Usability** (user experience, accessibility)
  * **Reliability** (uptime, error handling)

### 💡 S.M.A.R.T. Requirements Framework

To be effectively tested, requirements must follow the **S.M.A.R.T.** criteria:

* **S**pecific: Clear, focused, and free of ambiguity or uncertainty.
* **M**easurable: Objective with explicit success criteria.
* **A**ttainable: Achievable within project scopes and available resources.
* **R**ealistic: Practical and strictly aligned with project goals.
* **T**estable: Should be verifiable by testing.

### 🛠️ Decomposing Requirements

In the QA world, we take a complex requirement and break it down logically to test individual components.

#### Decomposition Rules
* Requirements must be broken down into **atomic blocks**.
* Requirements should **not** be decomposed beyond the description.

#### What is an Atomic Block?
* The smallest, most basic part of a feature.
* The smallest piece that remains useful on its own.
* A requirement unit that cannot be broken down any further.

### 🗺️ Visualizing Requirements

#### Mind Maps
* Used to visualize distinct components and feature hierarchies.
* **Tools**: `draw.io`, `Xmind`, `Miro`

#### Flow Charts
* Acts as a roadmap or process of steps.
* Represents the user's journey through the application.
* Maps the exact flow of information and actions from beginning to end.
* **Tools**: `draw.io`, `gliffy.com`, `lucidchart.com`, `Miro`

#### Standard Flow Chart Symbols


| Shape Name | Visual Representation | Meaning / Function |
| :--- | :---: | :--- |
| **Rounded Rectangle** (Oval / Terminator) | `( Start / End )` | The start and end points of the flowchart |
| **Rectangle** (Process) | `[ Action Step ]` | A process step, action, or operation (e.g., login, save data) |
| **Diamond** (Decision) | `< Decision >` | A conditional branch evaluation (Yes/No or True/False question) |

### 🌫️ Handling "Gray Areas"

Gray areas are unclear, incomplete, hidden, or conflicting requirements discovered during analysis.

#### What to Do:
1. **Exploratory Testing**: Keep trying variations and investigate the application behavior actively.
2. **Check Similar Scenarios**: Look at existing test cases or comparable systems for baseline expectations.
3. **Clarify Requirements**: Engage stakeholders to remove ambiguity.

#### Key Questions to Ask for Clarification:
* What does it do?
* How does it work?
* What’s it for?
* How do users use it?
* What does it impact?
