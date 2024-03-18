# QuizApp Using Html Javascript and CSS

## Problem Statement

The Quizapp is a web-based application designed to provide the users with an interactive learning experience. It provides users with a platfrom to test their knowledge accross various topics through a series of timed multiple-choice questions. Feautures include the ability to track user porgress and provide instant feedback. The user-friendly interface and engaging content make it an effective tool for both self-assessment and learning reinforcement for its users. The application is designed with the assumption that users have a basic foundational knowledge of HTML, CSS, and JavaScript.

## Functional Features of the App

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

## Explanation of the Codebase

### 1. Index.html File 

1. Here in the Index file spefically in the head of the index file is where you link all of your files in this case we have style.css, questions.js and quizapp.js

```html
    <!-- CSS FILE -->
    <link rel="stylesheet" href="css/style.css">
    <!-- This is my personal font awesome kit code. you will have to add your own after you register with email-->
    <script src="https://kit.fontawesome.com/4a4f4b55b0.js" crossorigin="anonymous"></script>

     <!-- Add questions list -->
    <script src="js/questions.js" defer></script>

    <!-- Main logic of the app -->
    <script src="js/quizApp.js" defer></script>
```

2. Next we have the start button in the body of the html document. As well as a div that holds all the instructions with their specfic class names and here we also have the two buttons on the instruction page "start quiz" or "Exit"

```html
    <!-- Instruction box wrapper -->
    <div class="info_box">
        <div class="info-title"><span>Some Rules of this Quiz</span></div>
        <div class="info-list">
            <div class="info">1. You will have only <span>15 seconds</span> per each question.</div>
            <div class="info">2. Once you select your answer, it can't be undone.</div>
            <div class="info">3. You can't select any option once time goes off.</div>
            <div class="info">4. You can't exit from the Quiz while you're playing.</div>
            <div class="info">5. You'll get points on the basis of your correct answers.</div>
        </div>
        <div class="buttons">
            <button class="quit">Exit Quiz</button>
            <button class="restart">Continue</button>
        </div>
    </div>
```
3. - `quiz_box`  This is the main container for the quiz. It contains all other elements related to the quiz.
   - `section` This is where the questions and answer options are displayed. The que_text div will contain the question text, and the option_list div will contain the answer options.
   - `footer` Section contains a counter that shows the total number of questions in the quiz, and a “Next Question” button to proceed to the next question.
   - `result_box` This is displayed after the quiz is completed. It contains a message indicating that the quiz is complete, the user’s score, and buttons to either replay the quiz or quit.
   
```html
    <!-- Quiz Box -->
    <div class="quiz_box">
        <header>
            <div class="title">Demo Quiz App in JavaScript</div>
            <div class="timer">
                <div class="time_left_txt">Time Left</div>
                <div class="timer_sec">15</div>
            </div>
            <div class="time_line"></div>
        </header>
        <section>
            <div class="que_text">
                <!-- Insert questions from ./js/questions.js -->
            </div>
            <div class="option_list">
                <!-- Insert options to questions from ./js/questions.js -->
            </div>
        </section>

        <!-- footer of Quiz Box -->
        <footer>
            <div class="total_que">
                <!-- insert Question Count Number dynamically from JavaScript App logic -->
            </div>
            <button class="next_btn">Next Que</button>
        </footer>
    </div>

    <!-- Result Box -->
    <div class="result_box">
        <div class="icon">
            <i class="fas fa-crown"></i>
        </div>
        <div class="complete_text">You've completed the Quiz!</div>
        <div class="score_text">
            <!-- insert dynamic user score as Result from JavaScript -->
        </div>
        <div class="buttons">
            <button class="restart">Replay Quiz</button>
            <button class="quit">Quit Quiz</button>
        </div>
    </div>
```
### Style.css file

The style.css file contains the styling rules for the HTML elements in the Quiz App. Here are the key aspects of the styling:

1. Import fonts to use throughout the entire interface.

```scss
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap");
```

2. Reset CSS and Global styles. Here the * selector applies reset styles to all elements, removing default margins and padding and ensures box- sizing consistency 

```scss
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}
```
3. Button styles define the appearance of buttons throughout the application. It sets the font size, weight , color, padding, border radius and background color. Below is some of the buttons style used

