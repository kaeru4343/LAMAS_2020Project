---
layout: default
title: "Battleships - An Epistemic Logic Representation"
---

# Introduction

Battleships is a strategy type guessing game for two players that originally came out as pen and paper game in the 1930s and, later, in 1973, as a plastic board game.

The game created a multitude of spin-offs in various formats, including electronic versions, video games and even phone apps. Every version generally respects the core idea of the game, but will sometimes deviate in execution or rules.<br />
For the sake of simplicity, we will be using the game's default rules and a abridged version of its components in our attempt to model the game in an epistemic logic system.

# Rules and Components

As stated before, this is a game for two players.<br />
Each player has a grid of 10x10 that only they can see, pegs to mark an opponent's hits and misses and a number of ships of varying lengths and 1 width.<br />
Various versions of the game have a different numbers of ships, but the default version has:
*   1 Carrier, which has length 5, 
*   1 Battleship, which has length 4, 
*   1 Cruiser, which has length 3, 
*   1 Submarine, which has length 3 and 
*   1 Destroyer, which has length 2. 

For our abridged version, we will be using a 6x6 grid with the following ships:
*   1 Battleship, 
*   1 Cruiser and 
*   1 Destroyer.

The game is played as follows:

At the start, each party places down their ships without the knowledge of the opponent. They can place their ships wherever they want on their grid as long as the ships are either vertical or horizontal and they do not intersect other ships.<br />
Afterwards, the first round starts. During a round, the players each take a turn to attack a slot on the opponent's board. During an attack, they specify the coordinates they want to check, for example A-5(first row, fifth column), and after this announcement, the opposing player has to announce if the attempt was a hit or a miss and mark it on their grid accordingly.<br />
Then the other player does the same. The round ends and the next round begins. If all of the slots that a ship spans are hit, then the ship is considered to have "sunk" and the player to whom that ship belonged must announce that that particular kind of ship has been sunk.<br />
The rounds keep repeating until the ships of either one of the players, or of both (as the round ends after both players have taken a shot, this is possible), have been sunk.<br />
This concludes the rules the rules of the game.

# Epistemic Logic Conversion
Starting from the two competeting players, it is clear that we can simply transform them into agents and as such, we will have A<sub>1</sub> and A<sub>2</sub>.<br />
From there, each player has a board they know, so we have B<sub>1</sub> for the board of agent 1 and B<sub>2</sub> for the board of the second player.<br /> 
Since they know their own boards we have K<sub>1</sub>B<sub>1</sub> and K<sub>2</sub>B<sub>2</sub>, which roughly translates to agent 1 knows board 1 and agent 2 knows board 2.<br />
Thus, the game ends when C B<sub>1</sub> and/or C B<sub>2</sub>, which roughly translateds to board 1 is common knowledge and/or board 2 is common knowledge, or, in other words, it ends when the board of at least one player becomes common knowledge.<br /> 
A board becomes common knowledge when the status of all of the slots on it are common knowledge. The status of the slots is that there either is a ship on the slot or there is no ship on the slot.<br /> 
To transform this in epistemic logic, if B<sub>m</sub> sh<sub>ij</sub> means that there is a ship at position ij on board m, then we have B<sub>m</sub> &not; sh<sub>ij</sub> which means that there isn't a ship at position ij on board m, where, in our case, i &isin; {A, B, C, D, E, F}, j &isin; {1, 2, 3, 4, 5, 6} and m &isin; {1,2}.<br />
Since K<sub>1</sub>B<sub>1</sub> and K<sub>2</sub>B<sub>2</sub>, then K<sub>1</sub> B<sub>1</sub>sh<sub>ij</sub> and K<sub>2</sub> B<sub>2</sub>sh<sub>ij</sub> where ij are the slots that ships occupy and K<sub>1</sub> B<sub>1</sub> &not; sh<sub>ij</sub> and K<sub>2</sub>B<sub>2</sub> &not; sh<sub>ij</sub> where ij are the slots that are empty.<br />
From the previous fact and the fact that the game ends when at least one of the boards becomes common knowledge, we can re-write the condition as being C B<sub>m</sub>sh<sub>ij</sub> where m is either of the boards and ij are the slots where there are ships and C B<sub>n</sub> &not; sh<sub>kl</sub> where n is the same as m and kl are the slots that are empty.<br />

