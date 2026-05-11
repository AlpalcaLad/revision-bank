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
- Visual homing: visual patterns associated with locations/routes (e.g. bees navigation)
- QualNav, infers location from relative positions of landmarks (e.g. constellations)