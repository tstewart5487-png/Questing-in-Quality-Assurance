# Layout Adaptivity Testing

Layout adaptivity testing is a form of compatibility testing that checks whether a website or application can adapt correctly across different devices and environments.

## Testing Types

| Type | Description |
|------|-------------|
| **Compatibility testing** | Checks if the app can adapt across different devices overall |
| **Screen resolution testing** | Ensures the app behaves well between high and low resolution screens |
| **Screen size testing** | Ensures the app looks good on screens of all sizes |
| **Device testing** | Verifies the app is suitable for laptops, tablets, and smartphones |
| **Browser testing** | Confirms the app renders correctly across different web browsers |

---

## Responsive vs Adaptive Design

Both responsive and adaptive design principles come into play during layout adaptivity testing, where QA engineers verify the application works smoothly across devices.

### Responsive Design

Responsive design uses a single layout that automatically adjusts as screen width changes.

- One design created for all devices
- Content is dynamically loaded and displayed
- Uses **percentages** for element sizes rather than fixed pixel values
- Utilises a flexible grid system and fluid layouts
- Breakpoints determine when the layout changes, responding in real time
- Provides a uniform experience across all screen sizes
- General and universal solution

### Adaptive Design

Adaptive design uses multiple predetermined layouts built for specific screen sizes or device types.

- Distinct layout designs for different devices
- Server detects the device type and loads the matching layout
- Element sizes are specified in **pixels**
- Breakpoints are defined and set to fixed dimensions
- More controlled, static layout changes (as opposed to real-time adjustment)
- Offers precise control — better suited to complex projects
- More device-specific approach

### Quick Comparison

| | Responsive | Adaptive |
|---|---|---|
| **Number of layouts** | One | Multiple |
| **Sizing units** | Percentages | Pixels |
| **Layout changes** | Real-time, fluid | Controlled, static |
| **Device detection** | Client-side (CSS) | Server-side |
| **Best for** | General/universal projects | Complex, device-specific projects |
| **Breakpoints** | Dynamic | Fixed |

---

## Tools

QA engineers test across physical devices and virtual environments:

- **[SauceLabs](https://saucelabs.com/)** — cloud-based cross-browser and device testing
- **[LambdaTest](https://www.lambdatest.com/)** — browser and app testing across real devices and emulators

> **Note:** Emulators and simulators (virtual phones/tablets on your computer) are generally used for testing directly downloaded apps, not for testing the responsive design of web applications.