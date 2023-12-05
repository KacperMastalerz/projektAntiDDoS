4.1. Attack Detection Trigger Module
At present, many DDoS attack detection methods have been proposed in SDN, mainly focusing on detection and defense mechanisms [22,23]. Most of the existing detection methods are usually scheduled by periodic triggers. But, it is very difficult to choose an appropriate detection period. If the chosen period is too large, the response time will be too long, which forces the controller and switch to deal with a large number of attack packets and may cause the controller to crash. In contrast, if the period is too small, the detection module will be started more frequently, which leads to a waste of controller resources (i.e., CPU and network bandwidth) and affects controller efficiency. Therefore, as an important factor affecting detection efficiency and system performance, the trigger mechanism of attack detection is very worthy of scholars’ attention.
When a DDoS attack occurs, the number of packet_in messages will increase sharply, resulting in a decline in controller processing capacity and the depletion of controller resources. Therefore, we consider the ratio of the number of packet_in messages per unit time 𝑡
 to the processing capacity of the controller as the prerequisite for triggering the CC-Guard system.
𝛿𝑗=∑𝑖=1𝑀𝜆𝑖𝜂𝑗
(1)
In Equation (1), 𝑀
 represents the number of switches managed in controller 𝐶𝑗
, 𝜆𝑖
 represents the flow request rate of switch 𝑆𝑖
, 𝜂𝑗
 represents the processing capacity of the controller 𝐶𝑗
, and 𝛿𝑗
 represents the threshold for determining whether to start the system detection module. If 0.8≤𝛿𝑗≤1
, it indicates that controller 𝐶𝑗
 is about to be overloaded, at which point the system trigger mechanism is started.
