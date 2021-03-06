---
layout: default
title: "Battleship <br/> An Epistemic Logic Representation"
description: "Strategies"
theme: jekyll-theme-cayman
---

# Strategies  
In order for an individual to win the game, there are a few steps that can be taken to maximize the odds of that outcome. One such step is to place your ships in such a way that it becomes harder for the opponent to figure it out quickly. Another way to increase your chances of winning is to have a good offensive plan and a systemic approach to finding your opponent's ship before he does.

<b> Positioning </b>

In general, when placing the ships, it is better to avoid placing the ship on the edges and corners (On our grid, in places such as (A,6),(A,1),(F,1),(F,6), which are corners). This is because if the opponent attacks the ships in these positions, there are less adjacent slots (3 slots for normal edges and only 2 for corners, compared to 4 for non-edges) that could house ships, so statistically, they have a higher chance of guessing the location of the connected pieces in less turns than if they weren't located on edges. This problem is even more pronounced in the corner slots, as the opponent has a 50% chance of finding the location of the next ship part the next turn and 100% the turn after, assuming he missed during the first attempt.<br/>
To formalize this problem, we have corner &isin; {(A,6),(A,1),(F,1),(F,6)} and K<sub>i</sub> p<sub>Ship</sub>corner, which roughly translates into "Agent i knows that there is a ship in this corner". From the rules, there are only two possible direction that is allowed, since, for example in case of corner = (A,6) K<sub>i</sub> p<sub>Ship</sub>(A,6) &rarr; K<sub>i</sub>(p<sub>Ship</sub>(A,5) &or; p<sub>Ship</sub>(B,6)), since the slots in the other directions are out of bounds. This implies that within at most the next two steps, the ship's orientation is found and within the next (size of ship)-2 steps, the ship is sunk. The number of step required for sinking in this situation is minimal for all ship sizes in the most optimistic situation for the defender (the opponent keeps guessing the wrong directions until there is only one option left). As previously mentioned, if the ships are placed within (B~E,2~5) there are 4 possible targets available after the hit for non-edges and 3 possible targets for edges excluding corners.

<b> Attacking </b>

When attacking a position on the grid, it is preferred to avoid attacking the corners unless you already know that a ship part might be there. Formally, you would write this knowledge as K<sub>i</sub>p<sub>Ship</sub> corner, as seen before. We assume that the opponent is also aware of the position tactics when we take into account attacking, so in conclusion it is more likely that ships will not be in the corner slots in the first place.

Furthermore, &not;p<sub>Ship</sub>corner can also be discovered by attacking the two side of the corner in question. Attacking these positions is also preferable since this can leads to knowing the status (if there is or isn't a ship there) of three position in only 2 steps, as the best case scenario. To give a more formal example, if agent i behaves as follows and corner = (A,6), we can obtain more information efficiently: During a turn t, agent 1 discovers K<sub>i</sub>&not;p<sub>Ship</sub>(A,5) &and; during turn t+1 he discovers K<sub>i</sub>&not;p<sub>Ship</sub>(B,6), but K<sub>i</sub>&not;p<sub>Ship</sub>(B,6) &and; K<sub>i</sub>&not;p<sub>Ship</sub>(A,5) &rarr; K<sub>i</sub>&not;p<sub>Ship</sub>corner, so he discovers K<sub>i</sub>&not;p<sub>Ship</sub>corner as well. Therefore, information can be gained more efficiently in this case, which we can consider to be best for this scenario. If it is in the worst case, where your first attack missed and the second one hits, then the information gained is as good as if you were attacking the wrong side first after you attacked a corner. However, if your first attack hits and there is a corner piece that you discover with your next attack, then in this scenario, the information gain is better than if you were to simply attack the corner. Overall, this tactic of attacking the corner-adjacent slots has a 66% chance of a positive yield of information and is thus preferred over attacking the corners.

[Back](./)
