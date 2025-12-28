# The Impact and Effectivity of Improving Operating Room’s Schedules Using Simulation

In real-world hospital settings, operating room (OR) 
scheduling is a complex and critical task that involves 
coordinating multiple resources, including surgical teams, 
anesthesia providers, nursing staff, and the availability of 
specialized equipment. The primary objective is to maximize OR 
utilization while ensuring patient safety and minimizing delays. 
Effective OR scheduling must account for various factors such 
as case durations, surgeon availability, and emergency 
procedures. (Jun Xue et al. 2025) 
 
  One of the significant challenges in OR scheduling is 
balancing the efficient use of resources with the unpredictability 
of surgical procedures. Variations in surgery durations, last
minute cancellations, and emergency cases can disrupt even the 
most meticulously planned schedules. 

  In this simulation project, we aimed to model a simplified 
version of an OR scheduling system to analyze the impact of 
varying arrival rates on key performance metrics such as patient 
waiting times, queue lengths, and resource utilization. By 
simulating different scenarios, the goal was to gain insights into 
how changes in system load affect overall performance and to 
identify potential bottlenecks that could inform strategies for 
improving OR scheduling efficiency.

# Model Description

 We developed the model using Python and the simpy 
discrete-event simulation library. The simulation features two 
independent streams of patient arrivals: elective and 
emergency. Each patient type undergoes a surgery with a 
randomly determined duration, and wait times are tracked 
 
Assumptions and Simplifications 
 
- Surgeries start immediately upon patient arrival and once 
there is an operating room available 
- Elective patients arrive at fixed intervals, while emergency 
patients follow a Poisson arrival process.
- Elective Surgeries arrive based on a fixed schedule 
- Emergency Surgeries arrived randomly, and are given 
priority access due to high priority cases that must be
accommodated urgently. Meaning an elective case may 
be delayed if an emergency arrives.  
- Once a surgery begins, it continues uninterrupted to 
completion. This reflects standard clinical protocols where 
surgical procedures cannot be paused once underway. 
- Surgery durations for both patient types are assumed to 
follow the same exponential service-time distribution. This 
simplifies the simulation while approximating general 
variability.

 
Model Logic, Components, and Structure 
 
- Entities: Patients classified as elective or emergency. 
-  Events: Arrival (elective or emergency), start of surgery, 
end of surgery. For the system: OR utilization is derived 
by summing active surgery time over total simulation time, 
total surgeries completed, average queue lengths, and 
wait time. 
- Logic: If the OR is free, the next patient (emergency 
prioritized) enters surgery. If busy, elective cases wait; 
emergencies enter a priority queue.

# Experiment Design

The base scenario involved a single simulation run 
representing a typical hospital day (600 minutes) with a fixed 
number of four operating rooms. Elective surgeries were 
scheduled at pre-defined intervals, while emergency surgeries 
occurred randomly based on a probability model. The system 
prioritized emergency cases, allowing them to preempt elective 
surgeries when OR capacity was limited. This setup was 
chosen to reflect a realistic hospital environment where 
emergency surgeries can disrupt planned schedules and stress 
resource availability. 
 
  The simulation run length was set to 600 minutes, 
representing a full 10-hour shift in the operating room schedule. 
No warm-up period was defined, as the simulation includes 
events from the start of the day when ORs are first made 
available. 
 
   The structure of the model is suitable for exploring various 
parameters such as the number of ORs, emergency arrival 
probability, and turnover time. By varying these inputs, one 
could evaluate their impact on key outcomes like OR utilization, 
wait times, and the number of delayed or canceled surgeries.

# Analysis and Interpretation 

 When compared to elective surgeries, the simulation shows 
that emergency surgeries always have priority access to 
operating rooms, which leads to noticeably lower wait times. 
Even if the system finishes a respectable amount of both types 
of surgeries in the allotted 600 minutes, elective treatments are 
more likely to be delayed, particularly when emergency arrivals 
are common. 
 
   A lack of balance can be seen when comparing the 
performance of different operating rooms. For example, OR 4 is 
still underutilized, which may indicate ineffective resource 
allocation or queue assignment. There is a tendency for 
emergency procedures to overshadow elective cases as their 
arrival rate rises because of their longer average durations and 
higher priority; this could be the point past which the number of 
elective surgeries declines drastically. 
 
   The small number of ORs in comparison to periods of high 
demand is a major bottleneck. Elective surgeries must wait 
longer or be postponed because emergency arrivals tend to 
occur at short intervals. In order to address this and maintain 
performance under changing demands, techniques like 
dynamic scheduling, emergency ORs, or even more intelligent 
load distribution may be needed.

## Contributors’ GitHub Profile Links:

- [@alyssanew] (add-your-link)
- [@jeysiiiiiii] (add-your-link)
- [@ackleely](https://github.com/yourusername)

