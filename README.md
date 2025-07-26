# Python Turtle Graphics: Turtle Object Attributes and Methods
The turtle.Turtle object is the "artist" that draws on the turtle.Screen canvas. You control its movement, appearance, and drawing behavior using a rich set of methods.

## Creating a Turtle Object
First, you need to create a `Screen` and a `Turtle` object:
```python
import turtle

screen = turtle.Screen()
screen.colormode(255) # Good practice for consistent color handling (0-255 or color names)
screen.bgcolor("black")
screen.title("My Turtle Program")

my_turtle = turtle.Turtle() # Create a Turtle object
```

## 1. Motion Methods
These methods control how the turtle moves on the screen.

| Method                                    | Description                                                                 | Example                                     |
| :---------------------------------------- | :-------------------------------------------------------------------------- | :------------------------------------------ |
| `forward(distance)` / `fd()`              | Moves the turtle forward by `distance` units in its current direction.      | `my_turtle.forward(100)`                    |
| `backward(distance)` / `bk()`/ `back()`   | Moves the turtle backward by `distance` units. Heading remains unchanged.   | `my_turtle.backward(50)`                    |
| `right(angle)` / `rt()`                   | Turns the turtle right by `angle` degrees.                                  | `my_turtle.right(90)`                       |
| `left(angle)` / `lt()`                    | Turns the turtle left by `angle` degrees.                                   | `my_turtle.left(45)`                        |
| `goto(x, y)` / `setpos()` / `setposition()` | Moves the turtle to an absolute position `(x, y)`. Draws if pen is down.    | `my_turtle.goto(50, -75)`                   |
| `setx(x)`                                 | Sets the turtle's x-coordinate to `x`.                                      | `my_turtle.setx(10)`                        |
| `sety(y)`                                 | Sets the turtle's y-coordinate to `y`.                                      | `my_turtle.sety(-20)`                       |
| `setheading(angle)` / `seth()`            | Sets the turtle's orientation to `angle` degrees (0=East, 90=North by default). | `my_turtle.setheading(180)` (point West)    |
| `home()`                                  | Moves the turtle to `(0, 0)` and sets heading to 0 degrees.                 | `my_turtle.home()`                          |
| `circle(radius, extent=None, steps=None)` | Draws a circle. `radius` (positive for counter-clockwise). `extent` for partial circle. `steps` for inscribed polygon. | `my_turtle.circle(50)`                      |


## 2. Pen Control Methods
These methods determine how the lines are drawn by the turtle.

| Method                                 | Description                                                                 | Example                                     |
| :------------------------------------- | :-------------------------------------------------------------------------- | :------------------------------------------ |
| `penup()` / `pu()` / `up()`            | Lifts the pen, so the turtle stops drawing when it moves.                   | `my_turtle.penup()`                         |
| `pendown()` / `pd()` / `down()`        | Puts the pen down, so the turtle draws when it moves.                     | `my_turtle.pendown()`                       |
| `pensize(width)` / `width()`           | Sets the thickness of the drawing line to `width` pixels.                   | `my_turtle.pensize(3)`                      |
| `pencolor(color)`                      | Sets the color of the drawing line.                                         | `my_turtle.pencolor("red")`                 |
| `fillcolor(color)`                     | Sets the color used for filling shapes.                                     | `my_turtle.fillcolor("blue")`               |
| `color(pencolor, fillcolor)`           | Sets both the pen color and the fill color.                                 | `my_turtle.color("red", "yellow")`          |
| `begin_fill()`                         | Call this before drawing a shape to be filled.                              | `my_turtle.begin_fill()`                    |
| `end_fill()`                           | Call this after drawing a closed shape to fill it.                          | `my_turtle.end_fill()`                      |
| `clear()`                              | Deletes the turtle's drawings from the screen, but doesn't move the turtle. | `my_turtle.clear()`                         |
| `reset()`                              | Clears drawings, resets turtle to home, and restores default properties.    | `my_turtle.reset()`                         |


## 3. Turtle Appearance Methods
These methods change how the turtle cursor itself looks or behaves.

