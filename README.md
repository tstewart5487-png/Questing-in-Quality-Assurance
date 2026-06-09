# 🐵 Chaos Monkey - QA Testing Repository

A comprehensive QA testing and documentation repository featuring test cases, automation scripts, and quality assurance lessons for the **Urban Grocer** web application.

## 📋 Overview

This repository contains structured QA documentation, test case management, and testing scripts organized by sprint cycles. It serves as a learning resource and reference guide for quality assurance methodologies, boundary value analysis, and systematic testing practices.

**Repository Type:** QA Documentation & Testing  
**Primary Language:** Python  
**Status:** Active

## 📁 Repository Structure

```
Chaos-Monkey-.-/
├── main.py                              # Main Python automation script
├── AI Test Cases for TripleTen Table.md # Detailed test case documentation
├── Bridge Course/                       # Bridge course materials
├── Sprint 1 QA/                         # Sprint 1 QA test cases and reports
├── Sprint 2 QA/                         # Sprint 2 QA test cases and reports
├── Sprint 3 QA/                         # Sprint 3 QA test cases and reports
├── Jira/                                # Jira-related documentation
├── Trello/                              # Trello board exports and planning
└── .idea/                               # IDE configuration files
```

## 🧪 Key Features

### Test Case Documentation
- **Boundary Value Analysis (BVA)** - 3-value test cases with lower neighbor, boundary, and upper neighbor values
- **Comprehensive Test Coverage** - Test cases organized by requirement and functionality
- **Urban Grocer Application** - Focus on payment input validation and card number processing

### Sprint-Based Organization
- **Sprint 1 QA** - Initial QA documentation and foundational test cases
- **Sprint 2 QA** - Expanded testing scope and additional scenarios
- **Sprint 3 QA** - Advanced testing and edge case validation

### Testing Artifacts
- Test case tables with detailed steps and expected results
- Interactive execution checklists
- Requirements mapping and traceability
- Jira and Trello integration documents

## 📝 Test Case Example

The repository includes detailed test cases such as:

| Test Case | Focus Area | Key Validation |
|-----------|-----------|-----------------|
| TC-001 | Non-Numeric Input Rejection | Alphabetic and special character handling |
| TC-002 | Boundary Value Lower Neighbor | 11-digit card number validation |
| TC-003 | Boundary Value Limit | 12-digit card number validation |
| TC-004 | Boundary Value Upper Neighbor | 13-digit truncation behavior |
| TC-005 | Auto-Formatting | Space insertion on blur event |
| TC-006 | Clipboard Paste | Large input truncation |

## 🚀 Getting Started

### Prerequisites
- Python 3.x (for automation scripts)
- Text editor or IDE (for reviewing documentation)
- GitHub access to this repository

### Running Tests

To execute the main Python script:

```bash
python main.py
```

### Reviewing Documentation

1. Start with `AI Test Cases for TripleTen Table.md` for foundational test case examples
2. Navigate to respective `Sprint X QA` folders for sprint-specific documentation
3. Reference Jira and Trello folders for project tracking details

## 📚 QA Methodology

This repository emphasizes:

- **Boundary Value Analysis (BVA)** - Testing at boundaries and limits
- **Requirements-Based Testing** - Mapping test cases to specific requirements
- **Systematic Test Planning** - Organized by sprint and functionality
- **Traceability** - Clear linkage between requirements and test cases

## 🔄 Sprint Cycles

Testing is organized by sprint milestones:

- **Bridge Course** - Initial setup and foundational concepts
- **Sprint 1 QA** - Foundation phase testing
- **Sprint 2 QA** - Development phase testing
- **Sprint 3 QA** - Advanced phase testing

## 📊 Documentation Files

- **AI Test Cases for TripleTen Table.md** - Detailed BVA test cases for Urban Grocer payment input validation
- **Jira/** - Contains Jira-related planning and issue tracking
- **Trello/** - Contains Trello board data and task organization

## 🛠️ Tools & Integration

- **Jira** - Issue tracking and requirements management
- **Trello** - Task board and sprint planning
- **Python** - Automation and scripting
- **GitHub** - Version control and documentation

## 👤 Author

Created by **tstewart5487-png**

## 📄 License

This repository is currently unlicensed. For licensing information, please contact the repository owner.

## 💬 Contributing

For contributions, issues, or suggestions:
1. Create a new issue in the repository
2. Follow existing documentation standards
3. Reference sprint cycles and requirements where applicable

## 📞 Support

For questions or clarifications about test cases and documentation, refer to the specific sprint folders or test case files included in this repository.

---

**Last Updated:** June 2026  
**Status:** Active Development
