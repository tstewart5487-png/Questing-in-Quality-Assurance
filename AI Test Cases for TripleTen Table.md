### 🛠️ Preconditions
*   **Application State:** The Urban Grocer web application is opened, and the user is logged into an account.
*   **Navigation:** The user has opened the profile settings or payment methods section, and the "Add Card" modal/payment field is visible.
*   **Initial Conditions:** The "Card Number" input field is completely empty; the field is out of focus.
*   **UI Status:** The "Add" button is visible inside the card management layout and starts in a disabled/inactive state.

### 🧪 3-Value BVA Test Case Table


| Test Case ID | Requirement | Test Title | Test Data | Detailed Steps | Expected Result | Pass | Fail |
| :--- | :--- | :--- | :--- | :--- | :--- | :---: | :---: |
| **TC-001** | REQ-001 | Reject Non-Numeric Input | `ABCD !@#$` | 1. Click on the "Card Number" input field.<br>2. Type alphabetical characters "ABCD".<br>3. Type special characters "!@#$".<br>4. Observe the field. | The field rejects the input. No characters appear. The input field remains completely empty. | [ ] | [ ] |
| **TC-002** | REQ-003, 006 | **3-Value BVA:** Lower Neighbor (11 Digits) | `12345678901` | 1. Click on the empty "Card Number" input field.<br>2. Type exactly 11 numeric digits.<br>3. Observe the state of the "Add" button. | 11 digits are accepted and displayed in the field. The "Add" button remains disabled/inactive. | [ ] | [ ] |
| **TC-003** | REQ-003, 007 | **3-Value BVA:** Boundary Limit (12 Digits) | `123456789012` | 1. Click on the empty "Card Number" input field.<br>2. Type exactly 12 numeric digits.<br>3. Observe the state of the "Add" button. | 12 digits are accepted and displayed in the field. The "Add" button becomes enabled/active. | [ ] | [ ] |
| **TC-004** | REQ-003 | **3-Value BVA:** Upper Neighbor (13 Digits) | `1234567890123` | 1. Click on the empty "Card Number" input field.<br>2. Type 13 numeric digits sequentially.<br>3. Count the total characters registered in the field. | The field accepts only the first 12 digits. The 13th digit (`3`) is ignored. Character length stops at 12. | [ ] | [ ] |
| **TC-005** | REQ-004, 005 | Auto-Formatting Space Insertion (Blur Event) | `123456789012` | 1. Click on the "Card Number" field and enter 12 digits.<br>2. Click outside the input field (trigger a blur event to remove focus).<br>3. Observe the visual string formatting. | Spaces are automatically added. The field visually updates to display the card number as: `1234 5678 9012`. | [ ] | [ ] |
| **TC-006** | REQ-002, 003 | Large Input Clipboard Paste Truncation | `1122334455667788` | 1. Copy a 16-digit numeric string to the clipboard.<br>2. Right-click the empty "Card Number" field and select "Paste" (or use Ctrl+V / Cmd+V).<br>3. Inspect the field contents. | The system processes the paste action but truncates the value, preserving only the first 12 digits: `112233445566`. | [ ] | [ ] |

### ✅ Interactive Execution Checklist
- [ ] **TC-001:** Reject Non-Numeric Input
- [ ] **TC-002:** 11 Digits Entered (Button Stays Inactive)
- [ ] **TC-003:** 12 Digits Entered (Button Activates)
- [ ] **TC-004:** 13 Digits Typed (Truncation at 12)
- [ ] **TC-005:** Blur Event Triggered (Formatting Check)
- [ ] **TC-006:** 16 Digits Pasted (Truncation Check)
