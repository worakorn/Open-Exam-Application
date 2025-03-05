# Exam JSON Schema and Explanation

This document describes the structure and purpose of the provided JSON data, which represents an exam configuration and its questions.

## Overview

The JSON object contains information about an exam, including its name, number of questions, default time, instructions, domain percentages, and the questions themselves. It's designed to be a flexible and extensible format for defining exams.

## JSON Structure

```json
{
    "Exam Name": "My Custom Exam",
    "Number of Questions": 5,
    "Default Time": 5,
    "Instructions": "These are custom instructions for this specific exam bank.  Read them carefully!",
    "DomainPercentages": {
        "JavaScript Basics": 60,
        "DOM Manipulation": 40
    },
    "Questions": [
        {
            "DomainOfKnowledge": "JavaScript Basics",
            "Question": "What is the output of console.log(2 + '2');",
            "Choices": ["22", "4", "0", "Error"],
            "AnswerKey": "22",
            "Explaination": "2 + '2' use string then it equals 22."
        },
        // ... more questions ...
    ]
}
```

## Key Fields

* **`Exam Name`**: (String) The name of the exam.
* **`Number of Questions`**: (Integer) The total number of questions in the exam.
* **`Default Time`**: (Integer) The default time allowed for each question, in minutes.
* **`Instructions`**: (String) Specific instructions for the exam.
* **`DomainPercentages`**: (Object) An object representing the percentage distribution of questions across different domains of knowledge.
    * Keys: Domain names (e.g., "JavaScript Basics", "DOM Manipulation").
    * Values: Percentage of questions belonging to that domain (Integer).
* **`Questions`**: (Array) An array of question objects. Each question object has the following structure:
    * **`DomainOfKnowledge`**: (String) The domain of knowledge the question belongs to.
    * **`Question`**: (String) The text of the question.
    * **`Choices`**: (Array of Strings) An array of possible answer choices.
    * **`AnswerKey`**: (String) The correct answer.
    * **`Explaination`**: (String) An explanation of the correct answer.

## Example Question Object

```json
{
    "DomainOfKnowledge": "JavaScript Basics",
    "Question": "What is the output of console.log(2 + '2');",
    "Choices": ["22", "4", "0", "Error"],
    "AnswerKey": "22",
    "Explaination": "2 + '2' use string then it equals 22."
}
```

## Usage

This JSON structure can be used for:

* Dynamically generating exams in web applications.
* Storing and retrieving exam data in a structured format.
* Analyzing exam question distribution and performance.
* Importing and exporting exam data between different systems.

## Notes

* The `DomainPercentages` object is designed to provide a high-level overview of the exam's content distribution.
* The example json provided contains extra questions that are not accounted for in the "Number of Questions" field.
* The example JSON contains questions from "HTML Basics" domain, which is not accounted for in the DomainPercentages object.

This README provides a clear understanding of the JSON data structure and its intended use.

### Disclaimer

All of contents are AI Generated for educational purpose.
