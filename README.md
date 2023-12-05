# projektAntiDDoS4.2.1. Identification of Overloaded Controller
When subjected to DDoS attacks, controllers are overloaded by processing malicious flow requests, so it is important to identify overloaded controllers under DDoS attacks. The reason for overload is that the number of packet_in messages sent by the switch is greater than the processing capacity of the controller, which leads to the load on the controller. Therefore, we identify the overloaded controller according to Equation (2). If the number of packet_in messages of controller 𝐶𝑗
 is greater than 0.8 times the controller’s processing capacity, we consider that the controller is overloaded and switch migration is required.
∑𝑖=1𝑀𝛼𝑖×𝑓𝑖𝑗>0.8×𝜂𝑗
(2)
In Equation (2), 𝛼𝑖
 represents the number of packet_in messages sent by switch 𝑆𝑖
 to controller 𝐶𝑗
; 𝜂𝑗
 represents the processing capacity of controller 𝐶𝑗
; 𝑓𝑖𝑗
 represents the connection between switch 𝑆𝑖
 and controller 𝐶𝑗
. If 𝑓𝑖𝑗
 is 1, it means that controller 𝐶𝑗
 has a connection with switch 𝑆𝑖
; otherwise, if 𝑓𝑖𝑗
 is 0, it indicates that the controller 𝐶𝑗
 is not connected to switch 𝑆𝑖
.
4.2.2. Optimal Domain Migration Strategy for Switches
The essence of the switch migration problem is how to migrate switches in the overloaded domain to other controllers so that the load on each controller is balanced. The main algorithm process is as follows: Firstly, the candidate set 𝑆𝑀
 of migration switches is found from the overloaded controller domain according to Equation (2). Then, we select the target controller from the normal controller and set 𝐶𝑁
 according to the controller processing capacity threshold. The selection of the target controller is calculated with the objective of minimizing the switch migration time delay (time delay refers to the sum of the shortest physical distances of the switch 𝑆𝑖
 to be migrated from the overloaded controller 𝐶𝑗
 to the target controller 𝐶𝑗′
, as shown in Equation (3). This problem is an objective optimization problem and can be solved using the genetic algorithm [24]. Finally, the controller with the minimum function value is selected as the target controller, and the selected switch is migrated to the target controller. The pseudo-code of the switch migration algorithm is shown in Algorithm 1.
min𝐸=∑𝑖=1𝑀𝑚𝑖(𝐻𝑖𝑗+𝐻𝑖𝑗′)
(3)
s.t.    ∑𝑖=1𝑀𝛼𝑖×𝑓′𝑖𝑗′<0.8×𝜂𝑗′
(4)
In Equation (3), 𝐻𝑖𝑗
 represents the shortest distance between the switch 𝑆𝑖
 to be migrated and the overloaded controller 𝐶𝑗
; 𝐻𝑖𝑗′
 represents the shortest distance between the switch 𝑆𝑖
 to be migrated and the target controller 𝐶𝑗′
 (distance refers to the physical distance in the network topology). The state of the switch and controller is mapped from 𝐹=(𝑓𝑖𝑗)𝑀×𝑁
 to 𝐹=(𝑓′𝑖𝑗′)𝑀×𝑁
, and the value of 𝑚𝑖
 is calculated according to Equation (5). If the value of 𝑚𝑖
 is 0, it means that switch 𝑆𝑖
 has not changed state. If the value of 𝑚𝑖
 is 1, it means that switch 𝑆𝑖
 has a state change.
𝑚𝑖=⎧⎩⎨0,𝑓𝑖𝑗=𝑓′𝑖𝑗′=1 & 𝑗=𝑗′1,𝑓𝑖𝑗=𝑓′𝑖𝑗′=1 & 𝑗≠𝑗′
(5)
Algorithm 1: Target controller selection algorithm
Input: controller set 𝐶𝑛
, switch set 𝑆𝑚
;
Output: target controller 𝐶𝑡
, migration switch 𝑆𝑡
;
(1) for 𝐶𝑖∈𝐶𝑛
 do
(2) if ∑𝑀𝑖=1𝛼𝑖×𝑓𝑖𝑗>0.8×𝜂𝑗
(3) then 𝐶𝑜𝑣𝑒𝑟←𝐶𝑖
(4) end if
(5) end for
(6) Get normal controller set 𝐶𝑛𝑜𝑟=𝐶𝑛−𝐶𝑜𝑣𝑒𝑟
(7) Select switch set 𝑆𝑚′
  from controller 𝐶over
(8) While 𝐶𝑖∈𝐶𝑛𝑜𝑟 & 𝑆𝑖∈𝑆𝑚′
 do
(9) The GA algorithm is used to calculate min𝐸
 & ∑𝑀𝑖=1𝑎𝑖×𝑓′𝑖𝑗′<0.8×𝜂𝑗′
(10) end while
4.2.3. The Switch Mapping Phase
From the above description of the switch migration phase, we know the switch and the target controller to be selected for migration. This phase tells us how to migrate switch 𝑆𝑡
 from overloaded controller 𝐶over
 to target controller 𝐶𝑡
. The switch 𝑆𝑡
 sends a Remap message to the destination controller 𝐶t
, which replies with a Remap-Begin message after receiving the remap message and selects a random number to start the countdown. If the switch mapping is completed before the countdown to 0 s, 𝐶t
 sends an access control message to the switch 𝑆𝑡
 to be migrated and broadcasts the update message to the entire network. However, if the countdown times out, the countdown is reset, and the switch mapping process starts again.
