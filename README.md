Java Day 2
====

Today, we're going to be practicing creating objects and classes, so we can build more complex games this week and next week. If you already tried to build a complex game using only the `Zen` functions and a `while` loop, you may have noticed that you were repeating the same code many times on different variables or ending up with large blocks of unorganized code. Making classes and objects is helpful for both organizing code and efficiently repeating it.

## Think of an analogy

In our example we're going to use a Hogwarts analogy to think about classes and objects. You'll start by making two files, a `Hogwarts` class that has a `public static void main` method, and a `Wand` class that is empty.

**In Hogwarts.java:**
```java
public class Hogwarts {
	public static void main(String[] args) {
		
	}
}
```

**In Wand.java:**
```java
public class Wand {
	
}
```

## What is a class?

A class is a **structure for storing/describing data and methods**. We're going to go over an analogy to the `Human` class (a way to describe all humans), and look at how it affects the actual memory locations stored in your computer.

```java
class Human {
	int age;
	
	// A regular method
	public void run() {
		...
	}
	
	// A method that takes in an input
	public void eat(int amountOfFood) {
	
	}
}
```

## What is an object?

An object is made from a class. Like the `Human` class described all humans, a `Human` object is a specific human made from that description.

To make a `Human` object with Java code, you would write
```java
Human h = new Human();
```

This tells Java to take the `Human` class and make enough space in memory to store all the data and actions that a `Human` object can do.

## Coding your analogy

We're going to start by making actions that a `Wand` object can do.
```java
public class Wand {

	// The wand can be told to attack
	public void attack() {
		System.out.println("crucio!");
	}
}
```

Then, we'll make a `Wand` object and *call* the method. You've already seen how to make an object - once you have an object, you can tell it to do things with the `.` operator.
```java
public class Hogwarts {
	public static void main(String[] args) {
		Wand w = new Wand();
		w.attack();
	}
}
```

## Expand your analogy

You're going to continue your analogy and add more classes, so you can practice writing classes in different files and combining the result through a single application. The instructors will guide you through this today, and will keep adding advanced continuations below as your class progresses.














