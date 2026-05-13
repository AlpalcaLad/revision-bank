Moving body part to manipulate the environment
- reaching
- grasping

Robotic manipulator
- one or more links
- connected by joints
- endeffector (hand etc used to affect and move objects in environment)
generally one DOF per joint altho new ball and socket have more

**End effectors**
- Grippers, e.g. three fingers
- Human hand

**Joints**
- joint limit
	- extreme of how far the joint can move
	- Compute workspace (where endeffector can reach)
	- ![[Pasted image 20260511205111.png|254]]
	- use workspace, avoiding hitting robot and obstacles
- 7 DOF for human arm
	- 3 shoulder, 1 elbow, 3 wrist

**History reminder**
Waldo, puma (first industrial, nuclear), rumba, ICub, pepper

**Kinematics**
Relationship between actuator motion and resulting effector motion
- rules about structure of manipulator
	- what is attached to what, DOF count, join count etc
- determines where endpoint is given joint angles
Manipulation problems
- where endpoint is relative to rest of the arm
- How to generate paths for manipulator to achieve goal (inverse kinematics)

**Inverse Kinematics**
Position -> angle conversion
- from endpoint
- to angles of joints
Maths is computationally intensive, Jacobian inverse technique with Hessian matrix
Can be done with machine learning.

**Forward kinematics**
angles -> position
Find endpoint from angles

**Dynamics**
Properties of motion and energy of moving object
Different impact in robot motion
- behaviour of slow moving mobile robot not impacted by dynamics
- behaviour of fast moving juggling robot highly impacted by dynamics
expensive computation of direct and inverse dynamics.
In industry slow heavy robots are easier.
In a factory for building cars we have huge robots to do this.

**Compliance**
Capability of robot part to respond to environmental forces
Important for safety
Solutions
- Spring in joints
- Soft materials
- Software compliance
This adds mathematical complexity to calculations

**Control**
Actuator uncertainty
- impossible to know exact outcome of an action

**Closed loop** (feedback control)
- achieve and maintain a desired state by continuous comparison of current state with desired.
- Feedback: information sent back
- Desired state: where system wants to be
- Error: difference between current and desired states
- ![[Pasted image 20260511210320.png|391]]

**Open loop**
Apply the force, don't check hope it works
Good for heavy precise robots where we aren't worried about faults, as it avoids extra computation

**Proportional control (P)**
- system responds proportional to error
- Gain: magnitude of systems response, hard to determine in advance, trial and error
- Oscillation: undershoot or overshoot desired state
- Damping: Systematically decrease oscillation
- Worst case, not a good solution.

**Derivative control (PD)**
- proportional error signal added with derivative of the error signal
- solve gain/oscillation problem
- When system is close to desired state controlled differently when far
- Correct momentum as system approaches desired state
- Used widely in industrial robotics

**Proportional integral control**
- integral term I: system integrates incremental errors over time
- no steady state errors, repeatable fixed errors
- When I reaches threshold system corrects
- Many joints have PID controllers

Feedback control good for low level motor actions and errors
AI/cognition good for high level behaviour


**Cognitive approaches**
U - shaped learning
- Grasp reflex at 0-2 months, prereaching 
- Prereaching declines 2-3 months
- Reappears 3-4 months
Other u shaped learning examples
- walking reflex
- Past tense speaking went -> goed -> went
	- realised pattern implicitly but overapplied it


**Visually guided reaching**
Model 
- Direct centre of gaze towards visual target (foveate)
- Eye position = proprioceptive cue for target location
- learn mapping of eye position - arm movement

Motor babbling: random exploration of your environment,
randomly move objects without intent
Brain creates a map between joint activation and end position.
Babybot, precursor to iCub

**Advice**
Pick at least 2 models and learn them in detail

**Deep learning**
Gu et al
- random target reaching and door opening
- parallelised the algorithm across multiple robots, pooling policy updates asynchronously
- Training in simulation then physical robot testing
- primarily in uni in california

**CNN**
Hand eye coordination for grasping levine et al 2018
- 14 robots 800,000 training grasp examples
- CNN for grasp prediction
- CNN uses network to successful servo the gripper in real time grasps
- input: pre grasp, post grasp images