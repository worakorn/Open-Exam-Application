# Open Exam Application - Changelog

This document tracks the significant changes, features, and improvements made to the "Open Exam Application."

## Version 2.0.0 (Cutting Edge)
**File:** `exam-next.html`

**Summary:** This major release introduces the mathematically rigorous Computerized Adaptive Testing (CAT) engine. It also includes all 30+ stability patches and bug fixes from v1.9.1. 

**Key Features & Enhancements:**
1.  **Computerized Adaptive Testing (CAT) Engine:**
    *   **Sliding Window Algorithm:** Introduces a principled 3-question sliding window algorithm to dynamically adjust problem difficulty based on real-time performance.
    *   **Domain Balancing Logic:** Intelligently prioritizes under-represented knowledge domains to ensure broad exam coverage while adapting difficulty.
    *   **Advanced Stopping Criteria:** Implements "Early Fail" (mathematically impossible to pass), "Mastery" (5 consecutive correct answers at high difficulty), and standard Max Questions limits.
    *   **Stateful History:** Uses boolean answer history tracking to eliminate index-mismatch calculation bugs.
    *   **Real-time Analytics:** Notifies users in-test when passing is no longer statistically possible.
2.  **Hardened Stability & Security (Inherited from 1.9.1):**
    *   Validates protocols (`http/https`) before fetching JSON.
    *   Strict schema validation with `validateExamData` to enforce minimum requirements.
    *   Robust component state resets between exam sessions.
    *   XSS-safe DOM node creation.

## Version 1.9.1 (Stable)
**File:** `exam.html`

**Summary:** This release includes 30+ critical bug fixes, stability patches, and security improvements contributed by the community (Special thanks to bank4500 / Aj. Bank). It focuses on hardening the application's core logic without changing its outward features.

**Key Features & Enhancements:**
1.  **Strict Validation:** `validateExamData` now rigorously enforces `Questions` arrays, properties, and choice minimums to prevent invalid exams from loading.
2.  **Logic & Math Fixes:**
    *   Fixed a bug where unanswered questions resulted in NaN confidence scores (now correctly calculated as 0).
    *   Fixed infinite loops and `shuffleArray` behavior in proportional question distribution spreading.
    *   Prevented negative confidence scores by properly clamping the bounds between 0 and 100.
    *   Fixed time accumulation logic so returning to previous questions (`goBack`) accurately records total time spent.
3.  **UI & Security Improvements:**
    *   Implemented proper timer clearing (`clearInterval`) on exam restarts to fix memory leaks and double-ticking.
    *   Prevented double-submission of exams via UI debounce.
    *   Added safe generation of DOM nodes (removed `.innerHTML` usage in review listings) to prevent Cross-Site Scripting (XSS).
    *   Fixed missing ID association on setup screen checkboxes by utilizing safe index-based IDs.
    *   Added explicit `<html lang="en">` tag for SEO and accessibility.

## Version 1.9.0

**Summary:** This major release delivers a comprehensive visual transformation with a modern purple gradient theme, enhanced UI/UX throughout, improved mobile responsiveness, and optimized layout for better viewport utilization. All improvements are purely visual/UX focused while maintaining 100% functional compatibility.

**Key Features & Enhancements:**

