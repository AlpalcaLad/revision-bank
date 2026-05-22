**Encoder-Decoder networks**
A.K.A sequence-to-sequence networks
Generate arbitrary length output sequences which are contextually appropriate
Sequence based architectures like RNNs
One example task is RNNs for machine translation
![[Pasted image 20260521193516.png|501]]
![[Pasted image 20260521193710.png|497]]
If only the first hidden state had direct access to the context, this would weaken the influence of the context over the output into later iterations. 
Instead context fed into each step of the decoding context.
![[Pasted image 20260521194106.png|484]]
Difference than inference: we use teacher forcing, i.e. the correct token is used an input for the next step rather than its incorrect one.

**Attention mechanism**
Context vector c
- based on final hidden state of encoder
- Represents everything about source text
- decoder only relies on c
- Not sufficient if source text is long
Instead we use an attention mechanism which obtains information from all hidden states.
Creates a single (fixed-length) vector c based on weighted sum of all hidden states
Weights focus on part of source text relevant for the current token
c is dynamically derived, i.e. different for each token during encoding

The computation of a current decoder hidden state is dependent on
- Prior hidden state
- Previous token
- dynamically generated context vector c

We use dot product attention based on how relevant an encoder state e is to the current decoder state d.
score (d, e) = d . e
Results in scalar indicating similarity between two vectors
Calculating this for all encoder states gives a vector showing the relevance of each encoder state e to what is currently being decoded
Softmax: used to normalise these scores for final weights
![[Pasted image 20260521195029.png|471]]
Where hdi-1 is d and hej is e from my previous example. Alpha is the given weight.
![[Pasted image 20260521195145.png|473]]

**Transformers**
S shortcoming of sequence based architectures like RNNs is that they don't parallelise.
Transformers do sequence processing without recurrent connections.

For a casual, backward looking (left-to-right) transformer
Network has access of all inputs up to and including the one under consideration.
No access to input information beyond current input
![[Pasted image 20260521201406.png|463]]
Computation of each item independent of all other computations, so can be easily made parallel.
Makes use of self-attention layers (simple definition here explored more later): 
- information in contexts accessed without recurrent connections.
- Comparison is between current input and other elements within a given sequence.
- In practice a more sophisticated calculation is used (covered in week 7).
Teacher forcing used in training (use correct token for future training even if model incorrectly predicted).

**Bidirectional Transformer Encoders**
Allow the self attention mechanism to range over the entire input.
Map sequences of input embeddings to sequences of output embeddings, contextualised on the whole input (done through self-attention)
![[Pasted image 20260521202807.png|471]]

**BERT**
Tokens are subwords: "embeddings" = "em", "##bed", "##ding", "##s"
Input length kept fixed to keep computation easily solveable (tractable)
- i.e. 512 subwords in orig BERT model

Pretraining BERT
- learn representations of meaning of words/sentences
-  usually needs huge amounts of text
-  results in pretraining language models
Finetuning BERT
- Take a pretrained language model
- Further training on a downstream task e.g. NLI etc, sequence classification etc.
Transfer learning
- Acquiring knowledge by learning on one task and applying it to a new task
- e.g. Pretrained BERT model acquires knowledge about language
- Which makes it easier to learn downstream tasks

Language modelling
- model learns a cloze task (filling in the blanks) rather than predicting next word
Masked language modelling (MLM)
- first language objective for BERT
- Model presented with series of sentences
- in each sequence sample of tokens randomly replaced with 
	- \[MASK\]
	- random tokens aka 'noise' (randomly sampled from unigram probs)
	- left unchanged
- In orig BERT
	- 15% tokens samples
	- 80% replace with MASK
	- 10% other tokens
	- 10% unchanged
	- Objective: predict original token for masked tokens and 'noisy' tokens
Positional embeddings covered in Week 7
![[Pasted image 20260521204019.png|459]]
Cross entropy loss used again, averaged over sampled tokens only.
Learning uses all tokens in context but for the adjustment of weights sampled token loss only.

Next sentence Prediction
- Second learning objective of BERT
- Model presented with sentence pairs
	- 50% adjacent sentences
	- 50% randomly selected
- Goal: predict which category given sentences
- New tokens
	- \[CLS\] Start of prompt
	- \[SEP\] End of each sentence
- Segment embeddings are vector of 0s if first sentence or 1s if second sentence
- ![[Pasted image 20260521204437.png|542]]

**Contextual embeddings**
Vectors representing meaning of token within a context
To obtain from BERT
- Assume we have sequence of input tokens x1,...xn and we are interested in embeddings for token xi
- We take output vector yi from final layer of model
- This is the embedding.

**Fine tuning**
- Covered ad hoc in other weeks