## Week 1 

.
1. Do finish up the HTML-CSS Lab if you have not done so during class. 
  * Full link for list of HTML-CSS challenges. https://github.com/lewagon/html-css-challenges
  * Visit https://github.com/lewagon/html-css-challenges/tree/master/01-profile-content for today's exercise. 

2. [(Bonus Homework) Track down the Terminal City Murderer](https://github.com/veltman/clmystery)
  * There's been a murder. Track down the murderer using just your command line. Download the Zip file from github to begin. Don't use the hints unless you absolutely have too!


3. (Optional) For some extra javascript practice. Please visit http://exercism.io/languages/javascript. 


### Day 2

1. Install atom-beautify plugin to your atom editor, for auto formatting your code files. 
  * Go to Atom > Preferences > Install
  * Search for the package atom-beautify -> click on install (This will take around 2 to 3 mins)
  * Test beautifying your HTML/CSS/Javascript code works with shortcut "Control + Alt + B"
  * You can also access this from the menu at Packages > Atom Beautify > Beautify
  
2. Complete HTML-CSS LAB Sections 2 and 3 (Compulsory)
 * https://github.com/lewagon/html-css-challenges/tree/master/02-fonts-colors
 * https://github.com/lewagon/html-css-challenges/tree/master/03-box-model  
3. Upload homework on Google drive(Compulsory)
  4. Upload instructions: 
    5. Accept email invitation
    6. Upload homework in homework submission folder 
    7. Look for your name. If it is not there, let either TAs know and create a folder with your name.
    8. Name the homework folder: Date-HTML-CSS
    9. Please create a new homework folder every day so that we will be able to view your progress  
    10. Please look at Angeline's folder to get a better idea of how to save and name the homework.
4. Finish playing all 26 levels of the CSS Bento game
 http://flukeout.github.io
5. Work on Code School's Discover Dev Tools Course https://www.codeschool.com/courses/discover-devtools 
 
 
### Day 3
1. Complete HTML-CSS LAB Sections 4, 5, 6 (Compulsory)
 * https://github.com/lewagon/html-css-challenges/tree/master/04-advanced-selectors
 * https://github.com/lewagon/html-css-challenges/tree/master/05-fixed-sidebar
 * https://github.com/lewagon/html-css-challenges/tree/master/06-profile-dashboard

2. Work on the javascript independent practice (Compulsory)
 * Take a look at this [starter-code](https://gist.github.com/Lnfra/2e78dd3da1ea37fc95e51f2f792c4a78) and work through each exercise using the comments provided to console log the correct information. 
 * You can use [Code Pen](http://codepen.io/) for testing your code 
 
3. Upload the above homework on Google drive in the homework submission folder under your name (Compulsory)

4. Complete the try git tutorial https://try.github.io

5. Work on the [Javascript Freecode Camp](http://www.freecodecamp.com/challenges/comment-your-javascript-code)
 * Register and signin
 * Click on Map menu > Basic Javascript Section 
 * Complete from "Comment your javascript code" till "stand in line" 

### Day 4

if (studentName !== "weiyang") {
1. Independent Function Practice (look below) 
2. Finish up Function Labs. Attempting the bonus functions is optional.
3. Finish up DOM Labs. Bonus section is always optional.
4. (Optional) Finish up html & css part for Tic Tac Toe game. Do not worry about the javascript files for now. (look below for details)
}

### Independent Practice - Write some functions (15 mins)

Work through as many as these exercises as you can within the next 15 mins - use the [starter-code](starter-code) provided!

1. Write a function `lengths` that accepts a single parameter as an argument, namely
an array of strings. The function should return an array of numbers where each
number is the length of the corresponding string.

```javascript
var words = ["hello", "what", "is", "up", "dude"]
lengths(words)  # => [5, 4, 2, 2, 4]
```

2. Write a Javascript function called `transmogrifier`. This function should accept three arguments, which you can assume will be numbers. Your function should return the "transmogrified" result.

The transmogrified result of three numbers is the product of the first two numbers, raised to the power of the third number.

For example, the transmogrified result of 5, 3, and 2 is `(5 times 3) to the power of 2` is 225. Use your function to find the following answers.

```
transmogrifier(5, 4, 3)
transmogrifier(13, 12, 5)
transmogrifier(42, 13, 7)
```

Write a function `wordReverse` that accepts a single argument, a string. The
method should return a string with the order of the words reversed. Don't worry
about punctuation.

```javascript
wordReverse("Now I know what a TV dinner feels like")
# => "like feels dinner TV a what know I Now"
wordReverse("Put Hans back on the line")
# => "line the on back Hans Put"
```
### Tic Tac Toe Javascript

#### Introduction

This week, we have been learning about writing functions, working with
loops, and writing conditionals. We also learned about how HTML elements are styled and behave in the DOM.

For this lab, you'll be building a tic tac toe game in HTML, CSS, and pure JavaScript.

#### Exercise

##### Requirements

- A user should be able to click on different squares to make a move
- Every click will alternate between marking an `X` and `O`
- Upon marking of an individual cell, use JavaScript to add a class to
  each cell to display separate colors
- A cell should not be able to be replayed once marked
- Add a reset button that will clear the contents of the board

---

- Since this is our first extended lab, here are some __tips/hints__ to get started:

 - Construct a `index.html` to be your starting point on this
 project. Add your necessary HTML tags, including `script` and
 `link` tags to link to your JavaScript and CSS, respectively.

 - Before you even start working with JavaScript, construct the
 game board. The game board page should include the 3x3 grid and at
 minimum, a reset button. Using `id` and `class` on clickable
 elements will help you wire this up in JavaScript afterwards.

 - JavaScript portion will be next:

   * Locate the element first to use it within your app. Think about
      using `document.getElementById`, `document.getElementsByClassName` or something similar to locate your target elements. Try this in your console to make sure your selection works.

   * After finding the elements, start writing logic to listen for
      `click` events on those elements

   * You will also need a variable to keep track of moves - this
      will be used to indicate whether or not to draw an `X` or an `O`.

**Bonus:**
- Display a message to indicate which turn is about to be played
- After the necessary moves have been played, stop the game and alert the
  winner if one player ends up winning with three in a row
    * Hint: Determine a set of winning combinations. Check those
      combinations on the board contents after every move.


##### Starter code

There is no starter code provided for this lab.

##### Deliverable

Please find some screenshots of what you'll be creating.  Feel free to get creative with how you style your interface.

![Screen-shot](https://i.imgur.com/kz2L9f9.png)
![Screen-shot](https://i.imgur.com/d8lFshD.png)
![Screen-shot](https://i.imgur.com/Jw6hhcA.png)

##### Additional Resources

- [CSS-Tricks "What Is The DOM"](https://css-tricks.com/dom/)
- [More on events with Eloquent JavaScript](http://eloquentjavascript.net/14_event.html)

### TGIF

* Finish up all the homework and labs that we have given you over the weekend
* Special mentions for Tic Tac Toe
  * It is very important that you finish up Tic Tac Toe by this weekend. 
  * Please update us over the weekend on your progress by uploading your solutions on Google drive by Saturday night.
    * Please finish the layout/basic js DOM by Saturday.











