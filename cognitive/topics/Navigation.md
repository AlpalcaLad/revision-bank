**Navigation**
Moving the entire robot from one location to another (destination planning)
- locomotion
- localisation and mapping

**Manipulation**
moving part of the body to manipulate the environment
- reaching
- grasping

**Locomotion**
Mechanical locomotion (often wheels e.g. pepper)
biomimetic locomotion (crawling, sliding, running e.g. Boston dynamics)
legged locomotion
- leg events (lift Up / release Down)
	- for k legs, N = (2k - 1)!             <<<< Very important formula
- Gait: precomputed coordinated movements (oscillations)
	- Combinations of events to get movement like horses etc.

**Navigation**
4 key questions
- Where am i going (and why)
	- Mission planning
- What is the best way there
	- Path planning
- Where have I been
	- Map making (Simultaneous Localisation and Mapping, SLAM)
- Where am I 
	- Localisation

**Path planning**
Qualitative path planning
- Agents perspective
- Topological route with distinctive landmarks
- Associations (reactive e.g. turn right at any crossing met)
- AI search and planning
- Graph search
Quantitative path planning
- Metrics or map layout (birds eye view map)
- Orientation- and position-independent

**Topological navigation**
Landmark methods
Perceptually distinctive easy to recognise features
- Natural: object or scene
- Artificial: sign or visual pattern (e.g. QR-like)
- Gateway: landmark to change behaviour (e.g. junction)
Association between perceptual state and movement
- Visual homing: visual patterns associated with locations/routes (e.g. bees navigation), compare current view with stored snapshot image at destination
- QualNav, infers location from relative positions of landmarks (e.g. constellations)
World as relational graph where nodes are landmarks
edges are paths between landmarks
multi level spatial hierarchy, animal navigation

**Localisation**
mobile robot localisation - the problem of determining the pose of a robot relative to a given map of the environment (pose is x,y,theta)
Use bayesian algorithms to estimate likely location
- extract features from raw data, match to map e.g. corners, walls, doors
- computationally efficient
Common methods are marcov localisation and extended Kalman filters
Create hypothesis based on visible features

**SLAM**
Simultaneous localisation and mapping
vSLAM uses camera as primary sensor.

**Marcov localisation**
Used for global localisation without initial starting position.
Computes the belief in each possible position based on evidence

**Kalman filters**
Used for local localisation
Predict what robot will sense next given control action

**Iconic localisation**
Raw sensor readings to match actual observations to expected observation
- high computation due to many sensor readings
- Grid based method
	- World partitioned into tessellation of convex polygons
	- Compute likelihood of possible poses within each polygon
- Monte carlo locatilisation
	- Particles or samples scattered through space
	- compute belief in each pose
	- more particles added, particles with low prob die

**Cognitive Navigation**
RatSLAM, emulating spatial navigation ability of the rat's hippocampal system
Building and using maps simultaneously of large and complex environments
Less accurate than slam but better handling of noisy input, changing environments and complexity.
Much more flexible
Cells include
- place cell 
	- Fire consistently when the rat is at a specific location in the environment
		- e.g. place cell for desk, wall etc
- Head direction cell
	- Fire when looking in direction
- Grid cell
	- Like place cell but with multiple firing fields
	- Fires when rat is located at any vertices of a hexagonal pattern across the environment
	- Cells as signal for measuring displacement, distances and direction
Combining place and grid cells gives path integration mechanism for cognitive map
- innate sense of the world and location
- similar to SLAM mechanisms
Used in real examples e.g. office environment
Wiles' lab used iRat, animal robot interaction

**OpenRatSLAM**
Open source version of RatSLAM with bindings for ROS, used for car in St Lucia to make map 66km journey.

**Cameras vs LIDAR**
LIDARS are better. Auto cars use LIDAR.
We aren't ready for camera only.

**Advice in lecture**
Pay attention to Monte Carlo, other common filter for classical
grid cells place cells etc mapping into ratslam

**Milford et al**
RatSLAM proposal paper.
- Tested on Pioneer2-DXE robot.
- Carpeted campus building area
- Updates every 200ms
- 40m duration total with no starting information
- No cartesian product, just a rep consistent with some cartesian properties.
- RatSLAM able to reconstruct environment accurately within timeframe