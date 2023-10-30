# Strategy Game

"Strategy" is an [open source](https://git.kerrishaus.com/strategy) turn based strategy game. The game is named "Strategy" because naming things is hard.

# How to play

This is a turn based strategy game. Each player has one turn, with a configurable amount of time per turn.

# Multiplayer

Multiplayer for this game is based on the websocket technology, so that users are not required to port foward to play together. By default, the game connects to the websocket server hosted by Kerris Haus at `wss://wss.kerrishaus.com/games/strategy`. The client does not connect until a user has selected multiplayer, thus offline play is perfectly possible so long as all assets have been downloaded.

You can use your own websocket server software if you want to, and you can build on top of ours if you want. You can find the server software [here](https://git.kerrishaus.com/strategy-server)