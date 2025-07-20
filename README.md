# Open Exam Application (v1.6.0)

## Introduction

The "Open Exam Application" is a standalone, offline-capable exam system built entirely within a single HTML file using vanilla HTML, CSS, and JavaScript. It provides a highly flexible platform for creating and taking multiple-choice exams, with features like timed tests, advanced user-driven exam configuration, and immediate, detailed results.

**This application, including this documentation, is primarily AI-generated and intended for educational and demonstrative purposes. Use with caution.**

## Features

*   **Single File Portability:** The entire application runs from a single `exam.html` file, making it highly portable and suitable for offline use on any modern web browser.
*   **Custom Exam Banks (JSON):**
    *   Load external exam question banks from a local JSON file.
    *   Load exam banks from a publicly accessible URL hosting a JSON file.
    *   Supports a defined [JSON schema](./bank/README.md) for creating custom exams, including domain-specific questions, answer explanations, and configurable exam parameters.
*   **Advanced Exam Setup:**
    *   **Default Settings Mode:** Uses the settings from the JSON file. It intelligently applies `DomainPercentages` only if the question count is sufficient, otherwise falling back to random selection.
    *   **Quick Start Mode:** Allows users to start an exam quickly with a specific number of questions chosen randomly from the entire question bank.
    *   **Custom Selection Mode:** Empowers users to build their own exam by:
        *   Selecting one or more specific topics (Domains of Knowledge) from an alphabetically sorted list.
        *   Choosing the number of questions to be drawn randomly *only from the selected topics*.
*   **Modern Exam Experience:**
    *   Clean, responsive user interface that works on both **desktop and mobile devices**.
    *   Multiple-choice questions presented one at a time.
    *   Optional, user-configurable timer with automatic submission when time expires.
    *   Navigation (Next/Back buttons), with an option in the JSON (`"BackNavigation": false`) to disable the "Back" button for a more restrictive exam.
    *   Progress bar indicating the user's current position in the exam (e.g., Question 5 / 20).
*   **Immediate Results & Enhanced Review:**
    *   Instant scoring upon submission, including overall percentage and average time per question.
    *   Results are broken down by knowledge domain and **sorted by performance (best to worst)** to provide clear insights.
    *   Option to review correctly and incorrectly answered questions, showing the user's answer, the correct answer, and the explanation.
*   **Demo Mode:** Includes a built-in demo exam for quick testing and demonstration of all features.

## How to Use

1.  **Download:** Get the `exam.html` file.
2.  **Open:** Open `exam.html` in a modern web browser (like Chrome, Firefox, Edge, or Safari).
3.  **Load an Exam:**
    *   **From URL:** Enter the URL of a JSON exam file and click "Load from URL".
    *   **From Local File:** Click "Browse File", select your local JSON exam file. The exam will load automatically.
    *   **Run Demo:** Click "Run Demo Exam" to use the built-in sample questions.
4.  **Configure Your Exam:** Once an exam bank is loaded, choose your preferred setup:
    *   **Default Settings:** The simplest option, using the configuration from the exam file.
    *   **Quick Start:** Select for a random assortment of questions.
    *   **Custom Selection:** Check the boxes for the topics you want to be tested on.
    *   For Quick Start and Custom modes, you can also specify the number of questions and the time limit.
5.  **Start Exam:** Click the "Start Exam" button.
6.  **Take Exam:** Answer the questions. Use the navigation buttons as needed.
7.  **View Results:** After submitting, your results will be displayed instantly, with your performance by topic sorted from best to worst.
8.  **Review:** Click on the review links to see details for your correct and incorrect answers.

## Exam JSON Format

For instructions on creating your own exam bank files, please refer to the **[bank/README.md](./bank/README.md)** file for the detailed JSON schema and field explanations.

## Download

*   The latest stable version can always be found as `exam.html` in the root of the project repository.

## ⚠️ Disclaimer & AI-Generated Content Notice

**Please be fully aware that this "Open Exam Application," its features, and all accompanying documentation (including this README) have been primarily generated with the assistance of Artificial Intelligence (AI).**

*   **No Guarantees:** While efforts are made during the AI generation process to produce functional and accurate code, there are no guarantees of perfect functionality, security, or absence of bugs.
*   **Educational Purpose:** This project is intended primarily for educational and demonstrative purposes to showcase what can be built with AI assistance.
*   **Use With Caution:** Exercise discretion when using this application, especially if considering it for any sensitive or critical purpose.
*   **Verify and Test:** If you intend to use or modify this application, thorough review, testing, and validation of the code are strongly recommended.
*   **AI Limitations:** AI-generated code may sometimes be overly complex, not follow all best practices, or have subtle logical flaws.

**By using this software, you acknowledge and accept these disclaimers.**
