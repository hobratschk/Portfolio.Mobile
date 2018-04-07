# Website Performance Optimization portfolio project

## Introduction
This project was part of my advanced Udacity coursework. I took a terribly under-performing
website, and made it more performant (at least 60 fps). But it's still visually terrible.

## Running Instructions
1. Go to the Settings tab in my new-frontend-nanodegree-mobile-portfolio repository
2. Scroll down to the GitHub Pages section, and open the link in your preferred browser.
3. Click on the Cam's Pizzeria link to view my optimizations. Try the size-change
  slider and scroll up and down the page to your heart's content. The changes are
  detailed below.
4. I have not yet significantly altered the content in Build Your Own 2048,
Website Performance Optimization, or Mobile Web Development links.

## My Changes:
### Changes to Index.html
1. inlined all of style.css in both index and pizza htmls (didn't delete it b/c
  style.css is in use by project-2048.html, project-mobile.html, and project-webperf.html)
2. optimized all images with optimizilla.com
3. add media='print' attr. to link tag of print.css
4. commented out google font Open Sans (didn't notice an advantage to keeping it)
5. added async attr. to analytics.js and perfmatters
6. resized pizzeria.jpg to 100 x 75px

### Changes to views/js/main.js
1. removed determineDx function
2. added will-change:transform and transform:translateZ(0)
  to .mover in views/CSS
2. in scroll function I changed the .mover pizzas from 200 to 24 (8 cols x 3 rows),
  wanted to resize pizza.png so browser doesn't have to access elem.style.height
  and elem.style.width for every pizza element, but when I did, the .mover pizzas
  became huge, and neither changing the size of pizza.png or changing .mover css
  made a difference, but commenting out the height and width properties didn't seem
  to affect scrolling fps
3. added requestAnimationFrame to updatePositions (asks browser to call a
  specific function and update animation before next repaint)
4. also changed updatePositions by moving the calculation which utilizes
  scrollTop method outside the loop (this was causing layout thrashing)

## Below are the instructions/tips provided by Udacity

### Getting started
#### Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

Profile, optimize, measure... and then lather, rinse, and repeat. Good luck!

#### Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js.

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>
