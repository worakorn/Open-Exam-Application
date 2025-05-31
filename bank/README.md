```markdown
# Open Exam Application - Exam JSON Schema

This document outlines the JSON structure used by the "Open Exam Application" to define and load exams.

## Overview

The JSON format allows for a comprehensive definition of an exam, including its metadata (name, instructions), question selection parameters (number of questions, domain distribution), timing, and the actual question bank. This structure is designed for flexibility and offline use within the single HTML application.

## JSON Structure

```json
{
    "Exam Name": "Comprehensive Web Development Exam",
    "Number of Questions": 10,
    "Default Time": 15, // Total exam time in minutes for the default setup
    "Instructions": "Welcome to the exam! Please read each question carefully. Good luck!",
    "BackNavigation": true, // Optional: true (default) or false. If false, the 'Back' button is disabled during the exam.
    "DomainPercentages": { // Optional: Defines how questions should be drawn from different domains
        "JavaScript Basics": 50, // 50% of the "Number of Questions" should come from this domain
        "DOM Manipulation": 30,
        "HTML Basics": 20
    },
    "Questions": [
        {
            "DomainOfKnowledge": "JavaScript Basics",
            "Question": "What is the output of `console.log(2 + '2');`?",
            "Choices": ["22", "4", "NaN", "Error"],
            "AnswerKey": "22",
            "Explaination": "In JavaScript, when the `+` operator is used with a number and a string, it performs string concatenation. Thus, `2` is converted to `'2'`, and `'2' + '2'` results in `'22'`."
        },
        {
            "DomainOfKnowledge": "DOM Manipulation",
            "Question": "Which method is used to select an HTML element by its ID?",
            "Choices": ["getElementByClassName", "querySelector", "getElementById", "selectById"],
            "AnswerKey": "getElementById",
            "Explaination": "`document.getElementById('elementId')` is the standard JavaScript method for selecting an element by its unique ID."
        },
        {
            "DomainOfKnowledge": "HTML Basics",
            "Question": "What does HTML stand for?",
            "Choices": ["Hyper Trainer Marking Language", "Hyper Text Marketing Language", "Hyper Text Markup Language", "Hyperlink and Text Markup Language"],
            "AnswerKey": "Hyper Text Markup Language",
            "Explaination": "HTML stands for Hyper Text Markup Language, which is the standard markup language for creating web pages."
        }
        // ... more questions as needed ...
    ]
}
```

## Key Fields Explained

*   **`Exam Name`**: (String, Required)
    The display name of the exam.
*   **`Number of Questions`**: (Integer, Required)
    The target number of questions to be presented to the user if "default settings" are chosen in the application. The actual number might be less if the question bank is smaller or if domain percentage calculations result in fewer questions.
*   **`Default Time`**: (Integer, Required)
    The default total time limit for the exam in minutes when "default settings" are chosen. If set to `0`, the exam will have no time limit by default.
*   **`Instructions`**: (String, Optional)
    Custom instructions for this specific exam bank. If provided, these will be displayed to the user before starting the exam. Can include HTML for formatting.
*   **`BackNavigation`**: (Boolean, Optional)
    *   If set to `false`, the "Back" button will be disabled during the exam, preventing users from returning to previously answered questions.
    *   If set to `true` or if the field is omitted, back navigation is allowed (default behavior).
*   **`DomainPercentages`**: (Object, Optional)
    *   An object where keys are strings representing the "DomainOfKnowledge" and values are integers (0-100) representing the desired percentage of questions from that domain.
    *   The sum of percentages should ideally be 100. If less, the remaining questions (to reach "Number of Questions") will be filled randomly. If more than 100, it's an invalid configuration.
    *   If this field is omitted, questions will be selected randomly from the entire "Questions" array up to the "Number of Questions" limit.
    *   The application attempts to honor these percentages but is limited by the number of available questions in each domain and the total "Number of Questions".
*   **`Questions`**: (Array of Objects, Required)
    An array containing the individual question objects. Each question object has the following structure:
    *   **`DomainOfKnowledge`**: (String, Required)
        The category or topic the question belongs to. This is used for domain percentage calculations and results display.
    *   **`Question`**: (String, Required)
        The actual text of the question.
    *   **`Choices`**: (Array of Strings, Required)
        An array of possible answer choices for the question. Must contain at least two choices.
    *   **`AnswerKey`**: (String, Required)
        The correct answer. This string *must exactly match* one of the strings in the `Choices` array.
    *   **`Explaination`**: (String, Required)
        An explanation for why the `AnswerKey` is correct. This is shown during the review.

## Application Behavior Notes

*   **Question Selection:**
    *   If `DomainPercentages` are provided, the application tries to select questions according to these percentages from the available bank.
    *   If the number of questions available in a domain is less than what its percentage dictates, the application will take all available questions from that domain and attempt to fill the deficit from other domains or randomly.
    *   The final number of questions in an exam session is determined by the "Number of Questions" setting in the JSON (for default setup) or the user's custom selection, but is always capped by the total number of unique questions available in the `Questions` array.
*   **User Customization:** The application allows users to override the "Number of Questions" and "Default Time" from the JSON file if they choose the "Customize" option before starting an exam.
*   **Old Format Compatibility:** The application is designed to be compatible with older JSON formats that might not include the `BackNavigation` or `DomainPercentages` fields. It will use default behaviors (back navigation enabled, random question selection) in such cases.

## Disclaimer

⚠️ **All code for the "Open Exam Application" and this accompanying JSON schema example were AI-generated.** This project is intended for educational and demonstrative purposes. Use with caution. Thoroughly review and test before relying on it for any critical application. Ensure your JSON data is correctly formatted according to this schema for optimal application performance.
```