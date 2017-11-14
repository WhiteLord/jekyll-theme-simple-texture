---
layout: post
title: "Java data stuctures"
description: "This article shows the basics of java data structures"
categories: [java]
tags: [java, data structures, basics]
redirect_from:
  - /2017/10/17/
---
This article is focused on data structures in Java. 
Without having a bright idea of how data structures in Java work, we wouldn't be able to write clear, 
robust and reusable code, our application will load as slow as hell, and all will come down with 
a single bug.
In order to detatch ourselves from bad examples and focus on the things that matter, 
this article will give a basic guide on the basics of java data structures and when to use the 
ready-to-go built-in elements.

## Arrays

As stated [here](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html "Oracle's website on arrays"), an array is a container object that hold a fixed number of values of a single type. Having this in mind, we cannot mix different data types (int and String for example).


{% highlight javascript linenos=table %}
int[] someIntArray = new int[];
String[] someStringArray = {"Some", "value", "goes", "here"};
long[] someLongArray = new long[]{};
{% endhighlight %}

There are different ways of initializing an array, as I've shown above. 

![smiley](https://docs.oracle.com/javase/tutorial/figures/java/objects-tenElementArray.gif)

The capabilities of an arry do not allow us to change its size once it's initialized, 
meaning that if we need to add a new member in this type of data structure, 
we should make a copy of the old array, and initialize a new one, which is **+_n_** members bigger or **_n_** times bigger,
where **_n_** stands for the number of members we want to add to the array.

Disadvantage of an array is the slow speed member values are stored or deleted from an array, meaning that
the use of array is only good enough **when we want to access a certain member of the array by index**.
For example:

{% highlight javascript linenos=table %}
int[] sampleArray = new int{1,2,4,5,6,7,8,9};
for(int i=0; i<sampleArray.lenght; i++){
    System.out.println(sampleArray[i]);
}
{% endhighlight %} 

In the next section, we'll be looking at the LinkedList and ArrayList data structures.