# projektAntiDDoS4.2.1. Identification of Overloaded Controller
When subjected to DDoS attacks, controllers are overloaded by processing malicious flow requests, so it is important to identify overloaded controllers under DDoS attacks. The reason for overload is that the number of packet_in messages sent by the switch is greater than the processing capacity of the controller, which leads to the load on the controller. Therefore, we identify the overloaded controller according to Equation 
4.2.2. Optimal Domain Migration Strategy for Switches
The essence of the switch migration problem is how to migrate switches in the overloaded domain to other controllers so that the load on each controller is balanced. The main algorithm process is as follows: Firstly, the candidate set 𝑆𝑀
 of migration switches is found from the overloaded controller domain according to Equation (2). Then, we select the target controller from the normal controller and set 𝐶𝑁
 according to the controller processing capacity threshold. The selection of the target controller is calculated with the objective of minimizing the switch migration time delay (time delay refers to the sum of the shortest physical distances of the switch 𝑆𝑖
 to be migrated from the overloaded controller 𝐶𝑗
 to the target controller 𝐶𝑗′
, as shown in Equation (3). This problem is an objective optimization problem and can be solved using the genetic algorithm [24]. Finally, the controller with the minimum function value is selected as the target controller, and the selected switch is migrated to the target controller. The pseudo-code of the switch migration algorithm is shown in Algorithm 1.
min𝐸=∑𝑖=1𝑀𝑚𝑖(𝐻𝑖𝑗+𝐻𝑖𝑗′)

