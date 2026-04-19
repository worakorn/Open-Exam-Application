*   # Open Exam Application

## Introduction

The "Open Exam Application" is a standalone, offline-capable exam system built entirely within a single HTML file. Crafted with vanilla HTML, CSS, and JavaScript—and significantly accelerated with Google Gemini—it provides a highly flexible platform for creating and taking multiple-choice exams. It features timed tests, advanced user-driven exam configuration, and immediate, detailed results with performance analytics.

There are currently two actively maintained versions of the application:
1. **`exam.html` (v1.9.1 - Stable):** The classic, standard exam application with robust fixed-length testing.
2. **`exam-next.html` (v2.0.0 - Cutting Edge):** The advanced application featuring a full Computerized Adaptive Testing (CAT) engine that dynamically scales difficulty based on real-time performance.

## Features

*   **Single File Portability:** The entire application runs from a single HTML file, making it highly portable and suitable for offline use on any modern web browser.
*   **Custom Exam Banks (JSON):**
    *   Load external exam question banks from a local JSON file.
    *   Load exam banks from a publicly accessible URL hosting a JSON file.
    *   Supports a defined [JSON schema](./bank/README.md) for creating custom exams, including domain-specific questions, answer explanations, and configurable exam parameters.
*   **Advanced Exam Setup:**
    *   **Default Settings Mode:** Uses the settings from the JSON file. It uses a highly accurate **proportional distribution algorithm (Largest Remainder Method)** to follow the `DomainPercentages`.
    *   **Quick Start Mode:** Allows users to start an exam quickly with a specific number of questions chosen randomly from the entire question bank.
    *   **Custom Selection Mode:** Empowers users to build their own exam by:
        *   Selecting one or more specific topics (Domains of Knowledge).
        *   Choosing the number of questions to be drawn randomly *only from the selected topics*.
*   **Modern Exam Experience:**
    *   Clean, **responsive user interface** that works on both **desktop and mobile devices**.
    *   Optional, user-configurable timer with automatic submission when time expires.
    *   Navigation (Next/Back buttons), with an option in the JSON (`"BackNavigation": false`) to disable the "Back" button.
    *   Progress bar indicating the user's current position in the exam.
*   **Performance Analytics:**
    *   **Confidence Score:** A unique metric that scores your performance based on both the correctness of your answer and the time taken to respond. Faster, correct answers yield a higher score.
    *   **Time Warnings:** An optional feature that provides a visual indicator during the exam if you are spending longer than the average time on a single question.
*   **Computerized Adaptive Testing (CAT) Engine *(exam-next.html only)*:**
    *   Intelligently scales question difficulty up or down using a sliding window algorithm based on your real-time performance.
    *   Prioritizes under-represented topics to ensure balanced domain coverage.
    *   Stops the exam dynamically upon mastery (consecutive high-level passes) or when a passing score is statistically unachievable.
*   **Immediate Results & Enhanced Review:**
    *   Instant scoring upon submission, including correct, incorrect, and **unanswered** counts, overall percentage, and the new Confidence Score.
    *   Detailed CAT statistics including hardest level reached and efficiency grade.
    *   Results are broken down by knowledge domain and **sorted by performance** (best to worst) to provide clear insights.
    *   Option to review **correct, incorrect, and unanswered** questions.
    *   The review screen now includes icons to flag specific questions:
        *   A **clock icon (🕰️)** appears next to any answered question where the time taken was significantly above average.
        *   An **'x' icon (❌)** appears next to any question that was left unanswered.
*   **Authoring Tool:** Includes `exam-builder.html` to easily create properly formatted JSON banks.
*   **Developer Debug Mode:**
    *   A `DEBUG` flag is available in the script to output detailed logs to the developer console.
*   **Demo Mode:** Includes a built-in demo exam for quick testing and demonstration of all features.

## How to Use

1.  **Download:** Get the `exam.html` or `exam-next.html` file.
2.  **Open:** Open the file in a modern web browser (like Chrome, Firefox, Edge, or Safari).
3.  **Load an Exam:**
    *   **From URL:** Enter the URL of a JSON exam file and click "Load from URL".
    *   **From Local File:** Click "Browse File", select your local JSON exam file.
    *   **Run Demo:** Click "Run Demo Exam" to use the built-in sample questions.
4.  **Configure Your Exam:** Once an exam bank is loaded, choose your preferred setup (Default, Quick Start, or Custom Selection) and configure options like question count, time limit, and time warnings.
5.  **Start Exam:** Click the "Start Exam" button.
6.  **Take Exam:** Answer the questions. Use the navigation buttons as needed.
7.  **View Results:** After submitting, your results will be displayed instantly.
8.  **Review:** Click on the review links to see details for your correct, incorrect, and unanswered questions, complete with performance flags.

## Exam JSON Format

For instructions on creating your own exam bank files, please refer to the **[bank/README.md](./bank/README.md)** file for the detailed JSON schema and field explanations.

## Download

*   The latest stable version can always be found as `exam.html` in the root of the project repository.
*   To test the latest adaptive algorithms, download `exam-next.html`.

## ⚠️ Disclaimer & AI-Generated Content Notice

**This project was primarily generated with Google Gemini.**

While Gemini is a powerful tool for accelerating development, it's important to remember that AI-generated code is a starting point.
*   **No Guarantees:** There are no guarantees of perfect functionality, security, or absence of bugs.
*   **Educational Purpose:** This project is intended primarily for educational and demonstrative purposes.
*   **Verify and Test:** If you intend to use or modify this application, thorough review, testing, and validation of the code are strongly recommended.

**By using this software, you acknowledge and accept these disclaimers.**
