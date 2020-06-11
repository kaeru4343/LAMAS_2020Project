---
layout: default
title: "Battleship - An Epistemic Logic Representation"
---

# Introduction

Battleship is a strategy type guessing game for two players that originally came out as pen and paper game in the 1930s and, later, in 1973, as a plastic board game.

The game created a multitude of spin-offs in various formats, including electronic versions, video games and even phone apps. Every version generally respects the core idea of the game, but will sometimes deviate in execution or rules.<br />
For the sake of simplicity, we will be using the game's default rules and an abridged version of its components in our attempt to model the game in an epistemic logic system.

# Rules and Components <a href="/rulesComponents.md">

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
This concludes the rules of the game.

# Epistemic Logic Conversion
Starting from the two competing players, it is clear that we can simply transform them into agents and as such, we will have A<sub>1</sub> and A<sub>2</sub>.<br />
From there, each player has a board they know, so we have B<sub>1</sub> for the board of agent 1 and B<sub>2</sub> for the board of the second player.<br /> 
Since they know their own boards we have K<sub>1</sub>B<sub>1</sub> and K<sub>2</sub>B<sub>2</sub>, which roughly translates to agent 1 knows board 1 and agent 2 knows board 2.<br />
Thus, the game ends when C B<sub>1</sub> and/or C B<sub>2</sub>, which roughly translated to board 1 is common knowledge and/or board 2 is common knowledge, or, in other words, it ends when the board of at least one player becomes common knowledge.<br /> 
A board becomes common knowledge when the status of all of the slots on it are common knowledge. The status of the slots is that there either is a ship on the slot or there is no ship on the slot.

To transform this in epistemic logic, if B<sub>m</sub> sh<sub>ij</sub> means that there is a ship at position ij on board m, then we have &not; B<sub>m</sub> sh<sub>ij</sub> which means that there isn't a ship at position ij on board m, where, in our case, i &isin; {A, B, C, D, E, F}, j &isin; {1, 2, 3, 4, 5, 6} and m &isin; {1,2}.<br />
Since K<sub>1</sub>B<sub>1</sub> and K<sub>2</sub>B<sub>2</sub>, then K<sub>1</sub> B<sub>1</sub>sh<sub>ij</sub> and K<sub>2</sub> B<sub>2</sub>sh<sub>ij</sub> where ij are the slots that ships occupy and K<sub>1</sub> &not; B<sub>1</sub> sh<sub>ij</sub> and K<sub>2</sub>&not; B<sub>2</sub> sh<sub>ij</sub> where ij are the slots that are empty.<br />
From the previous fact and the fact that the game ends when at least one of the boards becomes common knowledge, we can re-write the condition as being C B<sub>m</sub>sh<sub>ij</sub> where m is either of the boards and ij are the slots where there are ships and C &not; B<sub>n</sub> sh<sub>ij</sub> where n is the same as m and kl are the slots that are empty.<br />

That covers the part about the board and the location of the ships, but there is another parallel set of knowledge that needs to be taken into account and that is knowledge about the ships themselves.<br />
In general, it is common knowledge what kinds of ships each player has and their length and, to be more specific, in our case, it is common knowledge that each player has 1 ship of length 4, 1 ship of length 3 and 1 ship of length 2.

We will translate that in epistemic as C ship<sub>i</sub>, where i is the number of the ship (i &isin; {1, 2, 3}), in other words, the ships are common knowledge, and C len<sub>j</sub> ship<sub>i</sub>, where j is the length of the ship i, in other words, the lengths of the ships are common knowledge. These will act like axioms in this system. <br />
The game also involves the sinking of the ships. Looking at it practically, a ship sinks once all of the slots it takes are hit. Since we've modelled hits as knowledge about ships being in a slot or not, we can model a ship sinking as its position becoming common knowledge. As such, we need a separate way to mark knowledge about the positions of the ships. So we define K<sub>i</sub> pos ship<sub>ij</sub>, where i is the number of the agent (i &isin; {1, 2}) and j is the number of the ship (j &isin; {1,2,3}).<br />
Because of the previous definition and the fact that each player knows where their ships are, we get: <br />
K<sub>1</sub> pos ship<sub>11</sub>, K<sub>1</sub> pos ship<sub>12</sub>, K<sub>1</sub> pos ship<sub>13</sub>, K<sub>2</sub> pos ship<sub>21</sub>, K<sub>2</sub> pos ship<sub>22</sub> and K<sub>2</sub> pos ship<sub>23</sub>. <br />
Upon the position of all ships of one player becoming common knowledge, it leads to the board becoming common knowledge, because now all of the empty positions are common knowledge as well. In an epistemic logic form, this would mean that:<br />
(C pos ship<sub>11</sub> &and; C pos ship<sub>12</sub> &and; C pos ship<sub>13</sub>) &rarr; C B<sub>1</sub> &or; (C pos ship<sub>21</sub> &and; C pos ship<sub>22</sub> &and; C pos ship<sub>23</sub>) &rarr; C B<sub>2</sub>.

