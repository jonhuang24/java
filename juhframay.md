```java
import java.awt.Color;
import java.awt.Graphics;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;
import java.awt.event.MouseMotionListener;

import javax.swing.JFrame;


public class TheGame extends JFrame implements KeyListener, MouseListener, MouseMotionListener {

	int x = 0;
	
	public static void main(String[] args) {
		new TheGame();
	}
	
	public TheGame() {
		super("name of game");	// Step 1
		setSize(500, 500);		// Step 2
		
		addMouseListener(this);
		addKeyListener(this);
		addMouseMotionListener(this);
		
		setVisible(true);		// Step 3
	}
	
	public void paint(Graphics g) {
		g.setColor(Color.WHITE);
		g.fillRect(0, 0, 500, 500);
		g.setColor(Color.RED);
		g.fillOval(x, 200, 40, 40);
	}

	@Override
	public void mouseDragged(MouseEvent e) {
		System.out.println("DRAGGED: " + e.getX() + ", " + e.getY());
	}

	@Override
	public void mouseMoved(MouseEvent e) {
		System.out.println("MOVED: " + e.getX() + ", " + e.getY());
		
	}

	@Override
	public void mouseClicked(MouseEvent e) {
		System.out.println("CLICKED: " + e.getX() + ", " + e.getY());
	}

	@Override
	public void mouseEntered(MouseEvent e) {
		System.out.println("ENTERED: " + e.getX() + ", " + e.getY());
	}

	@Override
	public void mouseExited(MouseEvent e) {
		System.out.println("EXITED: " + e.getX() + ", " + e.getY());
	}

	@Override
	public void mousePressed(MouseEvent e) {
		System.out.println("PRESSED: " + e.getX() + ", " + e.getY());
	}

	@Override
	public void mouseReleased(MouseEvent e) {
		System.out.println("RELEASED: " + e.getX() + ", " + e.getY());
	}

	@Override
	public void keyPressed(KeyEvent e) {
		System.out.println("KEY PRESSED: " + e.getKeyCode());
		x++;
		repaint();	// Don't forget to repaint!
	}

	@Override
	public void keyReleased(KeyEvent e) {
		System.out.println("KEY RELEASED: " + e.getKeyCode());
	}

	@Override
	public void keyTyped(KeyEvent e) {
		System.out.println("KEY TYPED: " + e.getKeyCode());
		
	}
}
```
