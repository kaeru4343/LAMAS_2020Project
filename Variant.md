---
layout: default
title: Rules and Components
theme: jekyll-theme-cayman
---
# Variation of the game 
Here we consider a variation of the game. The varinat is that when annoucing the posisitn for an attack, the agents needs to announce its own grid state together with the attack. so the announcement is "&not;K<sub>i</sub> p<sub>Ship</sub>(x,y,b) &and;  p<sub>Ship</sub>(x,y,b)" or "&not;K<sub>i</sub> p<sub>Ship</sub>(x,y,b) &and; &not; p<sub>Ship</sub>(x,y,b)", which translate to "I do not know if a ship is at (x,y,b) and I know that if a ship at (x,y,a)". Then the other agent must reply with the same actions as done before in the normal game. 
Since the agents want to avoid its own ship position to become common knowledge, when attacking, the agents want to expolit the other agents position and hide its own position.  
Then the agents needs make less annoucment which exploits their own position of the ship, p<sub>Ship</sub>(x,y,b). Futhermore, when one position of the ship is known to the other agents, K<sub>i</sub> p<sub>Ship</sub>(x,y,b) and from the common knowledge of the rules, the agent want to avoid attacking position on the surrondings of known position. This avoidane behavior is common knoweldge amongs the agents. 

[back](./)