# Open Exam Application - Changelog

This document tracks the significant changes, features, and improvements made to the "Open Exam Application."

## Version 1.7.0 (Current Release)

**Summary:** This is a maintenance and refinement release that significantly overhauls the core question distribution logic to be more intelligent and mathematically sound. It introduces a new proportional distribution algorithm that better respects the `DomainPercentages` defined in the JSON file. This version also fixes a critical UI bug in the custom exam setup, enhances the results screen with more precise sorting, and includes a developer-focused debug mode for validating the new algorithm.

**Key Features & Enhancements:**

1.  **Advanced Proportional Question Distribution Algorithm:**
    *   **Description:** The logic for selecting questions in the "Default Settings" mode has been rewritten to be more accurate and robust, using the **Largest Remainder Method** for proportional distribution.
    *   **Implementation:**
        *   The system now calculates the minimum number of questions required to assign at least one question to each topic defined in `DomainPercentages`.
        *   If the user requests *fewer* questions than this minimum, the system intelligently **falls back to a simple random selection**, ensuring a valid exam can always be generated.
        *   If the user requests *enough* questions, the new algorithm is used to distribute questions in a way that most accurately reflects the specified percentages.

2.  **Enhanced Results Screen Sorting:**
    *   **Description:** The sorting of the "Results by Domain" section has been refined to be more deterministic and logical.
    *   **Implementation:** The results are now sorted primarily in **descending order by performance percentage**, with a secondary **alphabetical (ascending) sort by domain name** to break any ties.

3.  **Developer Debug Mode:**
    *   **Description:** To aid in testing and validation, a debug mode has been added.
    *   **Implementation:** Setting the `DEBUG` constant at the top of the script to `true` will output detailed steps of the new question distribution algorithm to the browser's developer console.

**Bug Fixes:**

1.  **Fixed Custom Question Count Input:**
    *   **Description:** A critical bug was identified where the text input field for a custom number of questions failed to appear when "Custom..." was selected from the dropdown in the "Quick Start" or "Custom Selection" modes.
    *   **Implementation:** This has been corrected, and the input field now displays and functions as expected, allowing users to enter a specific number of questions.

**Testing Notes for Version 1.7.0:**

*   **Bug Fix Verification:** Verify that selecting "Custom..." in the question count dropdown now correctly displays the text input field for a custom number.
*   **Algorithm Testing (Default Mode):**
    *   Using a JSON with `DomainPercentages`, test with a question count *below* the minimum required (e.g., if 4 domains are specified, test with 3 questions). The result should be a random selection.
    *   Test with a question count *above* the minimum. The result should respect the ratios.
    *   Set `DEBUG = true` in the script and check the developer console to validate the algorithm's calculations during the "Default Mode" setup.
*   **Results Sorting:** After an exam, confirm the "Results by Domain" are sorted with the highest percentage first. If two domains have the same percentage (e.g., both 90%), confirm they are sorted alphabetically (e.g., "Art (90%)" appears before "History (90%)").
*   **Regression Testing:** Confirm that the "Quick Start" and "Custom Selection (By Domain)" modes still function correctly.

---

## Version 1.6.0

**Summary:** This is a major feature release focused on providing powerful, user-driven exam customization. It introduces three distinct exam setup modes, including the ability to select questions from specific, sorted topics. This version also adds mobile responsiveness for a seamless experience on any device and enhances the results screen by sorting domain performance to provide clearer feedback.

**Key Features & Enhancements:**

1.  **Advanced Exam Customization:**
    *   **Description:** The exam setup screen has been completely redesigned to offer three clear, powerful modes for generating an exam.
    *   **Implementation:**
        *   **Default Settings:** Uses the configuration from the JSON file (`Number of Questions`, `Default Time`). This mode now intelligently applies `DomainPercentages` only if the requested number of questions is sufficient to meet the ratio requirements; otherwise, it falls back to a random selection.
        *   **Quick Start:** Allows the user to select a number of questions to be drawn randomly from the *entire* question bank.
        *   **Custom Selection (By Domain):** Users can now select one or more specific "Domains of Knowledge" from a dynamically generated, alphabetically sorted list of checkboxes. The exam will then be built using questions *only* from the selected domains.

