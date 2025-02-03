## Modelling Crowd Behaviour: A Comprehensive Analysis for the Safe Evacuation of Freshers’ at Local Venues ##

### Abstract ###
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

### Layout of Night Club ###
The ground floor (40m x 35m) is twice the size of the first floor (20m x 35m), and consists of a dance floor, bathroom and two bars. 
In compliance with government regulations [25], we also included 4 emergency exits, each of width 2m. Initial density is set to be highest on the 
dance floor, with smaller density pockets around the bathroom and bars. We also introduced some ’obstacles’, such as a barrier around the front and 
back of the dance floor, and tables around bar 2. The first floor is a lounge area, with rectangular benches and a large bar at the back. 
It also has a single emergency exit, and two sets of staircases, positioned such that attendees navigating them emerge next to the emergency exits 
on the ground floor. The CSV version is also available here, where we grid the floor by 1m x 1m square and 1 represents the obstacles and 0 is the free space.

<img width="875" alt="Screenshot 2025-02-03 at 16 00 10" src="https://github.com/user-attachments/assets/f3de81b0-7cdc-47a1-a11d-29983eabc47f" />

### Assumptions ###
(i) Maximum capacity per square meter is 5 people.
(ii) Full capacity of the bar is 900 people with 300 upstairs and 600 downstairs.
(iii) Once an individual has left the building, there is no reentering and the queuing immediately stops once exit has been reached.
(v) Once the destination is decided, individuals will not change their chosen exit during the evacuation. (vi) Navigating a staircase takes each individual 10 seconds.
(vii) No death will be caused during the evacuation.

### Speed under different panic levels ###
Understanding how the psychological panic level influences evacuation time is essential for developing a robust evacuation plan so that personnel 
of the club can make a wise decision on the pressure degree they pose on people’s psychology to make the whole evacuation process more efficient.
To assess how pedestrians’ panic levels may lead to different results in evacuation, we separate panic into four stages: no-panic, 
low-panic, medium-panic and high-panic. And the corresponding speed can be expressed here: 

$$V_e = \frac{\mu_p}{\mu_0}\dot V_0$$

Here, Ve represents the evacuation speed, $V_0$ represents the speed without panic. $μ_p$ is the speed index, which varies with different panic levels 
and is calculated with the equation shown below. $μ_0$ is the speed index when no panic exists. 

$$μ_p =a·k_a +b·k_b +c·k_c +d·k_d$$

$a, b, c, d$ corresponds to the environmental factors are defined as below:

<img width="706" alt="Screenshot 2025-02-03 at 16 09 28" src="https://github.com/user-attachments/assets/aa233727-5528-4db5-b169-301179a9e105" />

### Possible herding behaviors ###
Occupant stands for the entirety of people within the cell. It is normally preset to be one person which is homogeneous. Nevertheless, heterogeneity which includes mentality properties such as herding is essential in investigating the global behaviour of evacuation. The research done by Helbing D, Farkas I, and Vicsek T in 2000 demonstrated that individualism urges people to seek the closest exits while herding ensures the successful escape can be fully imitated within the commune. Therefore, the combination of individualistic and herding behaviour will give desired results in evacuation.
Thus, in initialising, our CAM separates the whole population into three occupant types: single person, pairs, and groups of 3 people with the probability of 10%, 59.2%, and 30.8% respectively. And their initial positions are randomised.

Therefore, the initial layout is like:

<img width="702" alt="Screenshot 2025-02-03 at 16 11 44" src="https://github.com/user-attachments/assets/1d9986f8-957c-4ab9-af56-2d9139584f84" />


### Main CAM Model ###
This model follows the following flow chart as rules:

<img width="773" alt="Screenshot 2025-02-03 at 16 12 49" src="https://github.com/user-attachments/assets/14f82e1e-52e8-408e-8c6a-3eeaac3156d0" />

#### Panic Level Evaluation ####
The simulation results for each panic level group are shown here:

<img width="823" alt="Screenshot 2025-02-03 at 16 13 53" src="https://github.com/user-attachments/assets/ab68965b-ef41-4a4e-ab9c-35cd603c5284" />
<img width="554" alt="Screenshot 2025-02-03 at 16 14 18" src="https://github.com/user-attachments/assets/3e44f505-4010-4d6d-812a-eba3e3101d28" />

And the heatmap give the possible bottlenecks during the evacuation process.

<img width="270" alt="Screenshot 2025-02-03 at 16 15 24" src="https://github.com/user-attachments/assets/887d01bf-2e90-435c-be5f-be2b26b6418f" />
<img width="271" alt="Screenshot 2025-02-03 at 16 15 37" src="https://github.com/user-attachments/assets/65ab10f1-8f3b-4c9e-a066-68f95bb7ab3e" />
<img width="571" alt="Screenshot 2025-02-03 at 16 15 52" src="https://github.com/user-attachments/assets/28bfcc89-361b-4888-87d6-5ec98fe40dd7" />

#### Exit Evaluation ####
In the previous CAM, people going down from the western staircase would spontaneously evacuate through the western exit. However, the heat maps demonstrate that the western exit has the greatest density com- pared to others. Therefore, to reduce the possibility of collision and congestion, the crowd gathered need to be diverted. We either divert people to a new emergency exit near the western staircase or divert the crowd to other relatively idle exits. The newly constructed exit is circled in Fig 19 which is above the western staircase on the ground floor.

<img width="626" alt="Screenshot 2025-02-03 at 16 16 35" src="https://github.com/user-attachments/assets/f9851c1a-71dc-478a-aa35-32c751397224" />

When considering diverting the crowd only through existing exits without creating a new one, the exit on the east side is not considered for two reasons. Firstly, from the previous heat maps, the eastern exit already has a high population density. Secondly, The distance between the east and west exits is relatively far and close to the emergency position, which is time-consuming and safety unguaranteed. Therefore, we decided to test two possible cases: diverting some part of the crowd to the closest exit (southern exit) only; and diverting some part of the crowd to either the closest or second closest exit (southern exit and northern exit) arbitrarily.

<img width="670" alt="Screenshot 2025-02-03 at 16 17 06" src="https://github.com/user-attachments/assets/f60f38e0-cfe5-4057-9951-acef91c8c08c" />
<img width="708" alt="Screenshot 2025-02-03 at 16 17 19" src="https://github.com/user-attachments/assets/28af73b1-53d2-4835-90f3-8832a183ac51" />
<img width="542" alt="Screenshot 2025-02-03 at 16 17 51" src="https://github.com/user-attachments/assets/d077aa0f-a7ad-4670-b71d-5339606d311e" />
<img width="775" alt="Screenshot 2025-02-03 at 16 19 20" src="https://github.com/user-attachments/assets/1fc17ac4-ba54-4959-914a-a55a2216be45" />





















