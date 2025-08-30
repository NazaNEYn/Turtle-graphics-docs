# Python Turtle Graphics: Turtle Object Attributes and Methods
The turtle.Turtle object is the "artist" that draws on the turtle.Screen canvas. You control its movement, appearance, and drawing behavior using a rich set of methods.

## Creating a Turtle Object
First, you need to create a `Screen` and a `Turtle` object:
```python
import turtle
# from turtle import Turtle, Screen

# screen = Screen()
# screen.exitonclick()


screen = turtle.Screen()
screen.colormode(255) # Good practice for consistent color handling (0-255 or color names)
screen.bgcolor("black")
screen.title("My Turtle Program")

my_turtle = turtle.Turtle() # Create a Turtle object
```
-------------------------------------------------------------
# Screen class

```python
# Python Turtle Graphics: Screen Object Attributes and Methods

The `turtle.Screen` object is the window or canvas where all the drawing by `turtle.Turtle` objects takes place. It controls the overall environment and interaction.

## Creating a Screen Object

You typically create a `Screen` object like this:

```python
import turtle

screen = turtle.Screen() # Create the Screen object
```

## 1. Window Control & Setup Methods
These methods are used to configure the size, position, title, and background of the drawing window.

| Method                       | Description                                                                 | Example                                     |
| :--------------------------- | :-------------------------------------------------------------------------- | :------------------------------------------ |
| `setup(width=0.5, height=0.75, startx=None, starty=None)` | Sets the size and position of the main window. `width`/`height` can be pixels or screen fractions. | `screen.setup(width=800, height=600)`       |
| `screensize(canvwidth=400, canvheight=300, bg=None)` | Sets the size of the canvas (the drawable area) within the window.      | `screen.screensize(canvwidth=1000, canvheight=800)` |
| `title(titlestring)`         | Sets the title that appears in the window's title bar.                      | `screen.title("My Turtle Art")`             |
| `bgcolor(colorstring)`       | Sets the background color of the drawing canvas.                            | `screen.bgcolor("lightblue")`               |
| `bgpic(image_name)`          | Sets a background image for the canvas. `image_name` should be a GIF file.  | `screen.bgpic("background.gif")`            |
| `clear()`                    | Deletes all drawings and all turtles from the screen. Resets to initial state. | `screen.clear()`                            |
| `reset()`                    | Similar to `clear()`, but also resets all screen settings to default.       | `screen.reset()`                            |
| `bye()`                      | Shuts down the turtle graphics window. Preferred for clean exit.            | `screen.bye()`                              |
| `exitonclick()`              | Keeps the window open until the user clicks on it, then closes it.          | `screen.exitonclick()`                      |
| `mainloop()` / `done()`      | Starts the event loop; keeps the window open and responsive to events.      | `screen.mainloop()`                         |


## 2. Animation Control Methods
These methods manage how drawing updates are displayed on the screen.

| Method                               | Description                                                                 | Example                                     |
| :----------------------------------- | :-------------------------------------------------------------------------- | :------------------------------------------ |
| `tracer(n=None, delay=None)`         | Turns animation on/off (`n=0` for off) and sets update frequency.           | `screen.tracer(0)` (turn off animation)     |
| `update()`                           | Performs a screen update if `tracer(0)` was set. Crucial for instant display. | `screen.update()`                           |
| `delay(delay=10)`                    | Sets the delay in milliseconds between each turtle step (when tracer is on). | `screen.delay(50)`                          |




## A Simple Analogy for `screen.tracer(0)` and `screen.update()`

### The Theater Analogy

* **`screen.tracer(0)` is like a stage curtain being pulled down.** It hides all the behind-the-scenes work. Your audience (the user) can't see the individual movements of the actors (the turtles).
* **You move the actors (turtles) around on the hidden stage.** You can perform multiple actions (e.g., `turtle.forward(10)`, `turtle.right(90)`) without the audience seeing the intermediate steps.
* **`screen.update()` is like the curtain being lifted for a split second.** This reveals the actors' new positions all at once, creating a new "frame" for your animation.

### Putting It All Together

You'd repeat this process in a **game loop** to create smooth, seamless animation:

1.  **Pull the curtain down (`screen.tracer(0)`).**
2.  **Move the actors (update your turtles' positions).**
3.  **Pull the curtain up to show the new positions (`screen.update()`).**


## 3. Event Handling Methods
These methods allow the screen to respond to user interactions like keyboard presses or mouse clicks.

| Method                       | Description                                                                 | Example                                     |
| :--------------------------- | :-------------------------------------------------------------------------- | :------------------------------------------ |
| `listen(xdummy=None, ydummy=None)` | Sets the focus on the turtle window for keyboard events. Must be called.    | `screen.listen()`                           |
| `onkey(fun, key)`            | Binds a function `fun` to a key press event. `key` is a string (e.g., `"space"`, `"Up"`, `"a"`). | `screen.onkey(move_forward, "Up")`          |
| `onkeypress(fun, key)`       | Similar to `onkey`, but `fun` is called repeatedly while `key` is pressed.  | `screen.onkeypress(rotate_left, "Left")`    |
| `onclick(fun, btn=1, add=None)` | Binds a function `fun` to a mouse click on the screen. `btn` (1=left, 2=middle, 3=right). | `screen.onclick(draw_at_click)`             |
| `ontimer(fun, t=0)`          | Installs a timer that calls `fun` after `t` milliseconds.                   | `screen.ontimer(game_loop, 100)`            |

# Turtle Graphics Event Listeners 

Event listeners are a way to make your `turtle` program interactive. They "listen" for user actions like mouse clicks or key presses and then automatically run a function you've specified.

***

| Event Type | Event Listener Method | Description |
|---|---|---|
| Mouse Events | `screen.onclick(fun, btn=1)` | Binds a function to a mouse click on the screen. The function receives the `x` and `y` coordinates of the click. |
| | `screen.onrelease(fun, btn=1)` | Binds a function to a mouse button release on the screen. |
| | `screen.ondrag(fun)` | Binds a function to a mouse motion while a button is held down. |
| Keyboard Events | `screen.onkey(fun, key)` | Binds a function to a key press and release. Requires `screen.listen()`. |
| | `screen.onkeypress(fun, key)` | Binds a function to a key press down. |
| | `screen.onkeyrelease(fun, key)` | Binds a function to a key release. |
| Timer Events | `screen.ontimer(fun, t=0)` | Schedules a function to be called after a time delay in milliseconds. |


## 4. Coordinate System & Color Methods
These methods control the coordinate system and how colors are interpreted.

| Method                       | Description                                                                 | Example                                     |
| :--------------------------- | :-------------------------------------------------------------------------- | :------------------------------------------ |
| `setworldcoordinates(llx, lly, urx, ury)` | Sets up a user-defined coordinate system for the screen.                    | `screen.setworldcoordinates(-1, -1, 1, 1)`  |
| `colormode(cmode=None)`      | Sets the color mode (`1.0` for 0.0-1.0 RGB floats, `255` for 0-255 integers/names). | `screen.colormode(255)`                     |
| `mode(mode=None)`            | Sets the turtle mode (`"standard"`, `"logo"`, `"world"`).                   | `screen.mode("logo")`                       |


## 5. Input & Query Methods
These methods allow getting input from the user or querying screen properties.

| Method                       | Description                                                                 | Example                                     |
| :--------------------------- | :-------------------------------------------------------------------------- | :------------------------------------------ |
| `numinput(title, prompt, default=None, minval=None, maxval=None)` | Pops up a dialog window to get a numeric input from the user.             | `age = screen.numinput("Age", "How old are you?", 18, 0, 120)` |
| `textinput(title, prompt)`   | Pops up a dialog window to get a string input from the user.                | `name = screen.textinput("Name", "What's your name?")` |
| `window_width()`             | Returns the current width of the window in pixels.                          | `width = screen.window_width()`             |
| `window_height()`            | Returns the current height of the window in pixels.                         | `height = screen.window_height()`           |
| `turtles()`                  | Returns a list of all `turtle.Turtle` objects currently on this screen.     | `all_turtles = screen.turtles()`            |


## Example Usage:
```python
import turtle

