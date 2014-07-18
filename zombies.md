In BouncingBalls.java

```java
import java.awt.Color;
import java.awt.Graphics;
import java.util.ArrayList;

import javax.swing.JFrame;


public class BouncingBalls extends JFrame {
	// My list of balls
	ArrayList<Ball> balls = new ArrayList<Ball>();
	
	public static void main(String[] args) {
		
		new BouncingBalls();
	}

	public BouncingBalls() {
		super("Balls");		// Ingredient 1
		setSize(600, 600);	// Ingredient 2
		
		for (int index = 0 ; index < 100 ; index++) {
			// Make a ball and add it to the list
			Ball b = new Ball();
			b.setup();
			balls.add(b);
		}
		
		setVisible(true);	// Ingredient 3
	}
	
	public void paint(Graphics g) {
		g.setColor(Color.WHITE);
		g.fillRect(0, 0, 600, 600);
		
		for (Ball b : balls) {
			b.move();
			b.paint(g);
		}
		
		// Try waiting for a thirtieth of a second
		try {
			Thread.sleep(33);
		}
		catch (InterruptedException e) {
			System.out.println("Interrupted!");
		}
		
		// Repaint the window
		repaint();
	}
}

```

In Ball.java

```java
import java.awt.Color;
import java.awt.Graphics;


public class Ball {
	int x = 300;
	int y = 300;
	int dx = 7;
	int dy = 9;
	boolean infected = false;
	
	public void setup() {
		x = (int) (Math.random() * 600);
		y = (int) (Math.random() * 600);
		dx = (int) (Math.random() * 21) - 10;
		dy = (int) (Math.random() * 21) - 10;
	}
	
	public void paint(Graphics g) {
		g.setColor(Color.GREEN);
		g.fillOval(x - 5, y - 5, 10, 10);
	}
	
	public void move() {
		x = x + dx;
		y = y + dy;
		
		if (x < 5) {
			x = 25;
			dx = dx * -1;
		}
		if (x > 595) {
			x = 575;
			dx = dx * -1;
		}
		if (y < 5) {
			y = 25;
			dy = dy * -1;
		}
		if (y > 595) {
			y = 575;
			dy = dy * -1;
		}
	}
}

```