That covers the part about the board and the location of the ships, but there is another parallel set of knowledge that needs to be taken into account and that is knowledge about the ships themselves.<br />
In general, it is common knowledge what kinds of ships each player has and their length and, to be more specific, in our case, it is common knowledge that each player has 1 ship of length 4, 1 ship of length 3 and 1 ship of length 2.<br />
We will translate that in epistemic as C ship<sub>i</sub>, where i is the number of the ship (i &isin; {1, 2, 3}), in other words, the ships are common knowledge, and C len<sub>j</sub> ship<sub>i</sub>, where j is the length of the ship i, in other words, the lengths of the ships are common knowledge. These will act like axioms in this system. <br />
The game also involves the sinking of the ships. Looking at it practically, a ship sinks once all of the slots it takes are hit. Since we've modelled hits as knowledge about ships being in a slot or not, we can model a ship sinking as its position becoming common knowledge. As such, we need a separate way to mark knoweldge about the positions of the ships. So we definte K<sub>i</sub> pos ship<sub>ij</sub>, where i is the number of the agent (i &isin; {1, 2}) and j is the number of the ship (j &isin; {1,2,3}).<br />
Because of the previous definition and the fact that each player knows where their ships are, we get K<sub>1</sub> pos ship<sub>11</sub>, K<sub>1</sub> pos ship<sub>12</sub>, K<sub>1</sub> pos ship<sub>13</sub>, K<sub>2</sub> pos ship<sub>21</sub>, K<sub>2</sub> pos ship<sub>22</sub> and K<sub>2</sub> pos ship<sub>23</sub>. <br />
Upon the position of all ships of one player becoming common knowledge, it leads to the board becoming common knowledge, because now all of the empty positions are common knowledge as well. In an epistemic logic form, this would mean that (C pos ship<sub>11</sub> and C pos ship<sub>12</sub> and C pos ship<sub>13</sub>) \implies C B<sub>1</sub> or (C pos ship<sub>21</sub> and C pos ship<sub>22</sub> and C pos ship<sub>23</sub>) \implies C B<sub>2</sub>.

The last thing left to translate into epistemic logic, is the way the game is played. And this could be done as a series of anouncements. When one player wants to "attack" a position, they can simply state that they do not know the status of a certain slot. In other words, it can be translated to &not; K<sub>l</sub> B<sub>m</sub> sh<sub>ij</sub>, where l is the attacking agent, m is the board of the oponent and ij is the position in question. This in turn will prompt an announcement from the opponent that they know that the slot is either empty or has a ship on it. In other words, the reply would look something like K<sub>o</sub> B<sub>m</sub> &not; sh<sub>ij</sub> or K<sub>o</sub> B<sub>m</sub> sh<sub>ij</sub>, where o is the other agent, m, i and j are the same as in the previous annoncement and the negation depends on the actual true status of the board in question. This will result in C B<sub>m</sub> &not; sh<sub>ij</sub> or C B<sub>m</sub> &not; sh<sub>ij</sub>, depending on if the slot is actually empty or not. On top of that, it will result in another announcement if all of the slots of a ship were found, which is &not; K<sub>l</sub> K<sub>l</sub> pos ship<sub>op</sub>, where l is the attacker, o is the one getting attacked and p is the number of the discovered ship, and it roughly translates into "you don't know it, but you now know the position of my ship p.". After this announcement, the position becomes common knowledge, which would look as follows in epistemic logic: C pos ship<sub>op</sub>, with the variables having unchanged values from before.<br />
As stated before, once the positions of all 3 ships of a player become common knowledge, the game ends.<br />

# Example of an Epistemic Logic Playthrough

# Discussion





