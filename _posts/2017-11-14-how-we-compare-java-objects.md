---
layout: post
title: "Comparing java objects"
description: "This article depicts the basiscs of sorting java arrays"
categories: [java]
tags: [java, sorting, basics, Collections]
redirect_from:
  - /2017/11/14/
---
This article is focused on sorting different objects within a data structure in Java.

So, why is it important to have sorting functionality? Well, imagine that you go in a webiste, that sells you different stuff and you want to buy something. But sice you want to have the best item for the lowest price, you don't want to spend much money on it. 
So, what do you do? You filter out the results, so that the object with the lowest price and/or shipping is to be delivered to you. Easy-peasy.

Now, how do we make this work in java?

First of all, we need to learn what the [***Collections Framework***](https://docs.oracle.com/javase/tutorial/collections/ "Oracle's website")  is.

In short, **collections**, is the abstract human representation of the way items are sorted, based on their properties.
The **Collection Interface** in the Java programming language represents a group of objects, which can be later compared, based on their common properties.
The **Collections Class** in the Java programming language represents a class, which contains only static methods, which could be used in order to fullfil a sorting method later on.

How does the **Colections class** do its trick? 
Quite simply, `java.util.Collecions` supply static methods and *polymorphic* algorithms. For example, the `Collecitons.sort()` method is fed a collection, which has implemented the **List Interface**. From this, we can deduce that `Collections.sort` works for **ArrayList, LinkedList, Vector**.

So how do we implement a sorting functionality in our code?

Firstly, we create a class, which will later be instantiated. In our case, it's a Student object, contatining two fields - a String field, carrying the name of the object, and an integer one, representing the object's age.

{% highlight javascript linenos=table %}
public class Student{
	private String name;
	private int age;
	
	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public Student(String name, int age) {
		this.age = age;
		this.name = name;
	}
}

{% endhighlight %}

Then we have the Main.java class here:

{% highlight javascript linenos=table %}
import java.util.*;

public class Main {
	public static void main(String[] args) {
		
		LinkedList<Student> lls = new LinkedList<>();
		lls.add(new Student("Ivan", 13));
		lls.add(new Student("Svetlin", 22));
		lls.add(new Student("Petkan", 7));
		lls.add(new Student("Strahil", 13));
		
	}
}
{% endhighlight %}

Now we've intantiated and added four Objects of type Student in the **LinkedList**. I've chosen to use **LinkedList** as we'll be mostly inserting/deleting data. Of course, having just four objects put in a LinkedList surely does not give us the upper hand when we use this data structure in comparison to **ArrayList** but that's another topic.

So, we've got two options now - either we implement the Comparator<Object> interface or the Comparable<Object> one.

The big difference between those two interfaces is that the **Comparator** should be used in a custom class, different from the object class.


{% highlight javascript linenos=table %}
import java.util.Comparator;

public class CompareClass implements Comparator<Student> {

	@Override
	public int compare(Student o1, Student o2) {
		if(o1.getAge() > o2.getAge()) {
			return 1;
		}
		else if(o2.getAge() > o1.getAge()) {
			return -1;
		}
		return 0;
	}

}
{% endhighlight %}

As the class implements the interface, it should Override the **compare** method, described in the Interface.

So, this method compares the **age** field of the objects and returns the one that has the lesser value. Values *1, -1* and *0* represent the *state* of the fields - if the method returns *1*, then the first value is greater than the second, *0*, if they are equal and *-1* if the condition is not met. That's why **returning integers instead of booleans is better**.

As we did this, the final step is to use the **Collections.sort()** method in our code.

{% highlight javascript linenos=table %}
import java.util.*;

public class Main {
	public static void main(String[] args) {
		
		LinkedList<Student> lls = new LinkedList<>();
		lls.add(new Student("Ivan", 13));
		lls.add(new Student("Svetlin", 22));
		lls.add(new Student("Petkan", 7));
		lls.add(new Student("Strahil", 13));
		
		CompareClass cc = new CompareClass();
		Collections.sort(lls, cc);
		for(Student s : lls) {
			System.out.println("Student " + s.getName() + " is of age: " + s.getAge());
		}
{% endhighlight %}


Another way of comparing objects, is to use the **Comparable Interface** in the class, which instantiations we would like to compare.
This sounds a bit off, but you'll get the hang of it, as you go through the next lines of code.
Now, the Student class will implement the **Comparable Interface**, and the Student class will have the functionality to do the sorting.

{% highlight javascript linenos=table %}
public class Student implements Comparable<Student>{
	private String name;
	private int age;
	
	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public Student(String name, int age) {
		this.age = age;
		this.name = name;
	}

	@Override
	public int compareTo(Student o) {
		return this.getName().compareTo(o.getName());
	}
}
{% endhighlight %}

In the example we use the `String.compareTo` method, which returns a string, starting with the lowest [ASCII](http://www.asciitable.com/ "Ascii table online") value (for example the Dec value of the capital letter *A* is 65, the lowercase *a*, however is 97).
We don't have to instantiate the `CompareClass` class this time, as the functionality is directly served through the student class. 
In this case, the Main class will look like this:

{% highlight javascript linenos=table %}
import java.util.*;

public class Main {
	public static void main(String[] args) {
		
		LinkedList<Student> lls = new LinkedList<>();
		lls.add(new Student("Ivan", 13));
		lls.add(new Student("Svetlin", 22));
		lls.add(new Student("Petkan", 7));
		lls.add(new Student("Strahil", 13));

		Collections.sort(lls, sns);
		for(Student zz: lls) {
			System.out.println(zz.getName() + " is of age " + zz.getAge());
		}
	}
}
{% endhighlight %}

This way the name and age fields of the object are printed, in ascending order. Reversing the order will be completed using `Collections.reverse()` or `Collections.reverseOrder()`.