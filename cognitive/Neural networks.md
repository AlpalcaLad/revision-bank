Vision is a big bulk of the problems in cognitive robotics.
Alternatives are SLaM and random forest but CNNs are very effective at comp vision tasks
AlexNet, developed in 2011 led to a huge jump in accuracy.

**Neural network**
An artificial neural network consists of a set of *interconnected* *nodes*. It receives *input stimuli* from the environment and *learn* new behaviours/responses. 
Nodes are typically layered, two layers is a perceptron. Multi layer perceptron is generally 3 or more layers.
Most popular method is back propagation. Take final error and propagate back towards input.

**Shallow**
Feedforward neural networks. Information moves from one layer to the next layer.
Transformers are not recurrent networks they are feedforward. Not meant to be for sequences but you transform the task into predicting the next word.
Initially text generation would need sequential/recurrent networks without this transformation.
When you reach 20-30 layers start calling it a deep network, altho you wont see this for MLPs which generally at that point are worse than CNNs. Feedforward networks are fully connected layers.
Perceptron has limitations- can only learn simple linear problems![[Pasted image 20260508134917.png]]
An MLP with enough hidden nodes can theoretically learn any level of problem.

**Tasks**
Linear separable problems (easy)- logical gates AND/OR, can train a perceptron
Nonlinearly separable (hard) - XOR, only an MLP can be trained to do this. XOR is an easy problem but cant be handled by a perceptron.

because we learn in parallel for many images we make many micro adjustments. The learning rate dictates how fast we move. Particularly high rates will mean it learns too much from one image, we normally use very low since we work on many images at once.

Back prop algorithm released in 1986 by Hinton et al, before then people couldn't apply weight correction for a multi layer perceptron.

**Training parameters** 
Dropout - Each neuron is inactive with some random probability during each training minibatch
![[Pasted image 20260508135817.png]]
- forces the network to use all the neurons and not over rely on certain information/neurons
- One of the most used methods in Deep NN

Data augmentation - Reduce overfitting by generating similar examples that are altered by noise/light/flipping/colour swap/translations etc.
- Improves generalisation
- Not full substitute for more training data but can help

Network size- more neurons means it can learn better but too big of a model will be prone to overfitting.

Training parameters
- learning rate
- momentum - keep moving in same direction as last cycle somewhat, if 0 only apply current error propagation.

Optimisation methods
- Adam
- AdaGrad
- RMSProp

Trial and error, not 1 correct answer for the parameters.

**Datasets**
MNIST - handwritten digit classification
CIFAR - low resolution colour images
CIFAR-10, 10 categories, 6000 images each
CIFAR-100, 100 categories, 600 images each

**CNNs**
Invented by Lee Kahn but only made useful and efficient for large datasets by AlexNet (Hinton and Alex). 
Minimal topology
Input -> Convolution -> Fully connected -> Softmax
Convolution pooling modules
Input -> (Convolution -> pooling) -> Fully connected -> Softmax

**Feature Maps**
Copy the way the brain works, structured system with filters rather than fully connected layers. These filters are small simple neurons that filter elementary features (e.g. edges, end-points, corners). This reduces the number of connections needed

**Pooling (sub-sampling)**
Reduce spatial resolution of feature maps. Locally invariant, reduces sensitivity of output to shifts and distortions.
Max pooling - take max value from each receptive field value
![[Pasted image 20260508141159.png|390]]

(NOT AS RELEVENT FOR EXAMS BELOW)

**RNNs** 
Recurrent neural network, suitable for time series sequencing tasks, e.g. subtitling a video.
ChatGPT predicts one word at a time where an RNN outputs a sequence from a sequence.
RNNs remember the previous steps at each stage where Transformers don't use previous states.
LSTM
Recurrent networks which remember many features of previous states using gates to decide what to keep

**Transformers**
Feedforward neural network which added attention network. This is the ability to take a big sequence and understand the connections between words.
From a prompt the system determines connections between words to understand which tokens are most important.
Used for vision text generation and many other tasks.
They divide images etc into tokens.