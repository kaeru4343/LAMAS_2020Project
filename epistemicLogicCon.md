---
layout: default
title: "Battleship <br/> An Epistemic Logic Representation"
description: "Epistemic Logic Conversion"
theme: jekyll-theme-cayman
---

# Epistemic Logic Conversion

Starting from the two competing players, it is clear that we can simply transform them into agents and as such, we will have A<sub>1</sub> and A<sub>2</sub>.

From there, each player has a board they know, so we have B<sub>1</sub> for the board of agent 1 and B<sub>2</sub> for the board of the second player.

Since they know their own boards we have K<sub>1</sub>B<sub>1</sub> and K<sub>2</sub>B<sub>2</sub>, which roughly translates to agent 1 knows board 1 and agent 2 knows board 2.

Thus, the game ends when C B<sub>1</sub> and/or C B<sub>2</sub>, which roughly translated to board 1 is common knowledge and/or board 2 is common knowledge, or, in other words, it ends when the board of at least one player becomes common knowledge.<br /> 
A board becomes common knowledge when the status of all of the slots on it are common knowledge. The status of the slots is that there either is a ship on the slot or there is no ship on the slot.

To transform this in epistemic logic, if B<sub>m</sub> sh<sub>ij</sub> means that there is a ship at position ij on board m, then we have &not; B<sub>m</sub> sh<sub>ij</sub> which means that there isn't a ship at position ij on board m, where, in our case, i &isin; {A, B, C, D, E, F}, j &isin; {1, 2, 3, 4, 5, 6} and m &isin; {1,2}.

Since K<sub>1</sub>B<sub>1</sub> and K<sub>2</sub>B<sub>2</sub>, then K<sub>1</sub> B<sub>1</sub>sh<sub>ij</sub> and K<sub>2</sub> B<sub>2</sub>sh<sub>ij</sub> where ij are the slots that ships occupy and K<sub>1</sub> &not; B<sub>1</sub> sh<sub>ij</sub> and K<sub>2</sub>&not; B<sub>2</sub> sh<sub>ij</sub>, where ij are the slots that are empty.

From the previous fact and the fact that the game ends when at least one of the boards becomes common knowledge, we can re-write the condition as being *C B<sub>m</sub>sh<sub>ij</sub>* where m is either of the boards and ij are the slots where there are ships and C &not; B<sub>n</sub> sh<sub>ij</sub> where n is the same as m and kl are the slots that are empty.

That covers the part about the board and the location of the ships, but there is another parallel set of knowledge that needs to be taken into account and that is knowledge about the ships themselves.<br />
In general, it is common knowledge what kinds of ships each player has and their length and, to be more specific, in our case, it is common knowledge that each player has 1 ship of length 4, 1 ship of length 3 and 1 ship of length 2.

We will translate that in epistemic as C ship<sub>i</sub>, where i is the number of the ship (i &isin; {1, 2, 3}), in other words, the ships are common knowledge, and C len<sub>j</sub> ship<sub>i</sub>, where j is the length of the ship i, in other words, the lengths of the ships are common knowledge. These will act like axioms in this system.

The game also involves the sinking of the ships. Looking at it practically, a ship sinks once all of the slots it takes are hit. Since we've modelled hits as knowledge about ships being in a slot or not, we can model a ship sinking as its position becoming common knowledge. As such, we need a separate way to mark knowledge about the positions of the ships. So we define K<sub>i</sub> pos ship<sub>ij</sub>, where i is the number of the agent (i &isin; {1, 2}) and j is the number of the ship (j &isin; {1,2,3}).<br />
Because of the previous definition and the fact that each player knows where their ships are, we get: <br />
K<sub>1</sub> pos ship<sub>11</sub>, K<sub>1</sub> pos ship<sub>12</sub>, K<sub>1</sub> pos ship<sub>13</sub>, K<sub>2</sub> pos ship<sub>21</sub>, K<sub>2</sub> pos ship<sub>22</sub> and K<sub>2</sub> pos ship<sub>23</sub>.

Upon the position of all ships of one player becoming common knowledge, it leads to the board becoming common knowledge, because now all of the empty positions are common knowledge as well. In an epistemic logic form, this would mean that:

(C pos ship<sub>11</sub> &and; C pos ship<sub>12</sub> &and; C pos ship<sub>13</sub>) &rarr; C B<sub>1</sub> <br/>
&or;<br/>
(C pos ship<sub>21</sub> &and; C pos ship<sub>22</sub> &and; C pos ship<sub>23</sub>) &rarr; C B<sub>2</sub>.

The last thing left to translate into epistemic logic, is the way the game is played. And this could be done as a series of announcements. When one player wants to "attack" a position, they can simply state that they do not know the status of a certain slot. In other words, it can be translated to &not;K<sub>l</sub> B<sub>m</sub> sh<sub>ij</sub>, where l is the attacking agent, m is the board of the opponent and ij is the position in question.

