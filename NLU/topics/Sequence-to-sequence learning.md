Ask yourself 3 questions
- How does the model generate tasks
- What information can it say at each step
- what kind of input-output task are we solving

**Language models**
 [[word representations, N-Gram and RNNs]]
Autoregressive model using RNNs
- generate one word at a time based on previous timestep
- limitations
	- Error propagates over time
	- efficiency issue, no parallelisation
[[Transformers]]
Autoregressive model using transformers
- generate based on all previous outputs and context
	- handles long range context better
	- long range dependency: requiring things far back for context
GPT models
- Transformer decoder-only
	- encoder models theoretically more suitable for generating embeddings
	- decoders are more for generating text
- Positional information embedded with input tokens to encode token order
- At top linear layer and SoftMax to predict next token

**Masked Multihead Self-Attention**
- multiple heads 
	- each learns different aspect of relationships in input
	- masked self-attention
		- hides info from tokens to the right
		- prevents model looking into future
		- ![[Pasted image 20260522213132.png|412]]

If you train a model on left-right (how GPT typically works) there's limitations generalising to languages that read right to left. This can be helped with pre training, meaning a model can still be used.
GPT learns the relationship between context and target word.

**Sequence to sequence learning (Seq2Seq)**
- Input of sequence of tokens
- Output of sequence of token
- \<EOS\> token to separate the two
- Examples, all same abstract structure (input seq -> output seq)
	- Machine translation
	- Summarising text
	- Dialogue with ChatGPT
	- Long-form Question Answering
	- Semantic Parsing
	- Paraphrase generation
- Most tasks can be transformed to this
	- e.g. part of speech tagging, output is input but with POS tags

One approach to Seq2Seq is encoder-decoder models using RNNs
- Source words encoded first
- Target words generated autoregressively

**Machine translation**
- Take sentence in one language
- output in other language with same meaning
- word by word fails
	- grammar and word order fails

**Greedy decoding**
RNNs as we've looked so far use greedy decoding
- They choose the best token each time
	- Locally optimal
	- not necessarily globally optimal
- ![[Pasted image 20260522214533.png|490]]

**Beam search**
- Select best k options (hypothesis) based on softmax
	- Hypothesis = potential candidate
- Pass each hypotheses through decoder to obtain softmax over the next possible tokens
- Score hypothesis
- Repeat until \<\s\> generated then reduce k
- Repeat until k=0
- Probability of a partial translation = sum of log probabilities
- ![[Pasted image 20260522214941.png|423]]

**Evaluation**
BiLingual Evaluation Understudy (BLEU)
- For each word in hypothesis get minimum(count_hypothesis, count_reference)
- BLUE = sum of minimum values for each word/num of words in hypothesis
- ![[Pasted image 20260522215207.png]]
- Prevents system repeating correct word a bunch of times

BLEU-N 
- Generate n-grams for each hypothesis and reference
- for each n-gram in hypothesis get minimum(count_hypothesis, count_reference)
- BLEU-N = sum of minimum for each n-gram/num of n-grams in hypothesis

Higher order is stricter, more consecutive words need to be the same.
Unigram tracks vocab choice
Higher order checks structure and order of words

**Character F-score**
Based on function of number of character n-gram overlaps between hyp and reference
Parameter k = max length of char n-grams to be considered
chrP = ratio of 1 to k-grams in the hypothesis that are in reference averaged
chrR = ratio of 1 to k-grams in reference that occur in hypothesis averaged
![[Pasted image 20260522215627.png|504]]

**Example**
![[Pasted image 20260522215708.png|523]]
Space not counted as a character
![[Pasted image 20260522215834.png|524]]

**Deep learning approach to automatic text summarisation (ATS)**
Summarisation is a natural continuation of machine translation.
Summary text appended to full text in training
Autoregressive means it learns summary continuation to text.
Model can access source as well as any of the target generated so far

**Recall-Oriented Understudy for Gisting Evaluation (ROUGE)**
We don't need to know that full name
Count number of overlapping units (i.e. n-grams) between generated candidate and reference summaries
![[Pasted image 20260522231129.png|477]]

ROUGE-L Longest common subsequence (LCS)-based F-score
Sub sequence not the same as contiguous phrases. We also need to test the order of subsequences
![[Pasted image 20260522231321.png|483]]

ROUGE-S based on skip-bigram co-occurences.
![[Pasted image 20260522231502.png]]
e.g. police gunman could be a skipgram. Skip grams can skip words between.
