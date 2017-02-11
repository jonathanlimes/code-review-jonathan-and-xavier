# Code Review for Xavier

## Project Repo

[Xavier's Project Repo: Pong](https://github.com/random-9/wdi-project-1-random-9)

[Actual Game](https://random-9.github.io/wdi-project-1-random-9/)

## Review

#### Project Purpose

The project is a game of Pong, using the following components:
* HTML5 (with Canvas)
* CSS
* JavaScript

#### Project Organization

#### Features

* Use of HTML5 Canvas
  * The game uses HTML5 Canvas. A `canvas` board is declared in the HTML code, on which game objects (`Paddle`, `Ball`) are rendered onto the board with specified coordinates. The `paddle` and `ball` can move around the canvas because they can be assigned `x_speed` and `y_speed`: the speed at which objects move from left to right, and from up to down respectively.
* Collision Events
  * Crucial to the game is a function that detects the collision of two game objects. In this case, the game can only work if it can detect a collision event between a `paddle` and `ball`. A collision event is detected simply by checking if the `x`- and `y`-coordinates of the game objects coincide, as follows:
  ```
  if (bottom_x > paddle1.x && top_x < (paddle1.x + paddle1.width) && top_y < (paddle1.y + paddle1.height) && bottom_y > paddle1.y) {
  ```
* Use of Bootstrap to structure page
  * The page was structured using Bootstrap, which allowed convenient and easy organization of important elements of the game. The game canvas was put in a left column, while the game instructions were placed in a right column.

#### Areas of Success (Code, Organization)

* Very organized, modular code
  * The code is understandable to a person who is reading it for the first time. Every variable/function is clearly defined. Any person who is reading the code can understand what the game objects are because they are declared at the start of the code.
* Good use of constructors
  * The code was efficient. It did not create repetitive objects for each paddle/player, but used a `Paddle` constructor from which two players could be created:
  ```
  function Paddle (x, y, width, height) {
      this.x = x
      this.y = y
      this.width = width
      this.height = height
      this.x_speed = 0
      this.y_speed = 0
  }
  function Player1 () {
      this.paddle = new Paddle(20, 210, 10, 80)
      this.score = 0
  }
  ```
* Product is scalable for additional features in the future
  * I notice that Xavier deliberately kept the dimensions of the `Paddle` modifiable, for addition of difficulty levels in the future:
  ```
  Paddle.prototype.render = function () {
  ctx.beginPath()
      ctx.fillStyle = '#00ff00'
      ctx.fillRect(this.x, this.y, this.width, this.height)
      ctx.closePath()
  }
  ```

#### Areas for Improvement (Code, Organization)

* Direction of ball bounce depends on last recorded direction of paddle, may be slightly inaccurate
  * The code to determine whether the ball will reflect up or down after collision with a paddle is as follows:
  ```
  if (bottom_x > paddle1.x && top_x < (paddle1.x + paddle1.width) && top_y < (paddle1.y + paddle1.height) && bottom_y > paddle1.y) {
      this.x_speed = 5
      this.y_speed += (paddle1.y_speed / 2)
      this.x += this.x_speed
  }
  ```
  This records the last known `y_speed` of `paddle1`, and gives the ball its `y`-direction. This makes sense when the paddle is still moving when the ball collides with it, so the ball follows the same direction in which the paddle is moving. However, the ball takes the last known direction of the paddle even though the paddle is stationary when the ball collides with it. As such, a perfectly still paddle may make the ball bounce up non-intuitively, just because it was moving up a second earlier. To improve the game physics, a possible improvement would be to detect the **collision point of the ball on the paddle**, and give it its `y`-direction depending on **how far it landed from the middle of the paddle.**


* Ball, when reset, always moves in the same direction (towards Player Two)
  * When the ball runs past either player's boundary, the ball resets to start from the middle (`this.x = 300, this.y = 200`). However, because the ball is set to `this.x_speed = 5`, the ball always moves towards Player Two, which might give Player Two an unfair advantage over the game since the starting direction/speed/angle of the ball is always predictable. One suggestion is to change the direction of the ball movement **depending on who scored the most recent point**. For example:
  ```
  if (bottom_x < 5) {
      playerTwo.score++
      this.x_speed = -5   // ball moves towards P1 instead
      this.y_speed = 0
      this.x = 300
      this.y = 200
  }
  ```
  If the code gets too repetitive, consider putting the starting position and motion of the ball into a `resetBall()` function.

## Additional Notes
* Good use of Bootstrap to give the page structure
* Consider removing commented out code in the JS file, e.g. Lines 76-84, 139, 143
* CSS: Consider grouping elements and classes separately, for clearer organization
* To optimize gameplay: Add a timer to increase competitive pressure, introduce powerups or obstacles