1.  **Comprehensive UI/UX Overhaul:**
    *   **Modern Color Theme:** Introduced stunning purple gradient background (#667eea to #764ba2) throughout the application
    *   **Enhanced Container:** Premium elevated card design with enhanced shadows (0 20px 60px) and larger border radius (16px)
    *   **Gradient Typography:** Title text features purple gradient fill with transparent text for modern appearance
    *   **Improved Visual Hierarchy:** Better font weights (700-800), letter spacing, and size differentiation across all headings

2.  **Form & Input Improvements:**
    *   **Enhanced Input Fields:** Thicker borders (2px), larger border radius (8px), better focus states with purple accent (#667eea)
    *   **Purple Focus Rings:** Consistent purple shadow rings on all interactive elements
    *   **Better Transitions:** Smooth cubic-bezier animations throughout

3.  **Question Display Enhancements:**
    *   **Card-Based Layout:** Questions now appear in white cards with shadows for better separation
    *   **Enhanced Choice Elements:**
        *   Thicker borders and better hover effects (translateY lift animation)
        *   Purple accents when hovered or selected
        *   Clear visual feedback with background color change on selection
        *   Larger radio buttons (scale 1.2) with purple accent color

4.  **Button & Navigation Improvements:**
    *   **Enhanced Buttons:** Better padding, rounded corners (10px), improved shadows
    *   **Gradient Buttons:** Start button features purple gradient matching theme
    *   **Hover Effects:** Lift animations (translateY -2px) with enhanced shadows
    *   **Improved States:** Better disabled states with opacity

5.  **Progress Indicators:**
    *   **Gradient Progress Bar:** Purple gradient fill (90deg) with enhanced shadow
    *   **Better Animation:** Smoother transitions with cubic-bezier easing
    *   **Taller Bar:** Increased to 14px for better visibility

6.  **Setup Screen Enhancements:**
    *   **Card-Style Radio Options:** Already enhanced in 1.8.5, further polished with consistent spacing
    *   **Purple Section Headers:** Bold headers with 3px purple underline
    *   **Gradient Summary Box:** Settings summary with purple gradient background and border
    *   **Enhanced Time Warning:** Prominent yellow box with icon and description

7.  **Mobile Responsiveness & Display:**
    *   **Proper Viewport Meta Tags:** Added for optimal mobile display
    *   **Enhanced Version Info:** White background box with shadow for visibility against gradient
    *   **Offline Capability:** Confirmed fully offline-capable (all resources embedded)
    *   **Better Mobile Spacing:** Optimized padding and margins for mobile devices
    *   **Touch-Friendly:** Larger tap targets and better spacing on small screens

8.  **Layout Optimization:**
    *   **Reduced Vertical Spacing:** Minimized padding and margins throughout
    *   **Compact Design:** Smaller font sizes and tighter layout for better viewport utilization
    *   **Less Scrolling:** Optimized to show more content in single viewport
    *   **Better Space Efficiency:** Reduced container margins (30px→15px) and padding (40px→25px)

9.  **Results Screen (from 1.8.6+):**
    *   **Colorful Gradient Cards:** Score, Correct, Incorrect, and Unanswered metrics in gradient cards
    *   **Performance Badges:** Dynamic badges based on score (🏆 Excellent, ⭐ Great, 👍 Good, etc.)
    *   **Icons Throughout:** SVG icons for better visual communication
    *   **Better Organization:** Clear sections with proper spacing and borders

10. **User Experience Polish:**
    *   **Consistent Shadows:** Multiple shadow layers for depth throughout
    *   **Smooth Transitions:** Cubic-bezier easing for premium feel
    *   **Better Contrast:** Improved text colors and backgrounds for readability
    *   **Visual Feedback:** Clear hover states and selected indicators
    *   **Terms of Use Visibility:** Only shown on first page for cleaner interface during exam

**Internal Version Tracking:**
*   Started at: 20251124001
*   Final: 20251124005
*   Note: Internal versions track development iterations

**Testing Notes for Version 1.9.0:**

*   **Visual Verification:** Open exam.html and verify purple gradient background displays correctly
*   **Title Text:** Confirm gradient text effect on "Open Exam Application" title
*   **Form Inputs:** Test focus states show purple rings
*   **Question Display:** Verify choices have lift animation on hover and purple accent when selected
*   **Progress Bar:** Confirm purple gradient fill during exam
*   **Mobile Display:** Test on mobile device or resize browser - version info should be clearly visible
*   **Layout Density:** Verify more content fits in viewport with reduced need for scrolling
*   **Buttons:** Test all buttons have smooth hover effects with lift animation
*   **Results Screen:** Complete exam and verify gradient cards display correctly
*   **Overall Polish:** Confirm entire interface feels modern, cohesive, and professional

---

## Version 1.8.5

**Summary:** This release focuses on user transparency and legal clarity by adding a prominent disclaimer and a comprehensive "Terms of Use" section to the application's main page.

**Key Features & Enhancements:**

1.  **Disclaimer Box:**
    *   A disclaimer is now displayed on the initial page, informing users that the application is free to use and can be downloaded for offline use to enhance privacy.

2.  **User Agreement Section:**
    *   A detailed "Terms of Use" section has been added to the bottom of the page, covering:
        *   Acknowledgement that the software is AI-generated.
        *   A clear disclaimer of warranty.
        *   Explicit statements on usage rights (free for personal/commercial use, distribution, and modification).
        *   A prohibition on selling the software.
        *   Privacy recommendations and a link to the GitHub repository.
        *   Contact information.

## Version 1.8.4 (Current Release)

**Summary:** This release introduces sophisticated performance analytics to provide users with deeper insights into their test-taking habits. Key features include a "Confidence Score" that evaluates both speed and accuracy, optional time warnings for pacing, and an enhanced review screen that tracks unanswered questions and flags questions that took too long to answer.

**Key Features & Enhancements:**

1.  **Performance Analytics Engine:**
    *   **Confidence Score:** A new metric calculated for each question based on a combination of correctness and the time taken to answer relative to the exam's average. Fast, correct answers receive a high score, while slow or incorrect answers receive low or negative scores. The final result is presented as an overall percentage.
    *   **Time Tracking:** The application now records the time spent on each question individually.
    *   **Unanswered Question Tracking:** The system now explicitly tracks and reports questions that were skipped or never answered.

2.  **Enhanced Exam Experience:**
    *   **Optional Time Warnings:** Users can now select a checkbox during setup to receive a subtle visual warning (a "breathing" red timer) if they are spending more time on the current question than the calculated average.

3.  **Upgraded Review Screen:**
    *   **Review Unanswered Questions:** A new link on the results screen allows users to specifically review all questions they did not answer.
    *   **Performance Icons:** The review list is now enhanced with icons to provide immediate visual feedback:
        *   An **'x' icon (❌)** is displayed next to any unanswered question.
        *   A **clock icon (🕰️)** is displayed next to any answered question (whether correct or incorrect) where the time taken was significantly longer than the average, helping users identify knowledge gaps or areas of hesitation.

**Testing Notes for Version 1.8.4:**

*   **Confidence Score:** Verify the score appears on the results screen and seems reasonable (e.g., answering quickly and correctly results in a high score).
*   **Time Warnings:** Enable the "Show time warning" checkbox during setup. During the exam, wait on a question for longer than the average time and confirm the timer begins to pulse.
*   **Unanswered Questions:** Complete an exam while skipping several questions. Verify the "Unanswered" count on the results screen is correct and that the "Review Unanswered" link works.
*   **Review Screen Icons:**
    *   Confirm the 'x' icon appears for all unanswered questions in the review list.
    *   Answer some questions very slowly. Confirm the clock icon appears next to them in the review list (for both correct and incorrect answers).

---

## Version 1.7.0

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
