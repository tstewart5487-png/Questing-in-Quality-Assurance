## Cross-Browser Testing

- A type of **compatibility testing** and **non-functional testing**
- Tests whether an app functions consistently and smoothly across different browsers, platforms, devices, operating systems, and screen resolutions
- Required any time changes have been implemented in the layout

| Testing Type | Scope | Category |
|---|---|---|
| Operation Logic | Testing in one browser | Functional |
| Layout | Cross-browser testing | Non-Functional |

---

### 🖥️ Platform Testing
Also known as **device testing** — ensures applications work across different device types.

- **Desktop:** PCs and laptops
- **Mobile:** Smartphones and tablets

---

### ⚙️ Operating System Testing
Checks that apps work well with various operating systems.

| Desktop | Mobile |
|---|---|
| Windows | iOS |
| macOS | Android |
| Linux | |

---

### 🌐 Web Browser Testing
Ensures the app works well across different web browsers.

- Chrome
- Firefox
- Safari
- Edge
- Opera

> 💡 Don't forget to check different browser versions from the requirements document to avoid browser-specific bugs.

---

### 📐 Screen Resolution Testing
- HD
- Non-HD
- 1400 x 900
- 1280 x 768
- Retina

---

## DevTools: Emulating Platforms

1. **Open DevTools**
   - Windows: `Ctrl + Shift + C`
   - macOS: `Cmd + Opt + C`

2. **Activate the Device Toolbar**
   Click the device icon in the top-left corner. This allows you to view the website as if you were using various devices (e.g. iPhone SE, Android tablet).

3. **Choose a Device**
   Select a device from the dropdown in the upper-left corner. Click **Edit** in the Dimensions dropdown to customize your device options.