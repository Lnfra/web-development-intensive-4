# Week 7
## Day 1
First sign up an account with https://market.mashape.com/

#####Compulsory Pair Homework:
1. Using the below free API that converts sentences to yoda speak:
  * https://market.mashape.com/ismaelc/yoda-speak
2. Do up a front end using only HTML, CSS, jQuery, Ajax, to input and display data from this API.
3. You app should have an input field and a button.
4. When clicked the text in the input field is to be sent to the API, and the translated text is to be displayed. 
5. Note: to connect to the API, you would need to figure how to use the provided API key.
6. Push the final work to your github repository and create a gh-pages branch
7. Submit the links to the below form by 10/08/16:
  * https://docs.google.com/a/generalassemb.ly/forms/d/e/1FAIpQLScL_LbrM_bcBF-flWYTV5b5oQbDUJk9w8819BgPPChp3w7U9A/viewform

## Day 3
#####Compulsory Readings:
Read up on the introduction to jasmine and ajax jasmine before tomorrow's lesson.
  * http://jasmine.github.io/2.4/introduction.html
  * http://jasmine.github.io/2.4/ajax.html
 
#####Optional Readings (Extra References):
 * http://blog.codeship.com/jasmine-testing-javascript/
 * http://webdesign.tutsplus.com/tutorials/an-introduction-to-ajax-for-front-end-designers--cms-25099

#####Code for the jasmine code-a-long done today can be found at: 
  * https://github.com/primaulia/jasmine-standalone-reference


## Day 4
#####Compulsory Homework:
To finish all the exercises in Learn You Node. And push to a personal repo.

Write the function and jasmine test for a function getDuplicates(). Push the code to a personal repo. 
 * getDuplicates() is to accept one parameter an array of integers 
 * If the input array contains any **non-integers**, throw an error
 * Return an array of the duplicate numbers sorted in ascending error. The duplicate numbers are returned **only once** in the result
 * Return an empty array if the input array has no duplicates
 * If the input is not an array, throw an error.
 * Zero sized array is a valid input.
 * The integers in the input array may not be in order. 

Note: Please submit the above homework to this form before class on 12/8/16.
  * https://docs.google.com/a/generalassemb.ly/forms/d/e/1FAIpQLSfSujosikKnAQmLgDYAio6-24q6DQ2ypZ55z3ZmAANT7GUcZw/viewform


## Day 5
####Compulsory Group Homework: (Deadline Mon 15/08/16 before class.)

##### A front end Dashboard that consumes API public APIs:
1. Create a github repo that host the front end (HTML, ajax javascripts, css)
2. Using the below free API that generates random quotes:
  * https://market.mashape.com/andruxnet/random-famous-quotes
3. Do up a front end using only HTML, CSS, jQuery, Ajax, to pull data from this API.
4. You app should have a button that displays a new random quote when clicked.
5. Note: to connect to the API, you would need to figure how to use the provided API key.
6. Push the final work to your github repository and create a gh-pages branch
7. **Optional Bonus:** Create another static page that consumes the Group Member API (details below)
8. **Optional Bonus:** Also make use of the below Public APIs in your project.
  * Open Weather API
    * http://openweathermap.org/api
    * http://codepen.io/ga-sg/pen/grkGYL
  * Wikipedia API
   * https://en.wikipedia.org/w/api.php
   * http://codepen.io/ga-sg/pen/QEzqLa

##### A node backend that serves an API with your Group Member details:
1. Create a github repo that host the Node Application
2. Use **express framework**
3. Create an API endpoint that lists all group member details in json (e.g. '/members')
4. Application is deployed to Heroku
5. Continuously Integrated with Travis CI (or any CI tool choices) and Heroku
6. Data is hardcoded in json or array of json objects
7. Test to cover at least these three below:
  * API response is as expected (eg: http://myserver.herokuapp.com/members/junius returns junius' json data)
  * API call is a success (eg: http://myserver.herokuapp.com/members/junius returns 200 status code)
  * API call is an error (eg: accessing a non-existing endpoint, 404 status code) 


####Compulsory Individual Homework: (Deadline Wed 17/08/16 before class.)

##### A front end Profile page for yourself consumes the API about You:
1. Create a github repo that host the front end (HTML, ajax javascripts, css)
2. Do up a front end using only HTML, CSS, jQuery, Ajax, to pull data from this API.
3. You app should consumes individual API below and render it in the page 
4. Push the final work to your github repository and create a gh-pages branch

##### A node backend that serves an API about You:
1. Create a github repo that host the Node Application
2. Use **express framework**
3. Create an API endpoint that lists all group member details in json (e.g. '/me')
4. Application is deployed to Heroku
5. Continuously Integrated with Travis CI (or any CI tool choices) and Heroku
6. Data is hardcoded in json or array of json objects
7. Test to cover at least these three below: 
  * API response is as expected
  * API call is a success (eg: http://myserver.herokuapp.com/me returns 200 status code)
  * API call is an error (eg: accessing a non-existing endpoint, 404 status code) 

####Useful Reading Materials:
  * Tutorial on supertest http://willi.am/blog/2014/07/28/test-your-api-with-supertest/
  * Another tutorial on supertest http://www.marcusoft.net/2014/02/mnb-supertest.html
  * Travis Documentation https://docs.travis-ci.com/
  * Restful API in Express https://scotch.io/tutorials/build-a-restful-api-using-node-and-express-4