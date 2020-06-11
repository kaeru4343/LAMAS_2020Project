# Strategies  

In order for an agent to win the game, one way is to place the ship in such a way that it is hard to other agents to limits model. Or find out about the other agents position faster than the other agent.  

<b> Positions </b>
When placing the ships, one is better to avoid placing the ship on edges such as (A,6),(A,1),(F,1),(F,6). This is because if the agent is attacks on these potision, the agent has succesed in limiting the model into smaller model than other hit situation.
Formally, edge &isin; {(A,6),(A,1),(F,1),(F,6)} and K<sub>i</sub> p<sub>Ship</sub>edge, "Agent i knows that there is a ship on edge". From the rules, there are only two possible direction that is allowed, since, for example in case of edge = (A,6) K<sub>i</sub> p<sub>Ship</sub>(A,6) &rarr; K<sub>i</sub>(p<sub>Ship</sub>(A,5) &or; p<sub>Ship</sub>(B,6)) only and otherwise they are out of bound. This implies that within at most next two steps, the ship's orientation is found and within next (size of ship)-2 steps, the ship is sunk. The number of step required for sinknig in this situation is minimal for all ships' size in the most oppimistic situation (agents guesses the wrong directions until there is only one option) since if the ship is placed within (B~E,2~5) there are 4 possiblities states availbe after hit and 3 possible states for sides posisiton excluding edges. 


<b> Attacking </b>
When attacking/announcing the grid to find out about the other agents posision, attacking on the edges are only prefered if and only the agent i knows that agent i will know that there is a ship, K<sub>i</sub>K<sub>i</sub>p<sub>Ship</sub>edge. This is because from the positioning strategy, agents know that it is unlikely for a ship positioned on the edge. 
Also &not;p<sub>Ship</sub>edge can be known by attacking two side of a edge. Attacking of two side of edge is preferred since this can leads to kwonwing three posisiton in 2 steps. For example, in two step agent i models, K<sub>i</sub>&not;p<sub>Ship</sub>vertical_edge &and; K<sub>i</sub>&not;p<sub>Ship</sub>horizonal_edge &rarr; K<sub>i</sub>&not;p<sub>Ship</sub>edge. Therefore, information gain is more efficient in the best case.  
If it is not base case, then infromation gain is as good as the attacking other side positions. 