The last thing left to translate into epistemic logic, is the way the game is played. And this could be done as a series of announcements. When one player wants to "attack" a position, they can simply state that they do not know the status of a certain slot. In other words, it can be translated to &not;K<sub>l</sub> B<sub>m</sub> sh<sub>ij</sub>, where l is the attacking agent, m is the board of the opponent and ij is the position in question.<br />
This in turn will prompt an announcement from the opponent that they know that the slot is either empty or has a ship on it. In other words, the reply would look something like K<sub>o</sub> &not; B<sub>m</sub> sh<sub>ij</sub> or K<sub>o</sub> B<sub>m</sub> sh<sub>ij</sub>, where o is the other agent, m, i and j are the same as in the previous announcement and the negation depends on the actual true status of the board in question. <br />
This will result in C &not; B<sub>m</sub> sh<sub>ij</sub> or C B<sub>m</sub> sh<sub>ij</sub>, depending on if the slot is actually empty or not. On top of that, it will result in another announcement if all of the slots of a ship were found, which is K<sub>o</sub> pos B<sub>m</sub> sh<sub>i<sub>1</sub>j<sub>1</sub></sub>... &and; B<sub>m</sub> sh<sub>i<sub>n</sub>j<sub>n</sub></sub> &rarr; K<sub>o</sub> ship<sub>op</sub>, where o is the one getting attacked, p is the number of the discovered ship, and the numbers from 1 to n representing all of the locations of the components of the ship.This roughly translates into "Since I know the location of all of the ship parts it implies that I know where the ship is.".<br /> 
After this announcement, the position becomes common knowledge, which would look as follows in epistemic logic: C pos ship<sub>op</sub>, with the variables having unchanged values from before.<br />
As stated before, once the positions of all 3 ships of a player become common knowledge, the game ends.

<b>Formalizing the logic system</b>

Assume we have two agents, A<sub>1</sub> and A<sub>2</sub>, and a Kripke model M = <S,&#960;,R<sub>1</sub>, R<sub>2</sub>>, where S is all of the possible states: S={s<sub>(A,1,1)</sub>,s<sub>(A,2,1)</sub>, ..., s<sub>(A,6,1)</sub>, s<sub>(B,1,1)</sub>, ..., s<sub>(G,6,1)</sub>,s<sub>(A,1,2)</sub>, ..., s<sub>(G,6,2)</sub>}, where x &isin;(A, B, ..., G) and y &isin; (1, 2, ..., 6) represent the coordinates on the board in s<sub>(x,y,b)</sub> and b represents the board ownership (1 for A<sub>1</sub> and 2 for A<sub>2</sub>).<br /> 
Furthermore, in this model, it is common knowledge that there are 3 ships. Their size is also common knowledge. So we have Ship<sub>1</sub> with length 4,Ship<sub>2</sub>, with length 3, Ship<sub>3</sub> with length 2 and from there C Ship<sub>1</sub>, C Ship<sub>2</sub>, C Ship<sub>3</sub>.

Since we are monitoring two parallel representations, we also have two propositions. They are defined as follows:

p<sub>Ship</sub>(x,y,b) = t iff "A ship is located at coordinates (x,y) on the grid on board b";<br />
p<sub>Ship<sub>i,j</sub></sub> = t iff "All of the coordinates of ship j belonging to agent i are known";

The first preposition is used on the board, while the second is mainly used for announcements.

Now that we've declared our prepositions, we have &#x2112;<sub>KC</sub><sup>stat</sup>(A,P), which is a union of formula and epistemic actions.

