**Effector**
Any device with an effect on the environment
Humans/animals - arms,legs,fingers,wings,flippers
Robots - legs,wheels,arms,fingers,grippers
*Passive effector* - use passive actuation mechanisms exploiting the body-environment physics interaction (no/minimal energy needed). E.g. wings for flying, smart legs that walk by gravity (passive dynamic walker robot, needs a slope)
*Stiff effector* - Predetermined position/trajectory, uses energy directly

**Actuator**
Mechanism enabling effector to execute movement
e.g. muscles and tendons, electric motors, hydraulic/pneumatic cylinders, temperature/chemically sensitive materials
*Active actuator* - use energy to provide power to move the effector, does not respond to outside environment
*Compliant actuator* - softer mechanism that responds to external force, stopping its motor giving safe human robot interaction

**Joint**
An actuator that connects two body parts, can have more than one degree of freedom. A separate actuator was needed for each DOF but new motors allow more than one DOF

**Degree of freedom**
The dimension in which a movement can be produced in 3D
6 main: x,y,z (translational), roll (side to side), pitch (up and down), yaw (turn left and right)
Total degree
*Controllable degrees of freedom* are the physical ones controlled
*Total degrees* is the number on the object itself
e.g. a car has more total than controllable, because moving sideways is a degree of freedom you cant actually affect
an arm has less total than controllable, because you only need 3 degrees to position your hand, where we have 7 (i.e. some are redundant)
T.DOF = C.DOF Holonomic
T.DOF < C.DOF Non-Holonomic
T.DOF > C.DOF Redundant

**Sensor**
Physical devices to measure physical quantities
*Internal* - battery, motor
*External* - vision, distance, tactile, olfactory (detect substances like a nose), geospacial (e.g. LiDAR Light Detection and Ranging)
Discrete or continuous states
Levels of sensors
- Low, e.g. electronics (bump sensor on/off)
- Medium e.g. signal processing (microphone, sonar)
- High, e.g. computation (vision, NLP, map, multimodal)
Passive vision - bottom up image processing
Active vision - top down, use knowledge about task to look for specific stimuli