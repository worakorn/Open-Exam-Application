# Open Exam Application - Changelog

This document tracks the significant changes, features, and improvements made to the "Open Exam Application."

## Version 1.0.0 (Current Release)

**Date:** [Enter Date of This Release]

**Summary:** This major update introduces robust exam configuration options, allowing users to tailor their exam experience by selecting the number of questions and setting custom time limits. It also enhances the user interface for loading exams, improves progress tracking, and introduces a versioning system. Compatibility with a new JSON field (`BackNavigation`) for controlling exam flow has been added.

**Key Features & Enhancements:**

1.  **Flexible Exam Setup Options:**
    *   **Description:** After loading an exam bank (or the demo), users are presented with options to configure their exam session.
    *   **Implementation:**
        *   A new UI section (`#exam-setup-options`) appears post-load.
        *   Users can choose between:
            *   "Use default settings from exam file" (number of questions and time limit from JSON).
            *   "Customize number of questions":
                *   Select from predefined counts (5, 10, 20, 50, 100) or enter a custom number.
                *   The number of questions is capped by the available questions in the loaded bank.
                *   This option is disabled if the bank has fewer than a minimum threshold (e.g., 5 questions).
        *   Users can set a custom "Time Limit (minutes)" for the exam, with 0 indicating an unlimited duration. This input is pre-filled based on the chosen setup (JSON default or calculated for custom question counts).
    *   **Files:** `exam.html` (HTML structure for options, JavaScript for handling logic in `onExamDataLoaded`, `handleSetupTypeChange`, `handleCustomCountChange`, `handleExamDurationChange`, `updateCurrentExamSetup`).

2.  **Improved File Input UI & Experience:**
    *   **Description:** The native browser "Choose File" button has been replaced with a custom-styled "Browse File" button for a more consistent and prominent appearance, similar to the "Load from URL" button. The name of the selected file is now displayed.
    *   **Implementation:**
        *   The actual `<input type="file">` is hidden.
        *   A styled `<button id="browse-file-button">` proxies clicks to the hidden input.
        *   A `<span>` displays the selected file's name.
        *   Visual separation added between URL and file loading sections.
    *   **Files:** `exam.html` (HTML, CSS, and JavaScript updates).

3.  **Progress Bar Based on Current Question Position:**
    *   **Description:** The progress bar now reflects the user's current position within the exam (e.g., "Question 5 / 20") rather than the number of answered questions.
    *   **Implementation:**
        *   The `updateProgress()` function now calculates progress based on `currentQuestionIndex` and the total number of questions in the current exam session (`randomizedExamData.length`).
    *   **Files:** `exam.html` (JavaScript update in `updateProgress()`).

4.  **`BackNavigation` Control via JSON:**
    *   **Description:** Exam creators can now disable the "Back" button during an exam by adding a `"BackNavigation": false` property to their exam JSON file.
    *   **Implementation:**
        *   The application checks for the `BackNavigation` field in the loaded `examData`.
        *   If `false`, the "Back" button in the question view is disabled and hidden throughout the exam.
        *   If `true` or omitted (for backward compatibility), the "Back" button functions normally (disabled only on the first question).
    *   **Files:** `exam.html` (JavaScript updates in `onExamDataLoaded()` and `showQuestion()`).

5.  **Application Version Display:**
    *   **Description:** The application now displays its version number at the bottom of the page.
    *   **Implementation:**
        *   A constant `APP_VERSION` (set to "1.0.0") is defined in the JavaScript.
        *   An HTML `div#version-info` is added and populated with the version on `DOMContentLoaded`.
    *   **Files:** `exam.html` (HTML and JavaScript).

**Previous Notable Features (Implied in base leading to this version):**

*   **Average Time per Question Calculation:**
    *   Tracks exam start time and calculates average time per question upon submission.
    *   Displayed in the results section.
*   **Enhanced Question Selection Logic:**
    *   Supports `Number of Questions` from JSON to determine exam length for default setup.
    *   Implements `DomainPercentages` for weighted question selection from different knowledge domains.
    *   Ensures questions are shuffled and not repeated within an exam session.
*   **Comprehensive JSON Validation:**
    *   `validateExamData()` checks for required fields, correct data types, valid answer keys within choices, and logical consistency in `DomainPercentages`.
*   **Improved Review Section:**
    *   Always shows correct answers and explanations during review.
    *   Groups reviewed questions by their "DomainOfKnowledge".
*   **Demo Mode:**
    *   Provides a built-in exam if no external file is loaded, accessible via a "Run Demo Exam" button.
*   **Core Functionality:**
    *   Loading exam data from local files or URLs.
    *   Presenting multiple-choice questions.
    *   Timed exams with auto-submission.
    *   Navigation (Next/Back).
    *   Immediate results (score, percentage, domain breakdown).

**Testing Notes for Version 1.0.0:**

*   Verify all exam setup options (default, custom question count, custom time limit) work correctly.
*   Test the disabling of custom question options when the bank size is below `MIN_QUESTIONS_FOR_CUSTOM_SETUP`.
*   Confirm the "Browse File" button functionality and selected file name display.
*   Ensure the progress bar accurately reflects the current question number.
*   Test the `BackNavigation: false` JSON setting to confirm the "Back" button is disabled/hidden.
*   Check that older JSON formats (without `BackNavigation` or `DomainPercentages`) load and function correctly.
*   Confirm the application version "1.0.0" is displayed.

**Disclaimer:**

⚠️ **This application and its changelog are primarily AI-generated. Use with caution and always test thoroughly.**