**Classical robots**
Functional breakdown in separated modules (Divide and Conquer)
- Perception (Artificial vision, NLP)
- Planning (Knowledge bases, spatial models)
- Action (Robotics Arms, Mobile robots)
Highly complex
Must integrate modules

**Behaviour based robotics**
Rodney Brooks 1991 proposed division at level of behaviour.
He invented Roombas
"Elephants dont play chess", dont worry about complex high level reasoning problems.
Focus on low level easier tasks and basic components
![[Pasted image 20260507150559.png|428]]
Subsumption architecture like giving a weight/priority to responses.
Only works for simpler problems

**Bio-Inspired Approaches**
Look at evolution and psychology
Evolutionary robotics is the automatic design of robots and of their sensorimotor control systems through and evolutionary computation process.
![[Pasted image 20260507150948.png|427]]
For subsumption architecture randomly generate weights.
Genotype - weights etc (DNA) set of numbers encoding parameters and structure
Phenotype - physical expression of the DNA, e.g. create a feedforward multi layer perception etc
Capra robot- simple robot, 6 small range infrared bump sensors in front, 2 in back. Two wheels (actuators), 2 degrees of freedom, direction dictated by speed difference.

When doing binary encoding randomly flipping bits can have vastly different impacts because flipping the first few bits will have a significantly higher magnitude than the last few. Grey encoding ensures only a small amount is changed no matter which bit is flipped

FARSE simulator used for iCub fitness simulation. Projecting into real world from simulation large field of research. Noise needs to be applied to simulation to emulate real world noise.

ARMS race in robotics, co evolution - an adaptation in one lineage (e.g. predators) may change the selection pressure on another lineage (e.g. prey) giving rise to counter adaptation. If this occurs reciprocally an unstable runaway escalation of 'arm races' may result.
![[Pasted image 20260507153449.png|489]]


**Grammar encoding**
naive: 1-1 connected, 2-1 not connected, 3-1 connected etc.
We need to compress to prevent huge blowup
we use merge together parts of the big matrix into letters for file storage
For encoding a nnet weight matrix
- non terminal a-p for all 16 2x2 binary matricies
- non terminal A-Z as a-p quadruplets
![[Pasted image 20260507153623.png|445]]
we can mutate bigger letters in one go.
Lipson expert who 3d printed trained genomes
![[Pasted image 20260507154217.png]]


**Swarm Robotics**
Swarm robotics is the study of of how independent robots can act as a group, giving rise to collective behaviour that a single such robot could not achieve on its own.
Dorigo social insect behaviour in ants. Ants smell path of most successful ants and follow it.
Kilobot, very cheap large scale swarm robots (Roberstein, Harvard)