# Create the Screen object
screen = turtle.Screen()

# 1. Window Control & Setup
screen.setup(width=700, height=500)
screen.title("Screen Methods in Action")
screen.colormode(255) # Set color mode for names/hex
screen.bgcolor("#3399FF") # A nice blue background

# 2. Animation Control
screen.tracer(0) # Turn off automatic updates for faster drawing

# Create a turtle
my_turtle = turtle.Turtle()
my_turtle.speed(0) # Max speed
my_turtle.color("yellow")

# Draw something quickly
for i in range(100):
    my_turtle.forward(i)
    my_turtle.left(91)

screen.update() # Update the screen to show all drawing at once

# 3. Event Handling
def handle_space_key():
    my_turtle.clear() # Clear drawing
    my_turtle.penup()
    my_turtle.goto(random.randint(-200, 200), random.randint(-200, 200))
    my_turtle.pendown()
    my_turtle.write("Pressed Space!", align="center", font=("Arial", 16, "normal"))

import random # Need random for the example

screen.listen() # Listen for keyboard events
screen.onkey(handle_space_key, "space") # Bind space key to function

# 4. Input & Query
user_name = screen.textinput("User Input", "Enter your name:")
if user_name:
    my_turtle.penup()
    my_turtle.goto(0, -150)
    my_turtle.pencolor("white")
    my_turtle.write(f"Hello, {user_name}!", align="center", font=("Arial", 18, "bold"))
    screen.update() # Update again for the text

print(f"Window dimensions: {screen.window_width()}x{screen.window_height()}")


# Keep the window open until clicked
screen.exitonclick()
```

-------------------------------------------------------------
# Turtle class :
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
These methods determine how the lines are drawn by the turtle.<br>
[Turtle Colors](https://cs111.wellesley.edu/reference/colors)


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


## 7. Measurement Methods

| Method | Description | Example |
| :--- | :--- | :--- |
| `position()` / `pos()` | Returns the turtle's current `(x, y)` coordinates as a `Vec2D` tuple. | `my_turtle.position()` |
| `xcor()` | Returns the turtle's current x-coordinate. | `my_turtle.xcor()` |
| `ycor()` | Returns the turtle's current y-coordinate. | `my_turtle.ycor()` |
| `heading()` | Returns the turtle's current heading (the direction it's facing in degrees). | `my_turtle.heading()` |
| `distance(x, y)` | Returns the distance from the turtle's current position to the specified coordinates. | `my_turtle.distance(0, 0)` |


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
