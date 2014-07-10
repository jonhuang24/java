## Using built-in `Zen` classes

Today, you're going to use some classes that are distributed with the `Zen` library to make your code cleaner and more readable. Under the hood, these classes are just calling `Zen.fillOval`, `Zen.fillRect`, and `Zen.fillPolygon`.

To make a circle or oval,
```java
Oval o = new Oval(40, 30); 		// 40 pixels wide, 30 pixels tall
Circle c = new Circle(20);		// 20 pixels in diameter
```

To change the position of the object `o` or `c`, use the `setX` and `changeX` methods.
```java
o.setX(200);
c.setY(400);
o.changeX(5);
c.changeY(60);
```

You can also set the color of the object by using the `setColor` method.
```java
o.setColor("green");
c.setColor("red");
```

To actually tell the oval and circle to show up, use the `draw` method.
```java
o.draw();
c.draw();
```

You can read the x and y coordinates of the shape using the `getX` and `getY` function.
```java
System.out.println("The y position of the oval is " + o.getY() );
```

**Calling the draw function is really important**. A very common mistake is to set up the objects and all the position changing logic, but forget to tell that object to draw somewhere in your code.

## Quick pointers

There are a couple things you should keep in mind when using the built-in `Zen` shapes.
 - Every shape object can store a unique color. It saves you the effort of having to use `Zen.setColor` before telling the object to draw using the `draw` method.
 - The x and y coordinate for the `Circle`, `Oval`, and `Rectangle` class now refer to the **center** of the shape, not the top left corner. This is primarily for making it easier to measure distances between objects, and to have collisions look realistic.
 - 

## Full reference

In general, every shape has the following methods:
```java
setX( x );				// sets the x and y coordinate
setY( y );
changeX( amount );		// changes the x and y coordinate
changeY( amount );
getX()					// returns the x and y coordinate
getY()					
follow( shape ); 		// Tells this shape to set it's x and y coordinate to the
						// coordinates of another shape
```

### Circles
```java
Circle c = new Circle(40);		// diameter of 40
```

### Ovals
```java
Oval o = new Oval(10, 50);		// width 10, height 50
```

### Rectangles

Make sure that when you import the `Rectangle` class, you are importing it from `zen.shape.Rectangle` and **not from `java.awt.Rectangle``**!

```java
Rectangle r = new Rectangle(60, 80); 	// width 60, height 80
```

### Triangles

When you make a triangle, you need to give six inputs, which correspond to the three vertices of the triangle.
```java
Triangle t = new Triangle( x1, y1, x2, y2, x3, y3 );
Triangle t = new Triangle( 50, 100, 30, 40, 80, 50);
```

### Polygons

To make polygons, you need to make any number of `Point` objects. Make sure that when you import the `Point` class, you are importing it from `zen.shape.Point` and **not from `java.awt.Point``**!

```java
Point p1 = new Point(200, 300);
Point p2 = new Point(300, 500);
...
Point pn = new Point(200, 400);

Polygon poly = new Polygon(p1, p2, p3, ..., pn);
```



