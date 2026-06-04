### 🛠️ Industry Standard Preconditions
*   **Application State:** The application is launched and the user is on the specific input form screen.
*   **Initial Conditions:** The input field is empty; the cursor is not currently focused on the field.
*   **UI Status:** The "Add" button is visible and starts in a disabled/inactive state.

### 🧪 3-Value BVA Test Case Table


| Test Case ID | Requirement | Test Title | Test Data | Detailed Steps | Expected Result | Pass | Fail |
| :--- | :--- | :--- | :--- | :--- | :--- | :---: | :---: |
| **TC-001** | REQ-001 | Non-numeric rejection | `A! @` | 1. Click on input field.<br>2. Type "A", "!", and a space.<br>3. Observe the field. | Input is rejected; field remains empty. | [ ] | [ ] |
| **TC-002** | REQ-003, 006 | **BVA:** Lower Neighbor | `12345678901` | 1. Click input field.<br>2. Enter 11 numeric digits.<br>3. Check "Add" button state. | 11 digits accepted. "Add" button remains **Inactive**. | [ ] | [ ] |
| **TC-003** | REQ-003, 007 | **BVA:** Boundary | `123456789012` | 1. Click input field.<br>2. Enter exactly 12 digits.<br>3. Check "Add" button state. | 12 digits accepted. "Add" button becomes **Active**. | [ ] | [ ] |
| **TC-004** | REQ-003 | **BVA:** Upper Neighbor | `1234567890123` | 1. Click input field.<br>2. Type or paste 13 digits.<br>3. Count characters in field. | Accepts first 12 digits; 13th digit is ignored. | [ ] | [ ] |
| **TC-005** | REQ-004, 005 | Auto-Formatting (Blur) | `123456789012` | 1. Enter 12 digits.<br>2. Click outside the field.<br>3. Observe formatting. | Field displays: `1234 5678 9012`. | [ ] | [ ] |
| **TC-006** | REQ-002, 003 | Paste Truncation | `1122334455667788` | 1. Copy a 16-digit number.<br>2. Paste into the input field.<br>3. Check field content. | Field contains only first 12 digits: `112233445566`. | [ ] | [ ] |

### ✅ Interactive Execution Checklist
- [ ] **TC-001:** Non-numeric Rejection
- [ ] **TC-002:** BVA Lower Neighbor (11 digits)
- [ ] **TC-003:** BVA Boundary (12 digits)
- [ ] **TC-004:** BVA Upper Neighbor (13 digits)
- [ ] **TC-005:** State Transition (Blur) Formatting
- [ ] **TC-006:** Paste Truncation (16 digits)
