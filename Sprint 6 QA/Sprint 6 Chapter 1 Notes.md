# Chapter 1: Mobile Application Testing & Architecture

## 1. Application Types

### Native Applications
* **Installation:** Must be downloaded and installed locally before use.
* **Performance:** Performs better than web apps because they are not limited by the capacity of the web browser.
* **Device Integration:** Can access all of a device's native functions and hardware.
* **Connectivity:** Many native apps do not require an internet connection to function.
* **Maintenance:** Every update requires users to reinstall the app on each platform separately.

### Hybrid Applications
* **Architecture:** Combines features from both native apps and web apps.
* **Technology Stack:** Much of the code is the same as the web version of the app, utilizing HTML, CSS, and JavaScript.
* **Codebase:** Built using a single codebase that runs across both iOS and Android platforms.
* **Design:** Structural design elements stay uniform across different operating systems.
* **Deployment:** Requires an installation file to be downloaded first.
* **Updates:** Updates seamlessly without requiring the user to reinstall the application.
* **Connectivity:** Requires a permanent internet access connection to function.

### Installation & Testing Files
* **Transfer Methods:** Can be deployed by transferring the installation file from a desktop device to a mobile device.
* **iOS Format:** Uses `.ipa` files.
* **Android Format:** Uses `.apk` or `.aab` files.
* **Use Cases:** These files contain either a beta version of the app for testing or the final release version.

---

## 2. Device Testing Criteria

To properly check how a mobile app works, select devices based on the following hardware and software characteristics:

### Screen Resolution
* **Definition:** The number of pixels that fit into the physical size of the screen (expressed as Horizontal resolution $\times$ Vertical resolution).
* **Browser Impact:** Directly affects how the mobile browser renders the application.
* **UI Bugs:** Clicking borders for the button areas can shift depending on the screen resolution.

### Screen Size
* **Definition:** The physical length and width of the device screen, measured by its diagonal length in inches.
* **Layout Impact:** Different screen sizes affect the layout; elements will not adapt correctly if not optimized.
* **Scaling Issues:** Combining a large screen size with a low resolution causes element sizes to change disproportionately, making them look overly large or layer onto each other.

### Processor
* **Definition:** The nerve center of the device that defines the speed at which a mobile app will run.
* **Performance Variables:** Performance depends directly on the clock rate and the number of processor cores.

---

## 3. Testing Environments & Tools

### Device Matrices
A structured matrix used by QA teams to ensure test coverage across key variables:
* Operating system and its specific version number
* Screen size and resolution
* Phone manufacturer
* Processor type

### Emulators and Simulators
* **Android:** Android Virtual Device (AVD) Manager, which comes embedded into Android Studio.
* **Apple iOS:** Apple iOS Simulator, which comes embedded into Xcode.