```scss
.start_btn button {
  font-size: 25px;
  font-weight: 500;
  color: #a020f0;
  padding: 15px 30px;
  outline: none;
  border: none;
  border-radius: 5px;
  background: #fff;
  cursor: pointer;
}

.info_box .buttons {
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  padding: 0 30px;
  border-top: 1px solid lightgrey;
}

footer button {
  height: 40px;
  padding: 0 13px;
  font-size: 18px;
  font-weight: 400;
  cursor: pointer;
  border: none;
  outline: none;
  color: #fff;
  border-radius: 5px;
  background: #a020f0;
  border: 1px solid #a020f0;
  line-height: 10px;
  opacity: 0;
  pointer-events: none;
  transform: scale(0.95);
  transition: all 0.3s ease;
}
```
4. The provided styling enables active information to overlay other elements and conceal them upon activation.

   - An opacity of 1 renders the background completely opaque.
   - A z-index of 5 prioritizes the element, placing it atop the stack due to its highest index among all elements.
   - Setting pointer-events to auto allows the cursor to function as if no pointer-event was specified, adhering to default browser settings.
   - Scaling the element to 1 maintains its size as specified elsewhere in the CSS code, while transform centers the element on the page.

```scss
.info_box.activeInfo,
.quiz_box.activeQuiz,
.result_box.activeResult {
  opacity: 1;
  z-index: 5;
  pointer-events: auto;
  transform: translate(-50%, -50%) scale(1);
}
```

5. For the instruction, quiz, and results containers, their dimensions, background color, corner roundness, and opacity are specified. By setting the opacity to 0, they remain invisible until activated. A transition effect is applied to ensure seamless navigation between pages.

```scss
.info_box {
  width: 540px;
  background: #fff;
  border-radius: 5px;
  transform: translate(-50%, -50%) scale(0.9);
  opacity: 0;
  pointer-events: none;
  transition: all 0.3s ease;
}

.quiz_box {
  width: 550px;
  background: #fff;
  border-radius: 5px;
  transform: translate(-50%, -50%) scale(0.9);
  opacity: 0;
  pointer-events: none;
  transition: all 0.3s ease;
}

.result_box {
  background: #fff;
  border-radius: 5px;
  display: flex;
  padding: 25px 30px;
  width: 450px;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  transform: translate(-50%, -50%) scale(0.9);
  opacity: 0;
  pointer-events: none;
  transition: all 0.3s ease;
}
```
### Questions.js file

This repository contains the code for a Quiz App developed in JavaScript.

1. In the code, an array named questions is created to hold information about each quiz question. Each object within this array represents a single question and includes the following properties:

```javascript
let questions = [
  {
    numb: 1,
    question: "What does HTML stand for?",
    answer: "Hyper Text Markup Language",
    options: [
      "Hyper Text Preprocessor",
      "Hyper Text Markup Language",
      "Hyper Text Multiple Language",
      "Hyper Tool Multi Language",
    ],
  },
  {
    numb: 2,
    question: "What does CSS stand for?",
    answer: "Cascading Style Sheet",
    options: [
      "Common Style Sheet",
      "Colorful Style Sheet",
      "Computer Style Sheet",
      "Cascading Style Sheet",
    ],
  },
  {
    numb: 3,
    question: "What does PHP stand for?",
    answer: "Hypertext Preprocessor",
    options: [
      "Hypertext Preprocessor",
      "Hypertext Programming",
      "Hypertext Preprogramming",
      "Hometext Preprocessor",
    ],
  },
  {
    numb: 4,
    question: "What does SQL stand for?",
    answer: "Structured Query Language",
    options: [
      "Stylish Question Language",
      "Stylesheet Query Language",
      "Statement Question Language",
      "Structured Query Language",
    ],
  },
  {
    numb: 5,
    question: "What does XML stand for?",
    answer: "eXtensible Markup Language",
    options: [
      "eXtensible Markup Language",
      "eXecutable Multiple Language",
      "eXTra Multi-Program Language",
      "eXamine Multiple Language",
    ],
  },
```
`numb`: Represents the question number.
`question`: Holds the actual question text.
`answer`: Stores the correct answer to the question.
`options`: Contains an array of multiple-choice options for the question.

### Quizapp.js

The JavaScript code manages the functionality of the quiz app, including user interactions, question handling, timer control, and result display. 

1. The code begins by selecting various elements from the HTML document using document.querySelector() and related methods. 

- The querySelector() function accepts parameters in the same format as CSS selectors and retrieves the first matching element from the HTML document.

```javascript
const start_btn = document.querySelector(".start_btn button");
const info_box = document.querySelector(".info_box");
const exit_btn = info_box.querySelector(".buttons .quit");
const continue_btn = info_box.querySelector(".buttons .restart");
const quiz_box = document.querySelector(".quiz_box");
const result_box = document.querySelector(".result_box");
const restart_quiz = result_box.querySelector(".buttons .restart");
const quit_quiz = result_box.querySelector(".buttons .quit");
const option_list = document.querySelector(".option_list");
const time_line = document.querySelector("header .time_line");
const timeText = document.querySelector(".timer .time_left_txt");
const timeCount = document.querySelector(".timer .timer_sec");
const next_btn = document.querySelector("footer .next_btn");
const bottom_ques_counter = document.querySelector("footer .total_que");
```

