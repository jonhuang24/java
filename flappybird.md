# Flappy Bird

```
package FlappyBird;
import zen.core.Zen;

public class FlappyBird {
	
	static int x = 200;
	static int y = 300;
	static int dy = 0;
	
	static int pipe1 = 400;
	static int pipe2 = 625;
	
	static int center1 = 300;
	static int center2 = 100;
	
	public static void main(String[] args) {
		Zen.create(400, 600);
		
		while (true) {
			Zen.setBackground("light blue");
			
			drawFlappyBird();
			moveFlappyBird();
			
			drawPipes();
			movePipes();
			
			Zen.buffer(33);
		}
	}

	private static void movePipes() {
		pipe1 = pipe1 - 3;
		pipe2 = pipe2 - 3;
		if (pipe1 <= -50) {
			pipe1 = 400;
			center1 = Zen.getRandomNumber(100, 500);
		}
		if (pipe2 <= -50) {
			pipe2 = 400;
			center2 = Zen.getRandomNumber(100, 500);
		}
	}

	private static void drawPipes() {
		Zen.setColor("green");
		Zen.fillRect(pipe1, 0, 50, center1 - 50);
		Zen.fillRect(pipe1, center1 + 50, 50,  550 - center1);
		
		Zen.fillRect(pipe2, 0, 50, center2 - 50);
		Zen.fillRect(pipe2, center2 + 50, 50, 550 - center2);
	}

	private static void moveFlappyBird() {
		y = y + dy;
		dy = dy + 1;
		
		if (Zen.isKeyPressed("space")) {
			dy = -10;
		}
	}

	private static void drawFlappyBird() {
		Zen.setColor("yellow");
		Zen.fillOval(x - 30, y - 20, 60, 40);
	}
}
```
