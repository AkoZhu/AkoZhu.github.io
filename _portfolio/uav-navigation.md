---
title: "Autonomous UAV Navigation Using Sample-Based and Reinforcement Learning Methods"
date: 2022-05-05
excerpt: "Develop a robust framework for autonomous UAV navigation using both sample-based methods and reinforcement learning techniques.in a team of three. <br/><img src='/images/portforlio/uav/diagram.png' width='100%'>"
location: "University of Pennsylvania"
collection: portfolio
---

_This is a course project for ESE650 Learning in Robotics(Spring 2022) at University of Pennsylvania._

Here is our [report](/files/uav-report.pdf).

# Introduction
In our project, we adimed to develop a robust framework for autonomous UAV navigation suing both **sample-based methods** and **reinforcement learning techniques**. This primary goal was to find control inputs that enable unmanned aerial vehicles(UAVs) to reach a target state while safely avoiding obstacles. We implemented sample-based methods, including Repidly-Exploring Random Trees(RRT) and RRT*, combined with Linear Quadratic Regulator(LQR) for trajectory optimization. Additionally, we employed a reinforcement learning approach using Q-learning integrated with a Proportional-integral-Derivative(PID) controller to generate collison-free trajectories.


# Design Decisions and Implementation
## Sample-based Methods
We started by implemented RRT, a well-known sample-based algorithm that builds a tree by randomly sampling the configuration space and connecting the sameples to form a path. To overcome the limitation of RRT often resulting in sub-optimal paths, we implemented RRT*, which includes a cost function to find the current optomal path by rearranging nodes based on cost. This approach ensures that the trajectory is smoother and more efficient. We further optimized the trajectories using the LQR Minimum Snap method, which smooths transition between waypoints by solving for polynomial coefficients to minimize the jerk, ensuring dynamically feasible paths for UAVs. 

## Reinforcement Learning Approach
As for the reinforcement learning part, we choose Q-learning due to its computational efficiency and suitability for representing low-dimensional data. The Q-learning model was designed with a state space representing the UAV's position and a finite set of actions(North, South, East, West). The UAV receives rewards based on its action, promoting optimal pathfinding towards the goal while avoiding obstacles. To handle the nonlinear dynamics of quadrotors, we integrated a PID controller that provides stable hovering and precise navigation based on the UAV's current state and desired position. 

# Functionality and Preformance
The implemented framework was tested in 3D static environments using ROS Gazebo simulations. For the sample-based methods, RRT and RRT* were compared in terms of path optimality and computational efficiency. The RRT* algorthm demonstrated a significant improvement in generating smoother and more optimal paths compared to RRT, although with a higher computational cost due to continuous re-building of the tree. The LQR Minimum Snap method effectively optimized these paths, ensuring smooth transitions and adherence to the uAV's dynamic constraints. 

The Q-learning approach, combined with the PID controller, allowed the UAV to learn and navigate autonomously in an unknown environment. Through iterative learning, the UAV was able to find an optimal policy for reaching the goal state, with the PID controller ensuring stable and accurate movement. The traning process required 34 episodes to achive the optimal path in a discretized $$5 \times 5$$ grid environment, demonstrating the feasibility of reinforcement learning for UAV navigation.

# Experimental Results and Conclusion
Our experimental results indicate that both sample-based and reinforcement learnign approaches are capable of producing effective UAV navigation strategies. The RRT* algorithm, combined with LQR Minimum Snap, generated smooth and efficient paths, while the Q-learning approach provided a robust framework for learning-based navigation. The sample-based methods took significantly less time to compute paths compared to the reinforcement learning method, highlighting the trade-offs between these approaches.

Future work will focus on extending the reinforcement learning model to 3D environments and incorporating more complex scenarios to enhance the robustness and applicability of the framework. Additionally, integrating advanced motion planning algorithms and improving the obstacle avoidance capabilities will further refine the system's performance in real-world applications.