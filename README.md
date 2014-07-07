Java Day 1
====

Today, we're going to be doing a recap of the `Zen` library for the new students that are joining us. If you haven't used `Zen` before, don't worry - it's a really simple graphics library that lets us visualize Java concepts. 

Today, you will develop a simple Zen application that you can draw on with your mouse. If you've done this activity before, move on to the [advanced continuations](#advanced-continuations).

## Getting started

If this is your first project, you will first have to right click in the package explorer and select "New > Java Project". Refer to the [instructions at zenlab.io](https://zenlab.io/start) if you are not familiar with making Eclipse projects and setting them up with your files.

There are a couple things that people get stuck on when starting up their Zen project:
 - Not right clicking on *both* .jar files and adding them to the build path. 
 - Not placing the .jar files in the project folder.

Once you've created a project, you can double click on it to view its content. You should see a folder named "src" - right click on this folder and select "New > Class". In the dialog that pops up, give the class a name of `Drawing` and **check the box for `public static void main(String[] args)`**.

Once you've done this, you should have an empty file that looks like this:
```java
public class Drawing {
	public static void main(String[] args) {
		// All the code that you'll type today will be in here.
	}
}
```

**Ask an instructor for help if you aren't able to get your project set up!**

## Start coding

Remember the print function, `System.out.println`. Try adding a print statement to your code.

```java
public class Drawing {
	public static void main(String[] args) {
    System.out.println("Hello, world!");
	}
}
```

You should click the green run button in Eclipse to run their code. The run button looks like a green play button in the top toolbar - ask an instructor if you're not able to find it. You should see the console print out `Hello, world!`, or whatever text you gave as an input to `System.out.println`.

## The general format of actions

It's a good idea at this point to reinforce the `action(inputs)` idea. Notice how `action` is replaced by the name of the action, like `System.out.println`, and how the input needs to be text **in quotation marks**.
```
 System.out.println   (   "Welcome ... "    )  ;
         1            2          3          4  5
```

`1` is the name of an action, i.e. "print out".

`2` is an open parenthese to indicate the inputs to the action.

`3` is the input. Notice how text is surrounded by quotation marks, so Java doesn't read it as code.

`4` is a closing parentheses. Without it, Java won't know what are the exact set of inputs to the action.

`5` is the semicolon that has to go at the end of every instruction. However, it doesn't go at the end of every line - we'll look at ways later on where we'll write some code that shouldn't have a semicolon at the end of the line.

## Creating a window

Creating a window is also a single one-line function, and follows the same pattern as `System.out.println`. In this case, it takes two inputs - a width and height of the window. Both are given in pixels, the standard unit for measuring a display's size. Notice how the two inputs are separated by a comma (`,`).
```java
Zen.create(500, 500);
```

Hit run after you write this line, so you see a black window show up. **If you don't see a black window show up, ask the people around you first, then ask the instructor**.

## Drawing shapes

Let's start adding some shapes to the black window. We're going to talk about a couple of actions and their inputs, and then you're going to try to work with these actions to draw a scene.

The main actions are `Zen.fillRect` and `Zen.fillOval`. Both of these actions take four inputs - the first two inputs are an `x` and `y` coordinate, and the second two inputs are a `width` and `height`. The `x` and `y` coordinates indicate the top left corner of the rectangle, and the width and height indicate the size. 

```java
Zen.create(500, 500);
Zen.fillRect(100, 200, 50, 100);
Zen.fillOval(100, 200, 50, 100);
```

There are a couple things to note here:
 - the y-axis in `Zen` is *inverted*, which means that the y-axis increases downwards. 
 - `Zen.create` must be the first instruction that you do in your program, before any drawing.

## Changing colors

The default color that the windows draw in is white. To draw in a different color, you would use the `Zen.setColor` method, and give an input of some color, as text in quotations marks.
```java
Zen.setColor("blue");
```
Think of yourself as an artist with a palette. Whenever you dip your paintbrush into a certain color in the palette, everything you draw on the canvas after that will be in that color, until you dip your paintbrush back in and select a different color. The action of dipping in your paintbrush is `Zen.setColor`, and the action of painting on the canvas is `Zen.fillRect` and `Zen.fillOval`. When you set the color, all future shapes that Zen draws will be in that color. 

## Drawing a scene

Spend some time drawing a simple scene to practice using the graphics functions. It's important to either do the mental math or write out the coordinates for this step, so you can solidy your understanding of coordinates and which inputs control what aspects of the shapes being drawn. 

You will draw upon these simple drawing methods frequently throughout this course, so it is important that you get comfortable with using them.

```java
Zen.create(500, 500);
Zen.setColor( ... );
Zen.fillRect( ... );
Zen.fillOval( ... );
Zen.setColor( ... );
...
```

## Animating

An animation is just a bunch of pictures shown one after another, with a slight pause in between. At this point you should be able to draw a picture - now let's talk about adding the slight pause in between pictures using the `Zen.sleep` action.
```java
Zen.sleep(1000);
```
The `Zen.sleep` action takes in an amount in milliseconds to wait for. Java will pause the running of instructions for that amount of time, and resume the instructions after the `sleep` once the delay time has elapsed.

Use the sleep to create a simple animation where something in your scene changes, or something new pops in. Your code should look something like this.
```java
Zen.create(500, 500);
// Do some drawing with fillRect, fillOval, setColor
Zen.sleep(1000);
// Do some more drawing
Zen.sleep(500);
// Do some more drawing
```

## Connecting the mouse

The actions in `Zen` don't just perform drawing tasks, they can also provide data. One of those actions is called `Zen.getMouseX`, which takes no inputs and returns the x position of the mouse.
```java
Zen.getMouseX()
```
The open and closed parentheses at the end signifies that this action doesn't take any inputs. **Even if an action doesn't take inputs, you still need to have the open and closed parentheses at the end**. Forgetting the open and closed parentheses is a very common error.

When an action produces some data, you can use it as the input to another action. The `Zen.getMouseX` action produces a number, so the number it produces can be plugged in as an input to any action expecting a number. For example:
```java
Zen.fillOval(Zen.getMouseX(), 200, 50, 100);
```

If you had to fill in an oval at the mouse's x *and* y position, you could just substitute the `y` input to `Zen.fillOval` with `Zen.getMouseY()`.
```java
Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 100);
```

If you run this, you will see that a shape pops up wherever your mouse cursor is. If you wanted to keep drawing shapes where your mouse cursor is, you could repeat the instruction many times, and leave a short pause in between each one. It's useful to copy and paste for this step.

```java
Zen.create(500, 500);
// Any drawing and sleeping code from the last lesson.
Zen.setColor("red");

Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
Zen.sleep(100);
Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
Zen.sleep(100);
Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
Zen.sleep(100);
Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
Zen.sleep(100);
...
```

Once you have copied and paste the two lines, you will see a progressive animation of shapes show up on your screen, wherever your mouse pointer is.

## Repeating instructions

First isolate the instructions you want to do with curly braces. **The curly braces group together Java instructions, so Java knows to consider them as a logical chunk of code.** Notice how the code within a set of curly braces gets indented, so it is easier for us to visually make out what code is part of the **code block** later on. In the example below, we removed the repeated `Zen.fillOval` and `Zen.sleep` instructions.

```java
Zen.create(500, 500);
// Any drawing and sleeping code from the last lesson.
Zen.setColor("red");

{
	Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
	Zen.sleep(100);
}
```

Once you've done this, add in the `while` statement before the curly braces, along with a set of parentheses `( )`. Inside the parentheses, you need to write a **condition** that tells Java when it should repeat these instructions (and consequently, when it should stop).
```java
while ( ) {
	...
}
```

**A condition is any true or false statement.** You can't put just *any* statement though - it has to be something mathematical, since mathematics is the language that computers understand. So the true or false statement that you put in has to be something involving mathematical operators like `+`, `-`, `*`, `/`, the equality operator `==` (notice the two equal signs), the comparison operators (`<`, `>`), and the logical operators *and* (`&&`) and *or* (`||`). 

For example, you can tell Java to repeat the instructions while the number `1` is less than the number `2`. Since this statement is always true, Java will repeat the instructions within the curly braces forever.
```java
while (1 < 2) {
	// this code gets repeated forever
}
```

At this point, you should be able to draw on your application with the mouse cursor. Their code will look something like this:
```java
Zen.create(500, 500);
// Any drawing and sleeping code from earlier

Zen.setColor("red");
while (1 < 2) {
	Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
	Zen.sleep(100);
}
```

Notice that your application will still work as long as there are mathematically true statements in the condition for the `while` loop.

```java
// while 1 is less than 2
while ( 1 < 2 ) { ... }
// while 1 plus 1 is 2
while ( 1 + 1 == 2) { ... } 
// while 2 plus 3 is less than or equal to 5
while ( 2 + 3 <= 5 ) { ... }
// while 9 is greater than 8
while ( 9 > 8 ) { ... }
// while 1 is less than 2 and 2 is less than 3
while ( 1 < 2 && 2 < 3 ) { ... }
// while 5 > 0 or 100 < 0
while ( 5 > 0 || 100 < 0 ) { ... }
```

## Changing colors

Students will now use the keys on the keyboard to change the drawing color. To do this, they need to add an `if` condition to their `while` loop to set a different color when a certain key is pressed.

Start by writing out the instruction they would need to do.
```java
Zen.create(500, 500);
Zen.setColor("red");
while (1 < 2) {
	
	// Add in the line below
	Zen.setColor("blue");

	Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
	Zen.sleep(100);
}
```

If they run it now, the color of the oval will always be blue. They can change it so setting it to blue only happens if the `b` key is pressed. Starting with the same process as before, where they put curly braces first around the code they want to do:
```java
{
	Zen.setColor("blue");
}
```

And then control when the code should be run using an `if` condition, which only runs the code block if its given condition is true. The major distinction between `if` and `while` is that an `if` condition only checks the condition once, while a `while` loop will check the condition every time until it evaluates to `false`.
```java
if ( ) {
	Zen.setColor("blue");
}
```

If they add an always-true condition to the if, they will see it always sets the color to blue. If they add an always-false condition, it will remain its original color.
```java
if ( 1 < 2 ) {
	Zen.setColor("blue");
}
```

In this situation, *just as they asked Zen for a number representing the position of the mouse, they can ask Zen for the answer to a true/false question*. The answer is provided by the `Zen.isKeyPressed` method:
```java
Zen.isKeyPressed("b")
```

So the condition to their if could be the answer to `Zen.isKeyPressed("b")`, so their final code would look like this:
```java
Zen.create(500, 500);
Zen.setColor("red");
while (1 < 2) {
	
	if (Zen.isKeyPressed("b")) {
		Zen.setColor("blue");
	}

	Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
	Zen.sleep(100);
}
```

They could add in multiple `if` conditions to check different keys and change the color accordingly.
```java
Zen.create(500, 500);

while (1 < 2) {
	if (Zen.isKeyPressed("b")) {
		Zen.setColor("blue");
	}
	if (Zen.isKeyPressed("r")) {
		Zen.setColor("red");
	}
	if (Zen.isKeyPressed("g")) {
		Zen.setColor("green");
	}

	Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
	Zen.sleep(100);
}
```


