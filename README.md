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

This is the documentation for the REST API.

* `GET` `/dice` this is our dice which decides who starts the game
* `GET` `/game` keeps the game logic
* `GET` `/game/{game_id}` represents a game. Many games may run concurrently.
* `GET` `/game/{game_id}/board` represents a game's board.
* `GET` `/game/{game_id}/player/{player_id}` represents a player inside a game.
* `POST` `/game/{game_id}/turn` the endpoint where the players send their turns.
* `POST` `/game/{game_id}/turn/deploy` is where players deploy a ship, until
   a player has nothing left to deploy and starts firing at ships
* `POST` `/game/{game_id}/turn/fire` fires on the opponents ships. This is only
  possible when every ship has been deployed
* `GET` `/leaderboard` keeps the persistent leaderboard logic

The `hacking` folder has sample data to illustrate the APIs payload.

## Goals and Ideas

* Work test-driven using the py.test framework
* Create a modular API as a game engine, to be frontend-agnostic  
  and which communicates using json messages
* Maybe: Persist on disk using sqlite and `SQLAlchemy`?
* Follow PEP8 and other good advices
* Create Bots which can play the game autonomously against themselves  
  or human opponents

## Links

* http://de.battleship-game.org
