# **Card Clash \- Server**

This is the **server-side** of **Card Clash**, powering real-time multiplayer card battles for up to 10 players. Built with Node.js and Socket.IO, it manages game state, card picks, and chat. Deployed at [https://cardclash-server-w935.onrender.com](https://cardclash-server-w935.onrender.com/). Clone to contribute or run locally\!

## **🎮 Game Overview**

The server supports **Card Clash**, where players pick from a 30-card deck (25 valued 1-25, 4 valued 30, 1 valued 50\) to outscore opponents. It handles game creation, player joins, card shuffling, and eliminations, syncing all actions in real-time.

## **🧠 AI Techniques Used**

* **Randomized Card Shuffling**: Fisher-Yates algorithm (`shuffleArray`) ensures fair card distribution.  
* **Automated Card Assignment**: Auto-assigns cards for missed turns (`autoAssignCard`), using random selection from unpicked cards.  
* **Leaderboard Calculation**: Sorts players by score (`calculateLeaderboard`), with pick-time tiebreakers.  
* **Game Cleanup**: Removes games older than 24 hours to manage resources.

## **⚙️ Game Mechanics**

### **Scoring System**

* **Card Values**: 25 cards (1-25), 4 cards (30), 1 card (50).  
* **Scoring**: Players pick one card per round, adding its value to their score.  
* **Tiebreakers**: Slowest picker in a lowest-score tie is eliminated.

### **AI Behaviors**

* **No NPCs**: All actions are player-driven.  
* **Automation**: Handles turn timers, auto-assignments, and game state transitions (lobby, playing, ended).

### **Level Progression**

* **Rounds**: Players pick in turn; lowest scorer is eliminated.  
* **Turn Order**: Leaderboard-based (highest score first).  
* **Endgame**: Last player is champion, or no winner if all eliminated.

## **🛠️ Technical Details**

### **Tech Stack**

* **Node.js \+ Express**: Lightweight server framework.  
* **Socket.IO Server**: Real-time communication for events (`createGame`, `pickCard`).  
* **In-Memory Storage**: `Map` for game state and timers.  
* **Crypto**: Generates 6-character game codes (e.g., ABC123).

### **Architecture**

* **Real-Time Sync**: Socket.IO broadcasts updates (e.g., card picks, eliminations).  
* **Scalability**: Supports 10 players per game, with cleanup for stale games.  
* **Security**: CORS restricts to trusted origins (e.g., `https://cardclash.vercel.app`).

## **🚀 Getting Started**

### **Prerequisites**

* Node.js (v16+)  
* npm or yarn  
* Git

### **Installation**

Clone the server repo:

 git clone https://github.com/muzecaka/cardclash-server.git  
cd cardclash-server

1. 

Install dependencies:

 npm install

2. 

Set up environment variables (create `.env`):

 PORT=3001  
CLIENT\_URL=[http://localhost:3000](http://localhost:3000), https://cardclash.vercel.app

3. 

Run the server:

 npm start

4. 

*Note*: Requires the client running (see [cardclash repo](https://github.com/muzecaka/%5Bcardclash%7Csign-cardclash%5D)).

## **🤝 Contributing**

1. Fork the repo.  
2. Create a feature branch (`git checkout -b feature/YourFeature`).  
3. Commit changes (`git commit -m "Add YourFeature"`).  
4. Push (`git push origin feature/YourFeature`).  
5. Open a Pull Request.

## **📜 License**

MIT License. Include the copyright notice (“Card Clash by @muzecaka”) in derivatives.

*Note*: This project is licensed under the MIT License. If you create a derivative game, please include the original copyright notice (“Card Clash by @muzecaka”) as required.

## **🙌 Acknowledgments**

* By [MUZE CAKA](https://github.com/muzecaka)     
* X  [@muzecaka](https://github.com/muzecaka).  
* Discord [KanmiNFT](https://discord.com/invite/kanminft).

