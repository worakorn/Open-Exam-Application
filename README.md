# Open Exam Application (v1.0.0)

## Introduction

The "Open Exam Application" is a standalone, offline-capable exam system built entirely within a single HTML file using HTML, CSS, and JavaScript. It allows users to take multiple-choice exams, with features like timed tests, customizable question banks, and immediate results.

**This application, including this documentation, is primarily AI-generated and intended for educational and demonstrative purposes. Use with caution.**

## Features

*   **Single File Portability:** The entire application, including default exam data, can run from a single `exam.html` file, making it highly portable and suitable for offline use.
*   **Custom Exam Banks (JSON):**
    *   Load external exam question banks from a local JSON file.
    *   Load exam banks from a publicly accessible URL hosting a JSON file.
    *   Supports a defined [JSON schema](SCHEMA.md) for creating custom exams, including domain-specific questions, answer explanations, and configurable exam parameters.
*   **Flexible Exam Setup:**
    *   Use default settings (number of questions, time limit) defined within the loaded JSON exam bank.
    *   Allow test-takers to customize the number of questions for their exam session (from predefined options or a custom value, capped by bank size).
    *   Allow test-takers to set a custom time limit for the exam, or run an untimed exam.
*   **Exam Experience:**
    *   Multiple-choice questions presented one at a time.
    *   Optional timer with automatic submission when time expires.
    *   Navigation (Next/Back buttons), with an option in the JSON to disable the "Back" button for a more restrictive exam experience.
    *   Progress bar indicating the current question relative to the total.
*   **Immediate Results & Review:**
    *   Instant scoring upon submission.
    *   Display of correct answers, incorrect answers, and overall percentage.
    *   Results broken down by knowledge domain.
    *   Average time spent per question.
    *   Option to review correctly and incorrectly answered questions, showing the user's answer, the correct answer, and the explanation.
*   **Demo Mode:** Includes a built-in demo exam for quick testing and demonstration of features if no external exam bank is loaded.
*   **Open & Understandable:** The code is plain HTML, CSS, and JavaScript, making it relatively easy to inspect and understand (though AI-generated).

## How to Use

1.  **Download:** Get the `exam.html` file.
2.  **Open:** Open `exam.html` in a modern web browser.
3.  **Load Exam (Optional):**
    *   **From URL:** Enter the URL of a JSON exam file and click "Load from URL".
    *   **From Local File:** Click "Browse File", select your local JSON exam file. The exam will load automatically.
    *   **Run Demo:** Click "Run Demo Exam" to use the built-in sample questions.
4.  **Configure Exam:** Once an exam bank is loaded:
    *   Choose to use the default settings from the exam file.
    *   Or, customize the number of questions and set a specific time limit.
5.  **Start Exam:** Click the "Start Exam" button.
6.  **Take Exam:** Answer the questions. Use navigation buttons as needed.
7.  **View Results:** After submitting or when time runs out, your results will be displayed.
8.  **Review:** Click on the review links to see details for correct/incorrect answers.

## Exam JSON Format

For creating your own exam banks, please refer to the [SCHEMA.md](SCHEMA.md) file for the detailed JSON structure and field explanations.

## Download

*   The latest stable version can be found as `exam.html` in the project repository. (Future: Link to releases page if applicable).

## ⚠️ Disclaimer & AI-Generated Content Notice

**Please be fully aware that this "Open Exam Application," its features, and all accompanying documentation (including this README) have been primarily generated with the assistance of Artificial Intelligence (AI).**

*   **No Guarantees:** While efforts are made during the AI generation process to produce functional and accurate code, there are no guarantees of perfect functionality, security, or absence of bugs.
*   **Educational Purpose:** This project is intended primarily for educational and demonstrative purposes to showcase what can be built with AI assistance.
*   **Use With Caution:** Exercise discretion when using this application, especially if considering it for any sensitive or critical purpose.
*   **Verify and Test:** If you intend to use or modify this application, thorough review, testing, and validation of the code are strongly recommended.
*   **AI Limitations:** AI-generated code may sometimes be overly complex, not follow all best practices, or have subtle logical flaws.

**By using this software, you acknowledge and accept these disclaimers.**