# Ayan-s-Rookgame
**INTRODUCTION:**
Welcome to the Rook Game, a thrilling 1v1 chess-inspired challenge where  thinking and quick decision-making are the keys to victory!
In this fast-paced game, players navigate an 8x8 chessboard, guiding their rook pieces to race to the bottom-left corner before their opponent does.
Let the battle of wits begin!


**RULES TO PLAY**
Objective: The goal of the game is to reach the bottom-left corner of the 8x8 chessboard before your opponent.

Starting Position: Players begin with their rook pieces at the top-right corner of the chessboard.

Moves: On each turn, a player can move their rook any number of steps to the left or down. Diagonal moves and movements in other directions are not allowed.

Multiplayer Gameplay: This game supports real-time multiplayer functionality. Players can connect and compete against each other in real-time matches.

Turn Timer: Each player has 30 seconds to make their move. If a player fails to make a move within the allocated time, the game ends, and their opponent wins.

Victory: The first player to reach the bottom-left corner of the chessboard wins the game and is declared the ultimate Rook Move champion!


**BACKEND**
Node.js - JavaScript runtime environment

Express.js - Web application framework

MongoDB - NoSQL database (I have used MongoDB Atlas for cloud hosting)

Socket.io - Real-time communication library

TypeScript - Programming language with static typing



**INSTALLATION**
Clone the repository : git clone https://github.com/Ayankhader/Ayan-s-Rookgame.git

Install the packages : npm install

Run the server : npm start


**PROJECT STRUCTURE**
- src
   - controllers
        - gameController.ts : Contains all the controller functions
    - models
        - Game.ts : Contains the game model
    - routes
        - gameRoutes.ts : Contains all the routes
    - constants.ts : Constants used in the project
    - db.ts : Database connection
    - index.ts : Entry point of the server
- .env.example : Example .env file



**SOCKET EVENT HANDLERS**

**1.socket.on("disconnect"):**

Updates the game state if a player disconnects.

If the game is completed or the disconnected player is the only one in the game, there might not be any specific output to the clients.

If the game is ongoing and the player disconnects, it updates the game state and emits "game-ended" event to both players with the updated game state.

**2.socket.on("join-game"):**

If the game is not found: Emits "game-not-found" event to the socket.

If the game is already completed: Emits "game-ended" event to the socket with the updated game state.

If the game is already full: Emits "already-busy" event to the socket.

If the player successfully joins the game: Emits "start-game" event to both players' sockets with the updated game state.

**3.socket.on("rook-moved"):**

Emits "update-rook-position" event to the opponent's socket with the new rook position

if the move is valid and updates the game state.

If the rook reaches the specified position, it updates the game state and emits "game-ended" event to both players with the updated game state.

**4.socket.on("timer-ended")Event:**

Emits "you-win" event to the opponent's socket with the updated game state if the timer ends and the game is not completed.

If the game is already completed, there might not be any specific output to the clients.

If the game is not found or the player is not found, it emits "game-not-found" or "already-busy" event, respectively.



**SOCKET EMITTED EVENTS**

**1. socket.emit("game-not-found") :**
   
Sent to a specific client when the requested game is not found in the database.

The client can handle this event to display an error message to the user, indicating that the requested game was not found.

**2. socket.emit("game-ended", game) :**
   
Sent to both players' sockets when a game is completed. 
The game object contains updated game state information, including the winner, reason for game completion, and possibly other relevant details. Both clients can handle this event to display the game result to the players.

**3. socket.emit("already-busy") :**
   
Sent to a specific client when a player attempts to join a game that is already full (both player slots are occupied).

The client can handle this event to inform the user that the game is already in progress and both player slots are taken.

**4. socket.emit("start-game", game) :**
   
Sent to both players' sockets when a game is successfully started. The game object contains initial game state information, allowing both clients to set up the game interface and display the initial game state to the players

**5. socket.emit("update-rook-position", { rookRow, rookCol }) :**
   
Sent to the opponent's socket when a player moves their rook on the game board. The { rookRow, rookCol } object contains the new position of the rook.

The opponent client can handle this event to update the rook's position on their game board interface.

**6. socket.emit("you-win", game) :**

Sent to the winning player's socket when the game is completed.

The game object contains updated game state information, including the winner, reason for game completion, and possibly other relevant details. The winning player's client can handle this event to display a winning message and the game result


**PROJECT MOTIVATION:**


The motivation behind this project was driven by a unique opportunity presented by the Cuemath team. Tasked with the challenge as part of Cuemath's game developer hiring process, the project served as a practical assessment of my skills and creativity. Success in this endeavor not only represented a chance to showcase my abilities but also the prospect of joining a forward-thinking team at Cuemath. The project, therefore, became a compelling avenue to prove my  passion, and suitability for the role, motivating me to deliver this ,seeking forward to join and learn more in cuemath



**FUTURE ENCHANCEMENT**


User Authentication: Implementing user authentication to allow users to create accounts and track their game history.

Leaderboard: Creating a leaderboard to display the top players and their rankings.

Game listing: Creating a game listing page where users can view the ongoing games and join a game of their choice.

Tournament Mode: Implementing a tournament feature where players can compete in structured tournaments.

AI Opponent: Developing an AI opponent for single-player mode, allowing users to practice and enhance their skills


