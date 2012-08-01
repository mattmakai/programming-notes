Getting Started With D3.js by *Mike Dewar*
==========================================

Chapter 1: Introduction
-----------------------
* Author recommends using [JSLint](http://www.jslint.com/) tool and 
  "use strict"; within the draw function to keep JavaScript code clean
* d3.json('url', function(d) {}); // retrieve json from url and issues callback
  to the function
* Author recommends using another language (such as Python) for doing data 
  manipulation then sending the cleaned data to D3
* store data as key value pairs, with the key as the name of what the data is and
  the data as the value. Do not store data as keys!

Chapter 2: The Enter Selection
------------------------------
* Selections are based on CSS selectors, such as #idName, .className, etc.
* d3 relies heavily on "method chaining" (also known as "cascade"), where each
  method retruns a selection which in turn has methods that return a selection
* the data() methods initializes a selection, then enter() selects only the
  elements with data points that do not already exist on the screen
* enter() can be thought of as "actors entering the stage"

Chapter 3: Scales, Axes, and Lines
----------------------------------
* we need to use numerical, ordinal, log, and time scales to produce
  visualizations based on different types of data, d3 has code to work on
  these built-in
* 

