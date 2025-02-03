### Modelling Crowd Behaviour: A Comprehensive Analysis for the Safe Evacuation of Freshers’ at Local Venues ###

#### Abstract ####
Panic-induced crowd behaviour poses a significant threat, as evidenced by historical incidents like the Brixton Academy in 2022 
and the Hillsborough disaster in 1989. This study addresses the critical need for effective crowd management by formulating a robust 
evacuation plan for a local nightclub’s indoor Freshers’ event. Both microscopic and macroscopic modelling approaches were employed, 
considering individual behaviour’s and the collective dynamics of crowds. Our research aims to estimate evacuation time, analyse crowd density, 
potential bottlenecking, and identify forces and emotions influencing indi- viduals during evacuations. Three models were developed, two microscopic, 
and one macroscopic, all of which resulted in working evacuation simulations. The microscopic models displayed longer evacuation times on average 
compared to the macroscopic model. Additionally, all models were compared to the results of an online crowd evacuation simulation. 
Results from the two microscopic models, Social Force and Cellular Automata, are similar in many ways, potentially highlighting their robustness 
as evacuation simulations. All models successfully identify bottlenecking, and our evaluation underscores the influence of wider emergency exits 
on bottlenecking times, as discussed in previous literature. Future work will be aimed at resolving some weaknesses discovered in the models, 
such as resolving pathfinding challenges, emphasising the interplay between individuals in the model more, and evaluating bottlenecking further.

#### Layout of Night Club ####
The ground floor (40m x 35m) is twice the size of the first floor (20m x 35m), and consists of a dance floor, bathroom and two bars. 
In compliance with government regulations [25], we also included 4 emergency exits, each of width 2m. Initial density is set to be highest on the 
dance floor, with smaller density pockets around the bathroom and bars. We also introduced some ’obstacles’, such as a barrier around the front and 
back of the dance floor, and tables around bar 2. The first floor is a lounge area, with rectangular benches and a large bar at the back. 
It also has a single emergency exit, and two sets of staircases, positioned such that attendees navigating them emerge next to the emergency exits 
on the ground floor. The CSV version is also available here, where we grid the floor by 1m x 1m square and 1 represents the obstacles and 0 is the free space.
<img width="875" alt="Screenshot 2025-02-03 at 16 00 10" src="https://github.com/user-attachments/assets/f3de81b0-7cdc-47a1-a11d-29983eabc47f" />

#### Assumptions ####
(i) Maximum capacity per square meter is 5 people.
(ii) Full capacity of the bar is 900 people with 300 upstairs and 600 downstairs.
(iii) Once an individual has left the building, there is no reentering and the queuing immediately stops once exit has been reached.
(v) Once the destination is decided, individuals will not change their chosen exit during the evacuation. (vi) Navigating a staircase takes each individual 10 seconds.
(vii) No death will be caused during the evacuation.

#### Speed under different panic levels ####
Understanding how the psychological panic level influences evacuation time is essential for developing a robust evacuation plan so that personnel 
of the club can make a wise decision on the pressure degree they pose on people’s psychology to make the whole evacuation process more efficient.
To assess how pedestrians’ panic levels may lead to different results in evacuation, we separate panic into four stages: no-panic, 
low-panic, medium-panic and high-panic. And the corresponding speed can be expressed here: $$V_e = \frac{\mu_p}{\mu_0}\dot V_0$$