2.  **Mobile Responsive Design:**
    *   **Description:** The application is now fully responsive and provides an optimized viewing and interaction experience on both desktop and mobile devices.
    *   **Implementation:** CSS media queries have been added to adjust the layout, padding, and font sizes for smaller screens, ensuring excellent usability on phones and tablets. Key inputs are also sized to prevent automatic zooming on iOS.

3.  **Sorted Performance Results:**
    *   **Description:** The post-exam results screen has been improved to provide clearer insights into the user's performance across different topics.
    *   **Implementation:** The "Results by Domain" section is now **sorted in descending order** based on the percentage of correct answers, displaying the user's strongest domains first.

4.  **Intelligent Question Selection Logic:**
    *   **Description:** The "Default Settings" mode is now smarter about applying domain percentage rules from the JSON file.
    *   **Implementation:** The system calculates the minimum number of questions needed to satisfy the `DomainPercentages` (e.g., at least one question per specified domain). If the user (or the JSON default) requests *fewer* questions than this minimum, the system will ignore the percentages and perform a random selection to meet the user's request. This ensures the exam can always be generated.

5.  **Code Quality and Compatibility:**
    *   **Description:** The JavaScript codebase has been refactored for clarity, maintainability, and continued cross-browser support.
    *   **Implementation:** Functions have been refined to have single, clear responsibilities. The application continues to use standard, widely-supported JavaScript features to ensure it runs properly in most modern browsers without external dependencies.

**Testing Notes for Version 1.6.0:**

*   Verify all three exam setup modes ("Default", "Quick Start", "Custom Selection") function as expected.
*   Test the "Custom Selection" mode by selecting single and multiple domains and confirming the question pool is correctly filtered.
*   Confirm the domain list in "Custom Selection" is sorted alphabetically.
*   Test the "Default" mode with a JSON file that has `DomainPercentages` and request a number of questions both above and below the minimum required for the ratio.
*   Verify the domain results on the final screen are sorted from the highest percentage correct to the lowest.
*   Test the application's layout and usability on a mobile device or by resizing the browser window to a narrow width.

---

## Version 1.5.0

**Summary:** This major update introduced robust exam configuration options, allowing users to tailor their exam experience by selecting the number of questions and setting custom time limits. It also enhanced the user interface for loading exams, improved progress tracking, and introduced a versioning system. Compatibility with a new JSON field (`BackNavigation`) for controlling exam flow was added.

**Key Features & Enhancements:**

1.  **Flexible Exam Setup Options:**
    *   **Description:** After loading an exam bank, users are presented with options to configure their exam session.
    *   **Implementation:** A UI section appears post-load where users can choose between "Use default settings" or "Customize number of questions" (with predefined counts or a custom number). A separate input allows setting a custom "Time Limit (minutes)".

2.  **Improved File Input UI & Experience:**
    *   **Description:** The native browser "Choose File" button was replaced with a custom-styled "Browse File" button for a more consistent and prominent appearance. The name of the selected file is now displayed.
    *   **Implementation:** A styled `<button>` proxies clicks to a hidden `<input type="file">`. A `<span>` displays the selected file's name.

3.  **Progress Bar Based on Current Question Position:**
    *   **Description:** The progress bar now reflects the user's current position within the exam (e.g., "Question 5 / 20").
    *   **Implementation:** The `updateProgress()` function now calculates progress based on `currentQuestionIndex`.

4.  **`BackNavigation` Control via JSON:**
    *   **Description:** Exam creators can now disable the "Back" button by adding `"BackNavigation": false` to their exam JSON file.
    *   **Implementation:** The application checks for this field and disables/hides the "Back" button if set to `false`, while maintaining backward compatibility.

5.  **Application Version Display:**
    *   **Description:** The application now displays its version number at the bottom of the page.
    *   **Implementation:** A constant `APP_VERSION` is defined and populated into a dedicated `div` on page load.

**Disclaimer:**

⚠️ **This application and its changelog are primarily AI-generated. Use with caution and always test thoroughly.**