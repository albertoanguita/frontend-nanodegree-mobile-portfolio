The application is publicly accessible through github pages.

Go to http://albertoanguita.github.io/frontend-nanodegree-mobile-portfolio/ to check the main page

Go to http://albertoanguita.github.io/frontend-nanodegree-mobile-portfolio/views/pizza.html to check the pizzeria page

UPDATE!!: for some reason, the pizzeria page in github does not run the js code and the page does not display the 
random pizzas nor prints the moving pizzas. The code runs fine if downloaded to computer and run locally.

Optimizations in index.html:
----------------------------

These are the modifications I made to achieve a score above 90 in pagespeed:

- Replace pizzeria and profile pics by the ones generated automatically by pagespeed.
- Make analytics.js run asynchronously (add async attribute) so page parsing and rendering is not blocked for this 
code.
- Add media type attribute to css/print.css so it is not loaded by default.
- Inline the full contents of css/style.css in the html file so the css file does not have to be downloaded separately.
- Inline the font attributes in the html code, so they don't have to be downloaded separately


Optimizations in main.js:
-------------------------

i) Optimizing updatePositions function

The updatePositions function in main.js is invoked every time the user scrolls the page. The performance issue is 
caused by this function calculating a complicated phase value (involves the Math.sin function) for each pizza image. 
However, even when there are 200 different pizza images, there are only 5 possible phase values. To solve the problem, 
I precomputed those 5 phase values and stored them in a 5-length array called 'phaseArray'. Then, the for loop 
recovers 
phase values from this array instead of invoking the sin function.

ii) Optimizing the changePizzaSizes function

The changePizzaSizes function was slow because it calculated the newwidth for every single pizza. However, newwidth is 
actually the same for all pizzas, so it can be calculated just once. I moved this calculation outside the loop and 
reused this value for all pizzas.


