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

Let's use the keys on the keyboard to change the drawing color. To do this, you need to add an `if` condition to your `while` loop to set a different color when a certain key is pressed.

Start by writing out the instruction you would need to do.
```java
Zen.create(500, 500);
Zen.setColor("red");
while (1 < 2) {
	
	// Add in the instruction below
	Zen.setColor("blue");

	Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
	Zen.sleep(100);
}
```

If you run it now, the color of the oval will always be blue. You can change it so setting it to blue only happens if the `b` key is pressed. Starting with the same process as before, where you first put curly braces around the code they want to do:
```java
{
	Zen.setColor("blue");
}
```

Then control when the code should be run using an `if` condition, which only runs the code block if its given condition is true. The major distinction between `if` and `while` is that an `if` condition only checks the condition once, while a `while` loop will check the condition every time until it evaluates to `false`.
```java
if ( ) {
	Zen.setColor("blue");
}
```

If you add an always-true condition to the if, you will see it always sets the color to blue. If you add an always-false condition, it will remain its original color.
```java
if ( 1 < 2 ) {
	Zen.setColor("blue");
}
```

In this situation, *just as you asked Zen for a number representing the position of the mouse, you can ask Zen for the answer to a true/false question*. The answer is provided by the `Zen.isKeyPressed` method:
```java
Zen.isKeyPressed("b")
```

So the condition to your if could be the answer to `Zen.isKeyPressed("b")`:
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

You could add in multiple `if` conditions to check different keys and change the color accordingly.
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

## Advanced continuations

If you've already done this lesson, or you just sped through the basics, here are some advanced continuations that you can use to make your application draw continuous lines or talk over the web.

### Drawing a continuous line

Every time you fill in a point, you are leaving a large gap between the current point you're filling in and the point before it. To fix this, you can use the `Zen.drawLine` method, which draws a line between two (x, y) coordinates.
```java
Zen.drawLine(x1, y1, x2, y2);
```

The `Zen.drawLine` method works like any other `Zen` drawing method, where you can change the line color with `setColor` and you can plug in different inputs to `x1`, `x2`, `y1`, and `y2`. 

Try using `Zen.drawLine` to draw a line between the previous point you drew and the current point where the mouse pointer is. Some guidelines for completing this part:
 - you'll have to make new variables. If you don't remember how to use variables, the general idea is to make a variable by specifying the type and a unique name, like `int x`, and then giving it values by `x = ...`.
 - you'll have to think along the lines of "how do I store where the mouse pointer used to be, and draw a line from that point to where the mouse pointer currently is?". You'll have to extend your thinking to what is happening *between* frames.
 - the order of your instructions is really important.

### Hooking it up over the web

`Zen` has some built-in utility functions to share data with other `Zen` applications. The general way to connect your Zen applications over the web is to
 - Use `Zen.connect` to join a lab where you can share data with other people.
 - Make stuff in your regular `Zen` application move around.
 - Use `Zen.write` to write labeled information about your moving stuff to your lab.
 - Use `Zen.read` and `Zen.readInt` to read labeled information from your lab.
 - Use the labeled information to move things around on your screen.

To start off, add `Zen.connect` to the very top of your `main` method:
```java
public class Drawing {
	public static void main(String[] args) {
		Zen.connect("apples");
	}
}
```

Once you've connected, you can write a labeled piece of information to the web using `Zen.write`.
```java
Zen.write("dalmations", 101);
```

Once you've written some data, **anyone connected to the same lab can read it back with `Zen.readInt`**. 
```java
int d = Zen.readInt("dalmations");
// d will be set to 101
```

You can use this idea to write the x and y coordinate of your mouse to the web, and have your partner read it out. For example, if there are two partners in your Java class Bob and Joe, and theyw anted to hook up their apps over the web, they could do something like this:

**Bob would write his position to the web.**
```java
Zen.connect("bob and joe");

Zen.create(500, 500);
// Any drawing and sleeping code from the last lesson.
Zen.setColor("red");

while (1 < 2) {
	// Write my x and y position to the web
	Zen.write("bob's x", Zen.getMouseX());
	Zen.write("bob's y", Zen.getMouseY());

	Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
	Zen.sleep(100);
}
```

On Joe's computer, he will read in the x position with `Zen.readInt("bob's x")` and the y position with `Zen.readInt("bob's y")`, and draw an oval wherever the x and y coordinate indicates.
```
Zen.connect("bob and joe");
Zen.create(500, 500);
// Any drawing and sleeping code from the last lesson.
Zen.setColor("red");

while (1 < 2) {
	// Write my x and y position to the web
	Zen.fillOval(Zen.readInt("bob's x"), Zen.readInt("bob's y"), 50, 50);

	Zen.fillOval(Zen.getMouseX(), Zen.getMouseY(), 50, 50);
	Zen.sleep(100);
}
```
Notice how both bob and joe connect to the lab `"bob and joe"`. This allows them to read and write data from the same place.

Once you've hooked up your drawing tool to a partner's, try the following read/write exercises.
 - Bob can write his mouse position onto Joe's screen - how would you do it the other way around?
 - How could you read/write the current drawing color, so when you change the drawing color on your screen it changes on the other person's screen as well?
 - See how many people you can get to join your room and have show up on your window.
 



