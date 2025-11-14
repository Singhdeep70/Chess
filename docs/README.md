# Jaquematic 3000

## Intro

Jaquematic 3000 is an online chess application which was developed as the final project for the Skylab Academy full-stack 'bootcamp'.  It allows an unlimited number of users to play multiple games with each other.  Each user may play with an unlimited number of other users, one game for each pair at a time.  Players may play simultaneously, with moves being updated 'live', or they may play at their convenience, since moves are stored so that they are ready whenever a player logs in.

## Functional description

Jaquematic 3000 allows the chess afficionado to play an unlimited number of chess matches with other online users.  The user searches for other users from within the application and invites one or more to a chess match.  The invited user can accept or reject the invitation.  If the invitation is accepted, the two users start a game -- in this iteration of the application the inviting user plays white.  

Once playing, the players take turns.  Players may play simulataneously, with moves being updated 'live', or may login and play when they desire. Moves are checked for legality, and the user is alerted when they are in check.  The application checks for checkmate, stalemate, 3-repetition draw, lack of sufficient material, etc on each move, and if any of these situations occur the game ends, at which point the players are notified and the game is removed.  This iteration of the application does not permit the game to be reviewed once it has ended, neither may a player resign once a game has started.

## Technical description

The application is a web application that is meant to run within a browser environment. It consists of a ReactJS frontend that connects to with an API that runs on NodeJS.  The API uses ExpressJS to route requests and uses Mongoose to interface with a MongoDB store. The application uses the npm packages Chessboardjsx to handle the chessboard itself and Chess.js for the game engine to convert moves to FEN syntax and to handle rule-checking. 

The application is written in Javascript and takes advantage of ES6 and ESNext Javascript features.

User data is persistent across page reloads, as local data is stored in the user's SessionStorage.  

Styling is handled via SCSS and the application is mobile friendly.

Tests are written in Mocha/Chai.

## Data Models

![](images/chess-data-models.png)

## Basic Architecture

![](images/chess-basic-architecture.png)


## Making A Move: sample communication flow

![](images/chess-make-a-move.png)
 
## Running the project

These are basic instructions to get Jaquematic 3000 running locally for development.

- **Prerequisites**:
	- Node.js (v14 or later recommended) and npm installed. Verify with `node -v` and `npm -v`.
	- MongoDB running locally (or a connection string to a MongoDB Atlas instance).

- **Quick setup (development)**:

	1. Clone the repository and change into the project directory:

		 ```powershell
		 git clone https://github.com/Tushar81940/Chess.git
		 cd Chess
		 ```

	2. Install dependencies for the server and client (if the project is split into `server/` and `client/` folders). From the repository root run:

		 ```powershell
		 npm install
		 # if there are separate packages, also run in subfolders, for example:
		 # cd client; npm install; cd ../server; npm install
		 ```

	3. Configure environment variables. Create a `.env` file in the server directory (or at repo root if applicable) with at least:

		 ```text
		 MONGODB_URI=mongodb://localhost:27017/jaquematic
		 PORT=3000
		 JWT_SECRET=your_secret_here
		 ```

	4. Start MongoDB (skip if using Atlas). For Windows with a service installed:

		 ```powershell
		 net start MongoDB
		 # or use your MongoDB launcher if you installed via MongoDB Compass or another method
		 ```

	5. Start the application in development mode. From the appropriate directory run:

		 ```powershell
		 npm run dev
		 # or, if client and server are separate:
		 # cd server; npm run dev
		 # cd client; npm start
		 ```

- **Build and production**:

	- To build the client for production (if a `client` folder exists):

		```powershell
		cd client
		npm run build
		```

	- Start the production server (configure `NODE_ENV=production` and ensure the server serves built static assets):

		```powershell
		npm start
		```

- **Running tests**:

	```powershell
	npm test
	# or cd server; npm test (adjust according to repo layout)
	```

- **Troubleshooting**:
	- If you see connection errors, verify `MONGODB_URI` and that MongoDB is reachable.
	- If ports are in use, change `PORT` in your `.env` or stop the process using the port.
	- Check console logs in both client and server for error stack traces.

If you'd like, I can tailor these steps precisely to the repository layout (client/server folders, npm scripts names). Tell me whether the project has a `client/` folder, a top-level `package.json`, or any custom start scripts and I'll adapt the README accordingly.

