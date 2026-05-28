# 📋 QA Responsibilities by Development Stage

Every development task is divided into structured stages. QA engineers hold critical responsibilities throughout each phase of this lifecycle.

---

## 🗺️ Visual Workflow

GitHub natively renders the flowchart below to show how QA work mirrors the development track.

```mermaid
graph TD
    %% Define Styles
    classDef stage fill:#f9f9f9,stroke:#333,stroke-width:2px;
    classDef qa fill:#e1f5fe,stroke:#0288d1,stroke-width:1px;
    classDef note fill:#fff9c4,stroke:#fbc02d,stroke-width:1px;

    %% Workflow Flowchart
    subgraph Development_Lifecycle [Development Lifecycle & QA Workflow]
        
        %% Stage 1
        S1[1. Setting the Task<br><i>Manager formulates requirements</i>] --> Q1(QA Phase: Planning<br>• Estimate testing time)
        class S1 stage; class Q1 qa;

        %% Stage 2
        Q1 --> S2[2. Estimation<br><i>Team reviews requirements</i>]
        S2 --> Q2(QA Phase: Test Analysis<br>• Analyze layouts & details<br>• Clarify gray areas)
        class S2 stage; class Q2 qa;

        %% Stage 3 (Parallel Track)
        Q2 --> S3[3. Development<br><i>Developers write code</i>]
        
        subgraph Parallel_Execution [Parallel Action]
            S3 --> Q3(QA Phase: Test Design<br>• Create checklists<br>• Write test cases)
        end
        class S3 stage; class Q3 qa;

        %% Stage 4
        Q3 --> S4[4. Testing<br><i>Execute tests & fix bugs</i>]
        S4 --> Q4(QA Phase: Test Execution<br>• Log bug reports<br>• Provide final status reports)
        class S4 stage; class Q4 qa;

    end

    %% Key Concept Note
    N1[💡 Key Concept:<br>QA designs tests simultaneously<br>while developers write code.<br>Materials are ready instantly!] 
    class N1 note;
    Q3 -.-> N1
```

---

## ⚡ Interactive Tracking Table

Use the checkboxes directly inside your GitHub repository or issue description to track your QA team's progress for each task.


| Stage | QA Phase | Core Responsibilities | Deliverables / Status |
| :--- | :--- | :--- | :--- |
| **1. Setting the Task** | `Planning` | <ul><li>[ ] Evaluate total testing time</li><li>[ ] Assess initial requirements</li></ul> | `⏱️ Awaiting Estimate` |
| **2. Estimation** | `Test Analysis` | <ul><li>[ ] Analyze requirements and layouts</li><li>[ ] Clarify gray areas with stakeholders</li></ul> | `🔍 In Progress` |
| **3. Development** | `Test Design` | <ul><li>[ ] Create testing checklists</li><li>[ ] Write detailed test cases</li></ul> | `✍️ Paralleled with Dev` |
| **4. Testing** | `Test Execution` | <ul><li>[ ] Test new app features</li><li>[ ] Document and log bug reports</li><li>[ ] Deliver final feature status reports</li></ul> | `🚀 Ready to Execute` |

> 💡 **Parallel Workflow Tip:** While developers are busy writing code, QA engineers are actively designing tests. By the time development finishes, testing materials are already live and ready to deploy.
