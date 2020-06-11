---
layout: default
title: "Battleship - An Epistemic Logic Representation"
nav_order: 4
---

# Introduction

Battleship is a strategy type guessing game for two players that originally came out as pen and paper game in the 1930s and, later, in 1973, as a plastic board game.

The game created a multitude of spin-offs in various formats, including electronic versions, video games and even phone apps. Every version generally respects the core idea of the game, but will sometimes deviate in execution or rules.<br />
For the sake of simplicity, we will be using the game's default rules and an abridged version of its components in our attempt to model the game in an epistemic logic system.

# Rules and Components
The rules of the game are expalined here [Link](./rulesComponents.html).<br/>
In summary, there are three ships with diffreren shape and they are placed on 6x6 board without comminucating the posistion bewteen the agents and the task is find out where the ships are on the other agent's board. 

# Epistemic Logic Conversion
Here we shows that epistemic logic can be used to model agents knowledge in the game[Link](./epistemicLogicCon.html)
In summary, &#x2112;<sub>KC</sub><sup>stat</sup>(A,P) is defined as a union of the formula and epistemic actions and the game ends with one agent's board become a common knowledge among the agents, impling the everyone knows the position of ships on the board. The owner of the board that became common knoweldge loses the game. 

# Example of an Epistemic Logic Playthrough
One example of a game with play through is done here[Link](./example_play.html). 
 
# Discussion
The idea of modelling the game of Battleship can lead to a multitude of avenues for future research. An example of this would be analyzing the game, but from a game theory point of view, focusing on potential ways of optimization gameplay. Another avenue of research would be attempting to model a well-known, harder version of the game known as "Salvo Battleship". In that version of the game, each turn each player attacks a number of slots equal to their number of unsunk ships in a "salvo" instead of attacking one slot at a time. The opponent will only tell them how many out of those attacks were hits and leaves it to them to piece the rest of the information together. Of course, the players still need to announce when a ship was sunk. Obviously, this would be significantly harder to model and could lead to interesting behaviours in and of itself. Alternatively, future researchers could attempt to make additional rules, for example, ships could only be placed vertically, or remove rules, for example, they could remove the announcement of a hit, but keep the announcement of a ship sinking, which could result in interesting behaviour once more.

# Variation of the game 
There are variatons of the game and one is considered here[Link](./Variant.html). 



