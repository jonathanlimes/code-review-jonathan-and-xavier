# Code Review for Jonathan Lim

## Project Repo

[Link to project](https://github.com/jonathanlimes/wdi-project-1-jonathanlimes)

## Review

#### Project Purpose

WDI-SG 8 Project 1 - Creating a web browser game

Components of the project:

| Component | Description |
|---------- | ----------- |
| style.css | Main CSS script|
| index.html| Canvas element and main page |
|script.js  | Cash Money game logic, canvas rendering and DOM |
| images    | Background and sprites for the game |
| sounds    | Sound files used for the game |


#### Project Organization

#### Features

* General Gameplay
  * 2 players compete against each other to collect red packets while avoiding firecrackers. Red packets give $2 and firecrackers deduct $3
* Collision events
  * x and y coordinates of the player sprites, red packets, oranges and firecrackers are compared using if-else statements. Different functions are called for each type of collision
* Winner
  * After each collision event with either red packet or firecracker, player money counter variables are updated. Player with the most money when the 30 second timer runs out wins

#### Areas of Success (Code, Organization)

* Logic behind collision events
  * Code for collision events ensures all scenarios are taken into account
* Good organization of code
  * Code is easy to read and understand. Functions are appropriately named

#### Areas for Improvement (Code, Organization)

* Using constructors and prototypes
  * Achieve DRY objective. Some areas that could benefit from this include rendering of objects and collision events
* Separating DOM code from logic portion
  * DOM code can be separated from the logic portion of the js file. For example,    
  `var resetButton = document.querySelector('button')
  resetButton.addEventListener('click', function () {
    location.reload()
  })`

## Additional Notes

* Creative and engaging game. Nice touch with the background music and audio
* Good use of Skeleton to structure the page
* Neat code for both HTML and CSS
