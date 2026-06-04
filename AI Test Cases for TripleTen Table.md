### 🛠️ Preconditions
*   **Application State:** The Urban Grocer web application is opened, and the user is logged into an account.
*   **Navigation:** The user has clicked on "Add card" to open the payment modal overlay.
*   **Initial Conditions:** The "Card number (not yours):" input field is completely empty and out of focus.
*   **UI Status:** The "Link" button is visible inside the modal layout and starts in a disabled/inactive state (greyed out).

### 🧪 3-Value BVA Test Case Table


| Test Case ID | Requirement | Test Title | Test Data | Detailed Steps | Expected Result | Pass | Fail |
| :--- | :--- | :--- | :--- | :--- | :--- | :---: | :---: |
| **TC-001** | REQ-001 | Reject Non-Numeric Input | `A! @` | 1. Click on the "Card number (not yours):" input field.<br>2. Type alphabetical character "A".<br>3. Type special characters "! @".<br>4. Observe the field. | The field rejects the input. No characters appear. The input field remains completely empty. | [ ] | [x ] |
| **TC-002** | REQ-003, 006 | **3-Value BVA:** Lower Neighbor (11 Digits) | `12345678901` | 1. Click on the empty "Card number (not yours):" input field.<br>2. Type exactly 11 numeric digits.<br>3. Observe the state of the "Link" button. | 11 digits are accepted and displayed in the field. The "Link" button remains disabled/inactive (greyed out). | [ ] | [ ] |
| **TC-003** | REQ-003, 007 | **3-Value BVA:** Boundary Limit (12 Digits) | `123456789012` | 1. Click on the empty "Card number (not yours):" input field.<br>2. Type exactly 12 numeric digits.<br>3. Observe the state of the "Link" button. | 12 digits are accepted and displayed in the field. The "Link" button becomes enabled/active (changes from grey). | [ ] | [ ] |
| **TC-004** | REQ-003 | **3-Value BVA:** Upper Neighbor (13 Digits) | `1234567890123` | 1. Click on the empty "Card number (not yours):" input field.<br>2. Type 13 numeric digits sequentially.<br>3. Count the total characters registered in the field. | The field accepts only the first 12 digits. The 13th digit (`3`) is ignored. Character length stops at 12. | [ ] | [ ] |
| **TC-005** | REQ-004, 005 | Auto-Formatting Space Insertion (Blur Event) | `123456789012` | 1. Click on the "Card number (not yours):" field and enter 12 digits.<br>2. Click outside the input field (trigger a blur event to remove focus).<br>3. Observe the visual string formatting. | Spaces are automatically added. The field visually updates to display the card number as: `1234 5678 9012`. | [ ] | [ ] |
| **TC-006** | REQ-002, 003 | Large Input Clipboard Paste Truncation | `1122334455667788` | 1. Copy a 16-digit numeric string to the clipboard.<br>2. Right-click the empty "Card number (not yours):" field and select "Paste" (or use Ctrl+V / Cmd+V).<br>3. Inspect the field contents. | The system processes the paste action but truncates the value, preserving only the first 12 digits: `112233445566`. | [ ] | [ ] |

### ✅ Interactive Execution Checklist
- [ ] **TC-001:** Reject Non-Numeric Input
- [ ] **TC-002:** 11 Digits Entered (Link Button Stays Inactive)
- [ ] **TC-003:** 12 Digits Entered (Link Button Activates)
- [ ] **TC-004:** 13 Digits Typed (Truncation at 12)
- [ ] **TC-005:** Blur Event Triggered (Formatting Check `nnnn nnnn nnnn`)
- [ ] **TC-006:** 16 Digits Pasted (Truncation Check)