We also have:
R<sub>1</sub> = (s<sub>1</sub>(x,y,b),s<sub>1</sub>(x,y,b)) for all (x,y,b) and (s<sub>2</sub>(x,y,b), z<sub>2</sub>(x,y,b) for all z<sub>2</sub> &isin; S and<br />
R<sub>2</sub>  = (s<sub>2</sub>(x,y,b),s<sub>2</sub>(x,y,b)) for all (x,y,b) and (s<sub>1</sub>(x,y,b), z<sub>1</sub>(x,y,b) for all z<sub>1</sub> &isin; S, which means that the relations are reflexive within their own state and all states with the same coordinates for the other agent's board.

<b>Actions</b>

The game consists of rounds and each round consists of one action from each agent. The agents can only do one action, which in turn will prompt at least one reaction, at most two, from the other agent. These actions and reactions will take the shape of announcements. The agent whose turn it is now will announce "&not;K<sub>i</sub> p<sub>Ship</sub>(x,y,b)", where i is the number of the acting agent and x and y are coordinates on the grids, which translates into "I do not know if a ship is at (x,y,b)". The opposing agent has to reply with the fact that there is or isn't a ship on that slot. In other words, the reply would be as follows: "K<sub>j</sub> p<sub>Ship</sub>(x,y,b)" in case there is a ship there or "K<sub>j</sub> &not;p<sub>Ship</sub>(x,y,b)" in case there is no ship there, where j here stands for the number of the opposing agent, which would translate into "I know there is a(or no, in case not) ship at (x,y,b)". Assuming that all of the positions of a ship have been discovered with that announcement, agent j has to make another announcement:  "K<sub>j</sub> p<sub>Ship</sub>(x<sub>1</sub>,y<sub>1</sub>,b) &and; ... &and; K<sub>j</sub> p<sub>Ship</sub>(x<sub>n</sub>,y<sub>n</sub>,b) &rarr; K<sub>j</sub> p<sub>Ship<sub>j,k</sub></sub>", where k is the number of the discovered ship, with respect to the ships that are common knowledge, which would roughly translate into "Since I know the positions that this ship is on, I know where my ship k is.".<br />
Assuming we had M &#8871; &not;K<sub>i</sub> p<sub>Ship</sub>(x,y,b) by applying the first reply announcement, we get M', K<sub>j</sub> p<sub>Ship</sub>(x,y,b) &#8871; C p<sub>Ship</sub>(x,y,b). That is the scenario when a ship is there. The same is true if a ship is not there, only for the negation of p<sub>Ship</sub>(x,y,b) instead.<br />
Assuming we had M &#8871; &not;K<sub>i</sub> p<sub>Ship<sub>i,j</sub></sub> by applying the second reply announcement, we get M', K<sub>j</sub> p<sub>Ship</sub>(x<sub>1</sub>,y<sub>1</sub>,b) &and; ... &and; K<sub>j</sub> p<sub>Ship</sub>(x<sub>n</sub>,y<sub>n</sub>,b) &rarr; K<sub>j</sub> p<sub>Ship<sub>j,k</sub></sub> &#8871; C p<sub>Ship<sub>j,k</sub></sub>. <br />
There are a few more actions agents can take, but to showcase them properly, we need to go in more detail. All of these actions can be seen in the example playthrough that follows. <br />
To specify one more time, once all three ships of at least one player become common knowledge, the game ends.

# Example of an Epistemic Logic Playthrough

<embed src="Logical_Aspects_of_Multi_Agent_Systems_Project_Example_Playthrough.pdf" width="800px" height="2100px" />

# Discussion
The idea of modelling the game of Battleship can lead to a multitude of avenues for future research. An example of this would be analyzing the game, but from a game theory point of view, focusing on potential ways of optimization gameplay. Another avenue of research would be attempting to model a well-known, harder version of the game known as "Salvo Battleship". In that version of the game, each turn each player attacks a number of slots equal to their number of unsunk ships in a "salvo" instead of attacking one slot at a time. The opponent will only tell them how many out of those attacks were hits and leaves it to them to piece the rest of the information together. Of course, the players still need to announce when a ship was sunk. Obviously, this would be significantly harder to model and could lead to interesting behaviours in and of itself. Alternatively, future researchers could attempt to make additional rules, for example, ships could only be placed vertically, or remove rules, for example, they could remove the announcement of a hit, but keep the announcement of a ship sinking, which could result in interesting behaviour once more.

# Variation of the game 
Here we consider a variation of the game. The varinat is that when annoucing the posisitn for an attack, the agents needs to announce its own grid state together with the attack. so the announcement is "&not;K<sub>i</sub> p<sub>Ship</sub>(x,y,b) &and;  p<sub>Ship</sub>(x,y,b)" or "&not;K<sub>i</sub> p<sub>Ship</sub>(x,y,b) &and; &not; p<sub>Ship</sub>(x,y,b)", which translate to "I do not know if a ship is at (x,y,b) and I know that if a ship at (x,y,a)". Then the other agent must reply with the same actions as done before in the normal game. 
Since the agents want to avoid its own ship position to become common knowledge, when attacking, the agents want to expolit the other agents position and hide its own position.  
Then the agents needs make less annoucment which exploits their own position of the ship, p<sub>Ship</sub>(x,y,b). Futhermore, when one position of the ship is known to the other agents, K<sub>i</sub> p<sub>Ship</sub>(x,y,b) and from the common knowledge of the rules, the agent want to avoid attacking position on the surrondings of known position. This avoidane behavior is common knoweldge amongs the agents. 