| Method                       | Description                                                                 | Example                                     |
| :--------------------------- | :-------------------------------------------------------------------------- | :------------------------------------------ |
| `shape(name)`                | Sets the shape of the turtle cursor (`"arrow"`, `"turtle"`, `"circle"`, `"square"`, `"triangle"`, `"classic"`). | `my_turtle.shape("turtle")`                 |
| `speed(speed)`               | Sets the drawing speed (0=fastest, 1=slowest, 10=fastest).                  | `my_turtle.speed(0)`                        |
| `hideturtle()` / `ht()`      | Makes the turtle cursor invisible.                                          | `my_turtle.hideturtle()`                    |
| `showturtle()` / `st()`      | Makes the turtle cursor visible.                                            | `my_turtle.showturtle()`                    |
| `stamp()`                    | Leaves a copy of the turtle's shape at the current position. Returns a stamp ID. | `stamp_id = my_turtle.stamp()`              |
| `clearstamp(stampid)`        | Deletes the stamp with the given `stampid`.                                 | `my_turtle.clearstamp(stamp_id)`            |


## 4. Drawing State / Query Methods
These methods allow you to get information about the turtle's current state.

| Method                       | Description                                                                 | Example                                     |
| :--------------------------- | :-------------------------------------------------------------------------- | :------------------------------------------ |
| `pos()` / `position()`       | Returns the turtle's current `(x, y)` coordinates.                          | `current_pos = my_turtle.pos()`             |
| `xcor()`                     | Returns the turtle's current x-coordinate.                                  | `x = my_turtle.xcor()`                      |
| `ycor()`                     | Returns the turtle's current y-coordinate.                                  | `y = my_turtle.ycor()`                      |
| `heading()`                  | Returns the turtle's current heading in degrees.                            | `current_heading = my_turtle.heading()`     |
| `isdown()`                   | Returns `True` if the pen is down, `False` otherwise.                       | `if my_turtle.isdown(): print("Drawing")`  |


## 5. Special Drawing Methods
These methods draw specific elements at the turtle's position.

| Method                                     | Description                                                                 | Example                                                                 |
| :----------------------------------------- | :-------------------------------------------------------------------------- | :---------------------------------------------------------------------- |
| `dot(size=None, color=None)`               | Draws a circular dot at the turtle's current position.                      | `my_turtle.dot(10, "green")`                                            |
| `write(arg, move=False, align="left", font=...)` | Writes text at the turtle's current position. `font` is a tuple `(name, size, type)`. | `my_turtle.write("Hello!", font=("Arial", 12, "bold"))`               |

## 6. Event Handling Methods (Turtle-Specific)
These methods allow the turtle object itself to respond to mouse events. (For keyboard events and screen clicks, use `screen` methods.)

| Method                       | Description                                                                 | Example                                     |
| :--------------------------- | :-------------------------------------------------------------------------- | :------------------------------------------ |
| `onclick(fun, btn=1, add=None)` | Binds a function `fun` to a mouse click event *on the turtle*.             | `my_turtle.onclick(on_turtle_click_func)`   |
| `ondrag(fun, btn=1, add=None)` | Binds a function `fun` to when the turtle is dragged with the mouse.        | `my_turtle.ondrag(on_turtle_drag_func)`     |


## Example Usage:
```python
import turtle

screen = turtle.Screen()
screen.colormode(255)
screen.bgcolor("black")
screen.title("Turtle Methods Demo")

artist = turtle.Turtle()
artist.shape("turtle")
artist.speed(0)
artist.pensize(2)
artist.pencolor("cyan")
artist.fillcolor("purple")

# Draw a filled square
artist.penup()
artist.goto(-100, 100)
artist.pendown()
artist.begin_fill()
for _ in range(4):
    artist.forward(150)
    artist.right(90)
artist.end_fill()

# Write some text
artist.penup()
artist.goto(0, 180)
artist.pencolor("yellow")
artist.write("Python Turtle", align="center", font=("Verdana", 24, "bold"))

# Keep the window open until clicked
screen.exitonclick()
```