2. Event listeners are added to various elements to handle user interactions such as clicking buttons to start, continue, or quit the quiz.

- "Start" After the user clicks on the `start_btn`, the `activeInfo` class is appended to the `info_box` element. Due to the CSS styling, the `info_box` becomes visible as its opacity transitions from 0 to 1 upon receiving the activeInfo class.

```javascript
// if startQuiz button clicked
start_btn.addEventListener("click", (e) => {
  info_box.classList.add("activeInfo"); //show info box
});
```

- "Continue" Upon clicking, the activeInfo class will be removed from the info_box, causing it to be hidden as its opacity is set to 0. Simultaneously, the activeQuiz class will be added to the quiz_box, rendering it visible.

```javascript
// if continueQuiz button clicked
continue_btn.addEventListener("click", (e) => {
  info_box.classList.remove("activeInfo"); //hide info box
  quiz_box.classList.add("activeQuiz"); //show quiz box
  showQuetions(0); //calling showQestions function
  queCounter(1); //passing 1 parameter to queCounter
  startTimer(15); //calling startTimer function
  startTimerLine(0); //calling startTimerLine function
});
```

- "Quit" Upon clicking the quit_quiz button, the current window undergoes a reload, returning the user to the home page where the start quiz button is located. Additionally, all variables revert to their default values.

```javascript
// if quitQuiz button clicked
quit_quiz.addEventListener("click", (e) => {
  window.location.reload(); //reload the current window
});
```

3. Next variables and functions are defined to manage quiz operations such as displaying questions, handling user answers, and controlling the timer.

- `timeValue`: Represents the initial time value for each question in seconds.
  `que_count`: Tracks the index of the current question being displayed.
  `que_numb`: Represents the number of the current question.
  `userScore`: Keeps track of the user's score throughout the quiz.
  `counter` and `counterLine`: These variables are used to store interval IDs for the timer and the progress bar.
  `widthValue`: Represents the initial width value for the progress bar.

```javascript
// Variables to control quiz operations
let timeValue = 15;
let que_count = 0;
let que_numb = 1;
let userScore = 0;
let counter;
let counterLine;
let widthValue = 0;
```

- icons are used in addition to colors to identify the correct and incorrect answers. New div tags are created to embed them in the HTML DOM.

```javascript
// create new div tags for right or wrong tick icons
let tickIconTag = '<div class="icon tick"><i class="fas fa-check"></i></div>';
let crossIconTag = '<div class="icon cross"><i class="fas fa-times"></i></div>';
```

- Stops and clears timer and progress bar counters when an option is selected.
- Retrieves user's selected answer, correct answer, and counts available options.
- If user's answer is correct:
    - Increments user's score.
    - Adds green color and tick icon to the selected option.
- If user's answer is incorrect:
    - Adds red color and cross icon to the selected option.
    - Automatically highlights the correct answer.
- Disables all options to prevent further selection.
- Displays the "Next" button for the user to proceed.

```javascript
//if user clicked on option
function optionSelected(answer) {
  clearInterval(counter); //clear counter
  clearInterval(counterLine); //clear counterLine
  let userAns = answer.textContent; //getting user selected option
  let correcAns = questions[que_count].answer; //getting correct answer from array
  const allOptions = option_list.children.length; //getting all option items

  //if user selected option is equal to array's correct answer
  if (userAns == correcAns) {
    userScore += 1; //update total score value increment by 1
    answer.classList.add("correct"); //add green color to correct selected option
    answer.insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to correct selected option
    console.log("Correct Answer");
    console.log("Your correct answers = " + userScore);
  } else {
    answer.classList.add("incorrect"); //add red color to correct selected option
    answer.insertAdjacentHTML("beforeend", crossIconTag); //add cross icon to correct selected option
    console.log("Wrong Answer");

    for (i = 0; i < allOptions; i++) {
      if (option_list.children[i].textContent == correcAns) {
        //if there is an option which is matched to an array answer
        option_list.children[i].setAttribute("class", "option correct"); //add green color to matched option
        option_list.children[i].insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to matched option
        console.log("Auto selected correct answer.");
      }
    }
  }
  for (i = 0; i < allOptions; i++) {
    option_list.children[i].classList.add("disabled"); //once user select an option, disable all options
  }
  next_btn.classList.add("show"); //show the next button if user selected any option
}
```
### That Concludes the Readme file