---
title: "Intro to R"
author: "Kara Woo"
date: "03/26/2015"
output: html_document
---



> ### Learning Objectives {.objectives}
>
> * Familiarize participants with R syntax
> * Understand the concepts of objects and assignment
> * Understand the concepts of vector and data types
> * Get exposed to a few functions


### What is R?

R is an open source language for statistics and visualization. R is free and
has a large (and growing) community, making it a popular choice for data
analysis.

RStudio is an IDE, or "integrated development environment" for R. You don't
need to use RStudio to use R, but it comes with a lot of handy features.

*Point out different RStudio panes and show inputing basic commands directly
into console; explain difference between console and script*

### Creating objects

While you can type commands directly in the console, usually you'll want to
create objects, using "assignment". You assign values, data, etc. to objects
using the `<-` ooperator. For example:


~~~{.r}
x <- 8
x
~~~



~~~{.output}
[1] 8

~~~

Here we have created an object called `x` and assigned it the value 8. We can
then use `x` in other calculations or other assignments.


~~~{.r}
x * 3
~~~



~~~{.output}
[1] 24

~~~



~~~{.r}
y <- x / 2
y
~~~



~~~{.output}
[1] 4

~~~

You can overwrite an object's value at any time.


~~~{.r}
y
~~~



~~~{.output}
[1] 4

~~~



~~~{.r}
y <- 15
y
~~~



~~~{.output}
[1] 15

~~~

To view the objects that are in your current environment, use `ls()`.


~~~{.r}
ls()
~~~



~~~{.output}
[1] "hook_in"  "hook_out" "x"        "y"       

~~~

### Vectors and data types

*Adapted from Christie Bahlai's [materials](https://github.com/cbahlai/2015-01-05-wise-umich/) for the 2015-01-05 UMich workshop*

A vector is a group of values, mainly either numbers or characters. You can
assign this set of values to a variable, just like you would for one item. For
example we can create a vector of animal weights:


~~~{.r}
weights <- c(50, 60, 65, 82)
weights
~~~



~~~{.output}
[1] 50 60 65 82

~~~

The `c()` stands for "combine". A vector can also contain characters:


~~~{.r}
animals <- c("mouse", "rat", "dog")
animals
~~~



~~~{.output}
[1] "mouse" "rat"   "dog"  

~~~

The contents of a vector must all be the same type (i.e. all character or all
numeric).

Functions in R let you perform various operations, such as finding the mean of
a set of numbers, for example. Functions have a name followed by a set of
parentheses that contain arguments to the function. In many cases the first
argument to a function will be an object that you are working with.

If you want to learn more about a function you can look up the help file for it
by typing `?functionname`.

There are many functions that allow you to inspect the content of a
vector. `length()` tells you how many elements are in a particular vector:


~~~{.r}
length(weights)
~~~



~~~{.output}
[1] 4

~~~



~~~{.r}
length(animals)
~~~



~~~{.output}
[1] 3

~~~

`class()` indicates the class (the type of element) of an object:


~~~{.r}
class(weights)
~~~



~~~{.output}
[1] "numeric"

~~~



~~~{.r}
class(animals)
~~~



~~~{.output}
[1] "character"

~~~

The function `str()` provides an overview of the object and the elements it
contains. It is a really useful function when working with large and complex
objects:


~~~{.r}
str(weights)
~~~



~~~{.output}
 num [1:4] 50 60 65 82

~~~



~~~{.r}
str(animals)
~~~



~~~{.output}
 chr [1:3] "mouse" "rat" "dog"

~~~

You can add elements to your vector simply by using the `c()` function:


~~~{.r}
weights <- c(weights, 90) # adding at the end
weights <- c(30, weights) # adding at the beginning
weights
~~~



~~~{.output}
[1] 30 50 60 65 82 90

~~~

What happens here is that we take the original vector `weights`, and we are
adding another item first to the end of the other ones, and then another item at
the beginning. We can do this over and over again to build a vector or a
dataset. As we program, this may be useful to auto-update results that we are
collecting or calculating.

We just saw 2 of the 6 **data types** that R uses: `"character"` and
`"numeric"`. The other 4 are:

* `"logical"` for `TRUE` and `FALSE` (the boolean data type)
* `"integer"` for integer numbers (e.g., `2L`, the `L` indicates to R that it's
an integer)
* `"complex"` to represent complex numbers with real and imaginary parts (e.g.,
  `1+4i`) and that's all we're going to say about them
* `"raw"` that we won't discuss further

Vectors are one of the many **data structures** that R uses. Other important
ones are lists (`list`), matrices (`matrix`), data frames (`data.frame`) and
factors (`factor`).

> ### Challenge {.challenge}
>
> Combine objects `x`, `y`, and `weights` into a vector called `z`. Find the
> mean of this set of numbers (hint: there is a function called `mean()`).