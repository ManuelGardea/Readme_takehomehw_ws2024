# QuizApp Using Html Javascript and CSS

## 1. Problem Statement

The Quizapp is a web-based application designed to provide the users with an interactive learning experience. It provides users with a platfrom to test their knowledge accross various topics through a series of timed multiple-choice questions. Feautures include the ability to track user porgress and provide instant feedback. The user-friendly interface and engaging content make it an effective tool for both self-assessment and learning reinforcement for its users. The application is designed with the assumption that users have a basic foundational knowledge of HTML, CSS, and JavaScript.

## 2. Functional Features of the App

- Landing Page with Start Quiz Button
- Intructions/Rules that outlines how to use the web-application 
    - Two Options in the intrusction page, buttons options are Exit Quiz or Continue
- The Quiz
    - In the form of Multiple Choice
    - 4 Options to Choose from
    - The user has 15 seconds to answer the question
    - If time runs out before input answer is revealed
    - The timer is in the form of a countdown
    - Dynamic progress bar showing time elapsed
    - Once a user selects an answer the timer and progress bar will stop.
    - When option is true then it show a green bar with a checkmark on the correct option only.
    - When option is false then it shows the option will be on a red bar with an X icon and the correct answer will be in a green bar with a checkmark
- 5 questions total
    - Once all 5 questions are answered or time has elapsed then you are brought to a completion screen.
    - It will let user know how many questions they got correct
    - Two buttons are shown to the user
        - Replay quiz button will take user back to questions one and timer will start immediatly
        - Quit Quiz button will take user back to the landing page where they have the button Start Quiz.

# Directory Structure

The app's codebase is organized into several files and directories:

- `index.html`: The main HTML file that includes the basic structure of the app.
- `style.css`: Contains all the CSS rules for styling the app.
- `questions.js`: Stores all the questions for the quizzes.
- `quizApp.js`: Contains the main JavaScript code that powers the app's functionality.