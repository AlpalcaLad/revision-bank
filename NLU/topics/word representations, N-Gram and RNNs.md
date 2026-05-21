**Embeddings**
Learned representations of the meaning of words
Based on vector semantics
- meaning is defined by distribution of word in language use
- Words with similar contexts (e.g. neighbouring words) tend to have similar meanings
- ![[Pasted image 20260521130159.png|354]]

**Sparse vectors**
Term frequency-Inverse document frequency (TF-IDF)
- term frequency => tf_t,d = log(count(t,d) + 1)
- document frequency => idf_t = log(N / df_t)
	- Where N is the number of documents and df_t is the number of documents with term t
- W_t,d = tf_t,d * idf_t

Positive Pointwise Mutual Information (PPMI)
- Based on a term-term (word co-occurence matrix)
- Extent to which two words co-occur in corpus
- Pointwise Mutual Information
	- ![[Pasted image 20260521130911.png|219]]
	- PMI ranges from negative to positive infinity
- ![[Pasted image 20260521130852.png|269]]
	- ie replace all negative with 0

PPMI weight of word wi in context cj
![[Pasted image 20260521130940.png|264]]
![[Pasted image 20260521131106.png|266]]![[Pasted image 20260521131149.png|209]]![[Pasted image 20260521131205.png|236]]
Consider the below example
![[Pasted image 20260521131250.png]]
For w=information, c=data
Pij = P(information and data) = 3982 / 11716
Pi* = P(information) = 7703 / 11716
P* j = P(data) = 5673 / 11716

**Dense vectors**
Word2vec
- skip-gram, predict context given target word
- CBOW (continuous bag of words), predict target word given context
GloVe
- Use frequency that word appears in another words context
- uses ratios of probabilities from co-occurrence matrix
- ![[Pasted image 20260521131942.png|419]]
fastText
- can deal with unknown words
- subword representations i.e. bag of constituent n-grams
- "eating": \<ea eat ati tin ing ng\>
	- skip gram model learned for each n gram
	- word represented as sum of embeddings of constituent n-grams
- e.g. "eataly" embeddings for eat can still capture meaning

**Sparse vs Dense**
Sparse vectors, each dimension corresponds to either
- Document in large corpus (e.g. term document matrix in TF-IDF)
- Word in vocabulary (e.g. in a term-term matrix in PPMI)
- High dimension number (10k+ with mostly 0s)
Dense vectors
- Lower dimension number (e.g. 100-500)
- Models are often more likely to succeed with fewer weights

**Embedding usefulness**
- Detecting word similarity, measuring cosine similarity using two vectors
- Identifying related words, listing words by decreasing cosine similarity
- Clustering: induce hierarchical relationships
- Visualisations- using t-SNE to project into 2d
- Historical semantics
	- How words change meaning over time
	- ![[Pasted image 20260521132633.png|387]]

**Static Embeddings**
Each word mapped to one fixed embedding
A single vector learned for each unique word
If word has different meaning depending on context we need contextual embeddings

**N-grams**
see how often words occur
- Single words (unigrams)
- Word pairs (bigrams)
- word triples (trigrams)
Assign probability to each interpretation using statistics
Pick highest probability
Markov assumption
- probability depends only on limited history
- n previous words
special char \<s\> to denote start of sentence

**Maximum likelihood estimation**
![[Pasted image 20260521133603.png|616]]
N is the bigram/trigram etc number
![[Pasted image 20260521133700.png|372]]
![[Pasted image 20260521133635.png|586]]
Order matters e.g. "ham and" != "and ham"

**Generation using n-gram**
Randomly sample word based on start suitability
Randomly sample words conditioned on preceding choice until end symbol or fixed length

**Corpora**
Stats from Corpus
BNC (British national corpus)
- 100M words in 4k docs
- newspaper articles, academic papers, school essays, memos etc.
Google n-gram corpus
- 1 trillion words

**Recurrent neural networks**
![[Pasted image 20260521134620.png|463]]
Use previous word and state to generate next word.
Uses cross-entropy loss, minimising difference
![[Pasted image 20260521134749.png|490]]
![[Pasted image 20260521134817.png|372]]

**Generation**
Autoregressive generation: the word generated at time step t is conditioned on word selected by RNN at time step t-1
![[Pasted image 20260521135013.png|426]]