This in turn will prompt an announcement from the opponent that they know that the slot is either empty or has a ship on it. In other words, the reply would look something like K<sub>o</sub> &not; B<sub>m</sub> sh<sub>ij</sub> or K<sub>o</sub> B<sub>m</sub> sh<sub>ij</sub>, where o is the other agent, m, i and j are the same as in the previous announcement and the negation depends on the actual true status of the board in question.

This will result in C &not; B<sub>m</sub> sh<sub>ij</sub> or C B<sub>m</sub> sh<sub>ij</sub>, depending on if the slot is actually empty or not. On top of that, it will result in another announcement if all of the slots of a ship were found, which is K<sub>o</sub> pos B<sub>m</sub> sh<sub>i<sub>1</sub>j<sub>1</sub></sub>... &and; B<sub>m</sub> sh<sub>i<sub>n</sub>j<sub>n</sub></sub> &rarr; K<sub>o</sub> ship<sub>op</sub>, where o is the one getting attacked, p is the number of the discovered ship, and the numbers from 1 to n representing all of the locations of the components of the ship.This roughly translates into "Since I know the location of all of the ship parts it implies that I know where the ship is.".

After this announcement, the position becomes common knowledge, which would look as follows in epistemic logic: C pos ship<sub>op</sub>, with the variables having unchanged values from before.
As stated before, once the positions of all 3 ships of a player become common knowledge, the game ends.

<b>Formalizing the logic system</b>

Assume we have two agents, A<sub>1</sub> and A<sub>2</sub>, and a Kripke model M = <S,&#960;,R<sub>1</sub>, R<sub>2</sub>>, where S is all of the possible states: S={s<sub>(A,1,1)</sub>,s<sub>(A,2,1)</sub>, ..., s<sub>(A,6,1)</sub>, s<sub>(B,1,1)</sub>, ..., s<sub>(G,6,1)</sub>,s<sub>(A,1,2)</sub>, ..., s<sub>(G,6,2)</sub>}, where x &isin;(A, B, ..., G) and y &isin; (1, 2, ..., 6) represent the coordinates on the board in s<sub>(x,y,b)</sub> and b represents the board ownership (1 for A<sub>1</sub> and 2 for A<sub>2</sub>).

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

The game consists of rounds and each round consists of one action from each agent. The agents can only do one action, which in turn will prompt at least one reaction, at most two, from the other agent. These actions and reactions will take the shape of announcements. The agent whose turn it is now will announce "&not;K<sub>i</sub> p<sub>Ship</sub>(x,y,b)", where i is the number of the acting agent and x and y are coordinates on the grids, which translates into "I do not know if a ship is at (x,y,b)". The opposing agent has to reply with the fact that there is or isn't a ship on that slot. In other words, the reply would be as follows: "K<sub>j</sub> p<sub>Ship</sub>(x,y,b)" in case there is a ship there or "K<sub>j</sub> &not;p<sub>Ship</sub>(x,y,b)" in case there is no ship there, where j here stands for the number of the opposing agent, which would translate into "I know there is a(or no, in case not) ship at (x,y,b)". Assuming that all of the positions of a ship have been discovered with that announcement, agent j has to make another announcement:  "K<sub>j</sub> p<sub>Ship</sub>(x<sub>1</sub>,y<sub>1</sub>,b) &and; ... &and; K<sub>j</sub> p<sub>Ship</sub>(x<sub>n</sub>,y<sub>n</sub>,b) &rarr; K<sub>j</sub> p<sub>Ship<sub>j,k</sub></sub>", where k is the number of the discovered ship, with respect to the ships that are common knowledge, which would roughly translate into "Since I know the positions that this ship is on, I know where my ship k is.".

Assuming we had M &#8871; &not;K<sub>i</sub> p<sub>Ship</sub>(x,y,b) by applying the first reply announcement, we get M' &#8871; [K<sub>j</sub> p<sub>Ship</sub>(x,y,b)] C p<sub>Ship</sub>(x,y,b). That is the scenario when a ship is there. The same is true if a ship is not there, only for the negation of p<sub>Ship</sub>(x,y,b) instead.

Assuming we had M &#8871; &not;K<sub>i</sub> p<sub>Ship<sub>i,j</sub></sub> by applying the second reply announcement, we get M' &#8871; <K<sub>j</sub> p<sub>Ship</sub>(x<sub>1</sub>,y<sub>1</sub>,b) &and; ... &and; K<sub>j</sub> p<sub>Ship</sub>(x<sub>n</sub>,y<sub>n</sub>,b) &rarr; K<sub>j</sub> p<sub>Ship<sub>j,k</sub></sub>> C p<sub>Ship<sub>j,k</sub></sub>.

There are a few more actions agents can take, but to showcase them properly, we need to go in more detail. All of these actions can be seen in the example playthrough that follows [Link](./example_play.html).

To specify one more time, once all three ships of at least one player become common knowledge, the game ends.

[Back](./)
