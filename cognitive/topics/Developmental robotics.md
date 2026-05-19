**Language Learning**
learning the meaning of words corresponding to the visual world, i.e. using images. 

**Developmental robotics**
Interdisciplinary approach to the autonomous design of behavioural and cognitive capabilities in artificial agents (robots) that takes direct inspiration from developmental principles and mechanisms observed in natural cognitive systems (children)

**DevRob principles**
- Phylogenetic (evolutionary history of whole species over time, link to [[swarm robotics]]) and ontogenetic interaction (individual growth and development within their own lifetime) 
- Embodied (rooted in bodily actions, e.g. Pepper physically grasping objects) where one instruction from the brain lets the body and environment do the rest and Situated (interaction with physical/social environments) where you create your own version of the world by your senses, looks different to different people
- Intrinsic motivation (motivation to learn for the task itself) and social learning (learning based on social relationships)
- Nonlinear, stage like development
- Online (active and continuous) Open ended cumulative learning
- Decentralised, no single central brain to decide what whole body does, e.g. sensors in legs determine how you walk

**Development as a dynamical system**
Walking reflex until 2 months old.
No central brain decides what the whole body does (e.g. sensors in your legs determine how you walk)
Must organise these inputs (cybernetics theory)
Many causes for behaviour e.g. size strength senses
Fast response of brain to slower body parts

**Intrinsic motivation and social learning**
Willingness to learn, curious, novelty-seeking, drives, uses social learning and imitation
e.g. playground experiment - create a toy which is stimulating, let a robot play with it, If you let robots live in world for multiple days they create words referring to different parts of the playground.

**ICub**
Modelled after a 3-4 year child with 53 degrees of freedom by the Italian Institute of Technology. Advanced hands and sensorised skin, used for testing developmental robotics and learning.

**Perez-Osorio et al**
- utilising existing paradigm of cognitive psychology for human-robot interaction scenarios
- Gaze cueing effect -> Participants track a target quicker when a face is shown looking towards it.
- For many studies this doesn't work with robots, their faces acting like an arrow more than social
- Does work for iCub as an embodied humanoid agent.
- Perez performed this in reverse, showing iCub's performance was improved with a human's gaze as a prompt.
- They used classical psychological experimental methods.

**Morse et al**
- "Posture affects how robots and infants map words to objects"
- Performed experiments on iCub to replicate existing infant data and generate new findings
	- These were then tested in infant studies
- 16 month old toddlers
- Dichotomy of cognitivist vs embodied view
	- Cognitivist: cognition separate from body
	- mind works with abstract symbols
	- i.e. internal representations
	- Embodied: cognition emerges from bodily interaction with the world
	- thinking tied to sensory and motor systems
	- i.e. mental models depend partly on where you learnt about them
- "Modi": child hears word, sees several objects, later remembers what modi refers to.
- Learners cannot learn without using body
	- Eyes, head and torso move
	- Learning occurs in specific posture
- Neural net in iCub has three fields
	- Word field: stores heard words
	- Visual field: stores appearance of objects
	- Posture field: stores body posture
- Baldwin task
	- Robot saw target object on left, foil object on right
	- Different postures required to look at each
	- Robot heard word "modi" when oriented toward target location
	- Both objects appeared in new location and robot had to choose correct object when it heard "modi"
	- 71% accuracy
	- When no posture change associated with objects performance dropped to 46%.
	- When different posture for recall robot also underperformed at chance level.
	- Infants had very similar behaviour.
