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

# Linear Data structures

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


## ArrayList

ArrayList is a linear collection of data elements, that implements the **List interface** and extends the 
**AbstractList class**. 
When we have to compare Arrays with ArrayLists, we can say that Arrays have a fixed size, while the 
size of the ArrayList is dynamically allocated. If more elements are put in the ArrayList, the JVM will
extend the size of the ArrayList with 1.5x the value of the inital size.

Having in mind that the ArrayList Class has a `grow()` function, which includes the `int newCapacity = oldCapacity + (oldCapacity >> 1);` line,
we can surely say that the bitwise operator in this case serves the role of cutting 1 down to 0.5 and thus making
the ArrayList 1.5 times bigger as it used to be.


## LinkedList

LinkedList is a linear collection of data elements, in which their order is not array-based (or array-defined,
	as in the ArrayList)