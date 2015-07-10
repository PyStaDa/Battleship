# Battleship
This is a RESTful Webservice which provides the backend to play the famous battleship guessing game over HTTP

## Rules

Rules for battleship to be implemented in the API.

### The Map

Each player has a dedicated map. The map has a size of 10x10 quadrants.

### How to place ships

* Ships are build from squares which are connected in a straight line only
* Ships must not touch each other
* Each player has to place 10 ships
  * 1 Battleship (5 squares)
  * 2 Cruiser (4 squares)
  * 3 Destroyer (3 squares)
  * 4 Submarines (2 squares)

### Course of the game

* Toss a coin to find out which player starts the game
* When the player hits a ship, it is marked as "hit" and
  he may continue to attack
* When a player does not hit a ship, it's his opponent's turn

The game ends when one player lost all his or her ships.

## RESTful API

The API is modeled after http://tools.ietf.org/html/rfc6570 .  
The result can be directly used with the falcon framework http://falcon.readthedocs.org.

### Resources

* `/api/v1/`

## Goals

* Create a modular API as a game engine, to be frontend-agnostic
  which communicates using json messages
* Maybe: Persist on disk using sqlite and `SQLAlchemy`?
* Work test-driven (`pytest`?)
* Follow PEP8 and other good advices

## Links

* http://de.battleship-game.org
