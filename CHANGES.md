## exam.html Changelog

**Version:** [Implied: From previous version to the current version provided]

**Summary:** This update introduces significant enhancements to the exam application, focusing on question management and performance tracking. The primary additions are: 1) Average time spent per question, and 2) Improved question selection logic to prevent duplicates and adhere to user-defined question numbers and domain percentages.

**Features Added:**

1.  **Average Time per Question:**
    *   **Description:** The application now calculates and displays the average time a user spends on each question during the exam.
    *   **Implementation:**
        *   A `startTime` variable is introduced to track when the exam begins.
        *   `Date.now()` is used to determine the elapsed time upon exam submission.
        *   The `averageTimeSpan` element in the results section displays the calculated average time.
        *   The average time in second will be shown after submitting.
    *   **File:** `exam.html`
        *   Added: `<p>Average Time per Question: <span id="average-time"></span></p>` within `#results-container`
        *   Added: `let startTime;` global variable
        *   Added:  `const endTime = Date.now();`, and `elapsedTimeInSeconds` to `submitExam` function.
        * Added: code for calculate average time per question and update to element
            ```js
                 // Calculate elapsed time
                const endTime = Date.now();
                const elapsedTimeInSeconds = (endTime - startTime) / 1000;
                const numQuestionsAnswered = Object.keys(userAnswers).length; // Use this for average
                const averageTimePerQuestion = numQuestionsAnswered > 0
                    ? (elapsedTimeInSeconds / numQuestionsAnswered).toFixed(2)
                    : 0;

                averageTimeSpan.innerText = `${averageTimePerQuestion} seconds`;
            ```

2.  **Enhanced Question Selection:**
    *   **Description:** The system now supports selecting a specific number of questions from a larger question bank, preventing duplicates and optionally allocating question counts based on domain percentages.
    *   **Implementation:**
        *   The `prepareExamQuestions()` function has been added and significantly reworked to:
            *   Take the "Number of Questions" property from the exam data.
            *   Support "DomainPercentages" within the exam data to specify the proportion of questions from each domain.
            *   If "DomainPercentages" are defined, the function allocates questions per domain proportionally and randomly.
            * If not defined, questions will be select randomly.
            *   Shuffle the selected questions to ensure randomness.
        *   The `validateExamData()` function now validates "Number of Questions", "DomainPercentages"
        *   The `questionCountMessage` displays the number of question in the exam bank and number of question for user.
        * The `shuffleArray` function is used to shuffle array.
    *   **File:** `exam.html`
        *   Added: `<p id="question-count-message"></p>` to `#instructions`
        *   Added: `let randomizedExamData = [];`
        * Added: `shuffleArray(array)` function
         ```js
         function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
        }
        ```
        *   Added `prepareExamQuestions()` function for selecting specific number of question from json file.
         ```js
          function prepareExamQuestions(data) {
             const numQuestionsToSelect = data["Number of Questions"];
            // ...
        }
         ```
        * Updated `startExam` function to call `prepareExamQuestions` function.
            ```js
               // Prepare the questions (randomize and select based on percentages)
               randomizedExamData = prepareExamQuestions(examData);
            ```
        * Modified `validateExamData()` function to validate `Number of Question` and `DomainPercentages` in data.
        ```js
         function validateExamData(data) {
            //...
           if (typeof data["Number of Questions"] !== 'number' || data["Number of Questions"] <= 0) {
              alert("Error: 'Number of Questions' must be a positive number.");
              return false;
            }
           //...
        }
        ```
        * updated `onExamDataLoaded()` to show `questionCountMessage`.
            ```js
            function onExamDataLoaded() {
              //...
              // Display the number of questions in the exam bank
             const numQuestionsInBank = examData.Questions.length;
             questionCountMessage.innerText = `This exam will have ${examData["Number of Questions"]} questions out of ${numQuestionsInBank} questions in the bank.`;
             }
            ```
3. **Progress Bar**
    * Description: add progress bar to show progress
    * Implementation
        * create `#progress-bar-container` , `#progress-bar` and `#progress-text` element in html
        * create `updateProgress` function to update progress text and bar.
        * add `updateProgress` call to `startExam`, `showQuestion`, `saveAnswer`
    * File: exam.html
        * Added: `<div id="progress-bar-container">` and `<p id="progress-text"></p>` element in `instructions`
        * Added: `updateProgress` function
        ```js
            function updateProgress() {
                const totalQuestions = randomizedExamData.length;
                const answeredQuestions = Object.keys(userAnswers).length; // Count answered questions
                const progressPercentage = (answeredQuestions / totalQuestions) * 100;

                progressBar.style.width = `${progressPercentage}%`;
                progressText.innerText = `${answeredQuestions} / ${totalQuestions} Questions Answered`;
            }
        ```

**Other Improvements and Fixes:**

1. **Code Refactoring**
    * improve code to make it more readable.
2. **Demo Mode Message:**
    *   **Description:** When the application runs in "demo mode" (using the default data), a message is now displayed to the user indicating this state.
    *   **Implementation:**
        *   Added: `alert("Running in demo mode with default exam data.");` to the `startExam()` function.
3. **Validation:**
    *   **Description:** The `validateExamData()` function has been significantly enhanced to check for required fields, data types, minimum choice number and other potential errors in the exam data. Error messages are more specific and informative.
        *   Check Answer Key in Choice
        *   Check default time is number
4. **Review Improvement**
    * Modify `reviewQuestionsByDomain()` to always show answer.
    * Group question in `reviewQuestionByDomain()` by domain.

**Testing Notes:**

*   Thoroughly test the new "Average Time per Question" feature to ensure accurate calculations.
*   Test the different question selection scenarios:
    *   Without "DomainPercentages" defined.
    *   With "DomainPercentages" defined, covering various percentages and domain combinations.
    * Check edge case when no domain has remainders.
    * Ensure that the correct number of questions is selected in all cases.
* Test with a large question bank and with the demo data.

**Future Considerations:**

*   Add the ability to display time per question during exam.
*   Implement user login to store user results

