# Java Day 4

Yesterday we gave you classes that we had designed to make it easier to design compelling `Zen` games. Today, you're going to design your own class to represent a ball that can bounce off the edges of the window. In this particular example, we'll ignore gravity and assume the ball doesn't slow down.

## First, try it without a class

Here's some code to make a ball bounce around your screen that doesn't use objects. The `x` and `y` variables describe the ball's position in the window, while the `dx` and `dy` variables store the ball's speed.

```java
import zen.core.Zen;

public class BouncingBalls {

	public static void main(String[] args) {
		Zen.create(500, 500);
		int x = 250;
		int y = 250;
		int dx = Zen.dice(10) - 5;
		int dy = Zen.dice(10) - 5;
		
		while (true) {
			Zen.setBackground("white");
			
			// Draw the ball
			Zen.setColor("black");
			Zen.fillOval(x - 10, y - 10, 20, 20);
			
			// Move the ball
			x = x + dx;
			y = y + dy;
			
			// Check collisions on the wall
			if (y < 0) {
				y = 0;			// Set y to be the exact boundary value
				dy = dy * -1;	// Invert the y speed
			}
			
			// TODO: check other 3 wall collisions
			
			Zen.buffer(33);
		}
	}

}
```

**This code isn't complete!** You still need to check for the other 3 wall collisions, which are left to you as an exercise.

With this example, notice how difficult it would be for us to get multiple balls moving around in our window. We'd have to make four variables (`x`, `y`, `dx`, and `dy`) for each one!

## Make a `Ball` class

In general, all balls need to store where they are and how fast they are moving. These four pieces of information comprise the data that belongs to our `Ball` class. The ball also needs to have two actions - an action that moves the ball, and an action that draws it. We've laid out a class below for you to start with. There also needs to be an action that sets up the ball's initial position and speed like we had done above.

```java
public class Ball {
	// Ball data
	int x;
	int y;
	int dx;
	int dy;
	
	public void setup() {
		x = 250;
		y = 250;
		dx = Zen.dice(10) - 5;
		dy = Zen.dice(10) - 5;
	}
	
	public void move() {
		x = x + dx;
		y = y + dy;
		
		if (y < 0) {
			y = 0;			// Set y to be the exact boundary value
			dy = dy * -1;	// Invert the y speed
		}
	}
	
	public void draw() {
		Zen.setColor("black");
		Zen.fillOval(x - 10, y - 10, 20, 20);
	}
}
```

You can now use the `Ball` class in your regular `Zen` application by creating a `Ball` object.
```java
import zen.core.Zen;

public class BouncingBalls {

	public static void main(String[] args) {
		Zen.create(500, 500);
		
		// Create the ball and set it up
		Ball b = new Ball();
		b.setup();
		
		while (true) {
			Zen.setBackground("white");
			
			// Tell the ball to draw and move
			b.draw();
			b.move();
			
			Zen.buffer(33);
		}
	}

}
```

## Your tasks for today
 - Try adding in more balls. This involves making more `Ball` objects.
 - Make it so each ball has a randomly-chosen color.
 - Try adding 2 - 3 balls into your window, and have the balls bounce off each other if they get close enough. You will have to code your own `distanceTo` function in the `Ball` class to make this work in the cleanest possible way.
 
## Advanced continuations

 - Try using an `ArrayList` to store and draw many balls. We'll go more in depth with `ArrayList` next week, but here's the general idea:
 
An `ArrayList` stores a list of any number of objects. To create an `ArrayList` that stores `Ball` objects, you would create a list object and use the `add` method to add objects to it.
```java
ArrayList <Ball> list = new ArrayList <Ball> ();

Ball b = new Ball();
list.add(b);
```

If you want to loop through everything in the list and do some code *for each member of the list*, you would use a `for`-in loop:
```java
for (Ball member : list) {
	member.draw();
	member.move();
}
```

 - Once you've gotten multiple balls working, try having all the balls collide off each other. You don't have to have proper collisions, just have them shoot off in some random direction if they get too close to each other.


