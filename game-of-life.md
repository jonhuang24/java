## Conway's Game of Life

[TODO: add links and description]

```java
import zen.core.Zen;


public class GameOfLife {

	static boolean[][] grid = new boolean[50][50];
	
	public static void main(String[] args) {
		Zen.create(500, 500);
		fillBoardRandomly();
		
		while (true) {
			drawBoard();
			checkClick();
			transition();
			Zen.buffer(50);
		}
	}

	private static void checkClick() {
		// TODO Auto-generated method stub
		
	}

	private static void transition() {
		boolean[][] nextGrid = new boolean[50][50];
		
		for (int x = 0 ; x < 50 ; x++) {
			for (int y = 0 ; y < 50 ; y++) {
				int count = 0;
				if (x > 0 && grid[x - 1][y] == true) {
					count = count + 1;
				}
				if ( x > 0 && y > 0 && grid[x - 1][y - 1] == true ) {
					count = count + 1;
				}
				if ( y > 0 && grid[x][y - 1] == true ) {
					count = count + 1;
				}
				if ( y > 0 && x < 49 && grid[x + 1][y - 1] == true ) {
					count = count + 1;
				}
				if ( x < 49 && grid[x + 1][y] == true ) {
					count = count + 1;
				}
				if ( x < 49 && y < 49 && grid[x + 1][y + 1] == true ) {
					count = count + 1;
				}
				if ( y < 49 && grid[x][y + 1] == true ) {
					count = count + 1;
				}
				if ( x > 0 && y < 49 && grid[x - 1][y + 1] == true) {
					count = count + 1;
				}
				// check count, and change nextGrid accordingly
				
				if (grid[x][y] == false && count == 3) {
					nextGrid[x][y] = true;
				}
				if (grid[x][y] == true && count == 2) {
					nextGrid[x][y] = true;
				}
				if (grid[x][y] == true && count == 3) {
					nextGrid[x][y] = true;
				}
			}
		}
		
		grid = nextGrid;
	}

	private static void fillBoardRandomly() {
		for (int x = 0 ; x < 50 ; x++) {
			for (int y = 0 ; y < 50 ; y++) {
				if ( Zen.dice(6) == 1 ) {
					grid[x][y] = true;
				}
			}
		}
	}

	private static void drawBoard() {
		Zen.setBackground("white");
		// Go to every x between 0 and 50
		for (int x = 0 ; x < 50 ; x++) {
			// Go to every y  between 0 and 50
			for (int y = 0 ; y < 50 ; y++) {
				if ( grid[x][y] == true ) {
					Zen.setColor("black");
					Zen.fillRect(x * 10, y * 10, 10, 10);
				}
			}
		}
	}

}
```
