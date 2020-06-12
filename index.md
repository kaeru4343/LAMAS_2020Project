---
layout: default
title: "Battleship <br/> An Epistemic Logic Representation"
description: "By Catalin Flaviu Berki & Kenichi Furusawa"
---
<ul>
  <li>[Home](./)</li>
  <li>[Rules and Components](./rulesComponents.html)</li>
  <li>[Epistemic Logic Conversion](./epistemicLogicCon.html)</li>
  <li>[Playthrough Example](./example_play.html)</li>
  <li>[Strategies](./strategy.html)</li>
  <li>[Game Variant](./Variant.html)</li>
</ul>

# Introduction

Battleship is a strategy type guessing game for two players that originally came out as pen and paper game in the 1930s and, later, in 1973, as a plastic board game.

The game created a multitude of spin-offs in various formats, including electronic versions, video games and even phone apps. Every version generally respects the core idea of the game, but will sometimes deviate in execution or rules.<br />
For the sake of simplicity, we will be using the game's default rules and an abridged version of its components in our attempt to model the game in an epistemic logic system.

# Rules and Components
The rules of the game are explained in-depth [here](./rulesComponents.html).<br/>

In summary, the game consists of 2 players, their individual boards (in our version, they are a grid of 6x6 each) and their ships (in our version, there are 3 ships of sizes 4x1,3x1 and 2x1). They only know the positions of their own ships and must guess the positions of the oponent's ship. A game is played with rounds and each round consists of a turn of attacking for each player. The game ends when all of the ships are sunk/become common knowledge.

# Epistemic Logic Conversion
[Here](./epistemicLogicCon.html) we show how epistemic logic can be used to model agents knowledge and the game itself.

In summary, &#x2112;<sub>KC</sub><sup>stat</sup>(A,P) is defined as a union of the formula and epistemic actions. The game ends when one agent's board becomes common knowledge among the agents, impling that everyone knows the position of the ships on the board. The owner of the board which became common knoweldge loses the game. 

# Example of an Epistemic Logic Playthrough
You can follow a complete playthrough of the game in this epistemic logic system [here](./example_play.html).

# Strategies
There are ways in which an individual can play such that they maximize their chances of winning. We discuss this aspect of the game [here](./strategy.html).

# Discussion
The idea of modelling the game of Battleship can lead to a multitude of avenues for future research. An example of this would be analyzing the game, but from a game theory point of view, focusing on potential ways of optimization gameplay. Another avenue of research would be attempting to model a well-known, harder version of the game known as "Salvo Battleship". In that version of the game, each turn each player attacks a number of slots equal to their number of unsunk ships in a "salvo" instead of attacking one slot at a time. The opponent will only tell them how many out of those attacks were hits and leaves it to them to piece the rest of the information together. Of course, the players still need to announce when a ship was sunk. Obviously, this would be significantly harder to model and could lead to interesting behaviours in and of itself.<br/>
Alternatively, future researchers could attempt to make additional rules, for example, ships could only be placed vertically, or remove rules, for example, they could remove the announcement of a hit, but keep the announcement of a ship sinking, which could result in interesting behaviour once more. We attempt to detail such an approach [here](./Variant.html).<br/>
Finally, one more topic that could be worth looking into was the introduction of untruthful statements in the equation. The game would be changed drastically if a rule that states that each player could lie about a hit occuring or not occuring 3 times in a match. This would lead to all sorts of interesting tactics as well as to the inclusion of risk management into the game. On the other hand, a match could also even become unplayable if players are untruthful about ships sinking, so it would be best not to take it that far.



