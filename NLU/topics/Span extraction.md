**Applications**
We want to identify which tokens in a given text are relevant for broad queries "I want to know everything"
- Open class document categorisation
	- Keyword extraction
- Relation classification without entity mentions
	- relation extraction
- Relation extraction without relations
	- Open information extraction
- "Query-conditioned" information extraction
	- Machine reading comprehension

**Span extraction**
- Extracting 0..n contiguous spans from a piece of text
- Keywords are contiguous spans of words, representing/summarising essential content
- Relation extraction is getting entities related by a fixed set of relations
	- fixed vocabulary of relations
- Open information extraction ""Domain-independent discovery of relations from text, scaled to diversity/size of corpus"
	- Open vocabulary of relations
	- Convert from text to machine readable structured form
	- Give me everything style request
	- ![[Pasted image 20260522120426.png|337]]
	- Precision vs recall, in practice hard to carry out
		- syntactic and lexical ambiguity
		- "South Africa is in Africa" vs "South Africa is in the south of the African continent" (wording doesn't exactly match query)
		- Normalisation can help
		- Precision vs recall depends on requirements of task
- (Extractive) Machine reading comprehension is finding span in passage best answering question

**Evaluation metrics**
Precision, Recall and F1 score
Accuracy (Exact match) can evaluate MRC systems 
- Often too strict, one token difference assessed as completely wrong
- "apple" vs "an apple" EM: 0, F1: 0.66
F1 score at token level gradually penalises rather than outwrite dismissing
In practice typically Precision at Recall metric used 
- Higher area under curve means better score

**Traditional approaches to info extraction**
Traditionally closely related to info retrieval

Unsupervised keyword extraction (RAKE)
- keywords usually appear between stopwords
- keywords appear in text more often than non-keywords
- Algorithm
	- Identify continuous spans between stopwords
	- Rank and retrieve top K
		- Word frequency or
		- word degree (co-occur freq) or
		- combinations
		- ![[Pasted image 20260522122020.png|333]]
		- freq(i) = Ai,i
			- e.g. freq(cakes) = 3
		- deg(i) = sum(Ai)
			- e.g. deg(cakes) = 7
		- if degree >> freq, word is very general
		- if degree just > freq, word specific in use
		- for bigger phrases sum up scores of each word
	- Join stop-word delimited spans if they co-appear often enough
		- "of the" very important in "lord of the flies"

**Document graph generation**
With direct hyperlinks this is easier. e.g. Googles search engine uses hyperlink based graphs
Without direct we analyse which keywords co-occur
Straightforward linking
- when they mention the same keywords
More complex
- "Central/exclusive keywords"
	- Which keywords are extracted often when referenced
- "essential keywords" 
	- which central keywords are covered by many documents
- "General keywords"
	- Which keywords are referenced often but rarely extracted

**Pattern-based relation extraction**
e.g. crawling biomedical articles identifying all pairs sharing a specific connection
This is where we already have knowledge of patterns and relations
Patterns can be
- Syntactic
- Lexical
- Additional knowledge
	- e.g. X found in Y => Y contains X
		- Uranium, commonly found in Earth's crust implies Earth's crust contains uranium
	- e.g. X(organisation)'s Y(person) => Y is a member of X 
		- Manchester United's Marcus Rashford implies marcus rashford is a member of MU
These are often high precision low recall as they are often very specific and many templates are needed for coverage, introducing noise if too many are introduced,

**Bootstrapping**
Extracting rules without linguistic knowledge
- Find new expressions for known triples
- Extract patterns and add top-K as new
- Apply new patterns to corpus to extract new triple
![[Pasted image 20260522134802.png]]
We want to avoid selecting all new rules as it may add too general rules like "has" in the above example not always meaning contains.
![[Pasted image 20260522134956.png|545]]

**Open information extraction**
"Domain-independent and scalable discovery of relations extracted from text"
Input corpus -> set of relations with arguments (triples)
e.g. ![[Pasted image 20260522135201.png|484]]
Doesn't necessarily follow same format e.g. Einstein being a physicist doesn't involve a verb in the above example.
Unlike relation extraction, no defined list of relations.
Therefore OpenIE systems:
- applicable to many documents
- no domain specific knowledge
- must be quick for single extractions
	- e.g. LLMs would be slow

**DIPRE (Dual Iterative Pattern Relation Expansion)**
- Aim to extract relational tuples from the web of form (PERSON, BOOK TITLE)
- exploiting duality of patterns and relations
	- Good tuples help find good patterns
	- Good patterns help find good tuples
- Start by user-supplied tuples and iteratively
	- Use tuples to find patterns
	- Use patterns to find tuples
- Works by
	- Start with initial sample Rt (e.g. 5 author-title pairs)
	- O <- FindOccurances(Rt, D)
		- Find all occurences of Rt in D
	- P <- GenPatterns(O)
		- Generate patterns based on occurrences with low error rate and ideally high coverage
		- coverage compensated by large database
	- Rt <- MD(P)
		- Update Rt with setr of tuples form documents in D that matched patterns in P
	- If Rt is large enough return else repeat from O step

**Strengths**
Efficient and scalable.
Eliminated need for manually labelled training data

**Limitations**
Data driven system rely on good data.
If you have a few bad tuples, they create bad patterns which give even more bad patterns.
Dramatic scale up means mistakes compound.
Semantic drift - erroneous pattern leading to tuples etc loop

**Language model fine tuning**
Contextualised embeddings such as pre-training language model embeddings are expressive enough to plug into a linear classifier.
In practice 
- we concatenate question and passage as input to language model
- The final layer is multiplied with two vectors to get prob distrib over all tokens (denoting start/end positions) and minimising cross entropy loss between predicted distributions and ground truth.
- Heavy lifting done by pre trained model
If the document is too long for limits (e.g. BERT 512 limit)
- Simple solution
	- Long documents split into n chunks of size m and overlap s with question prepended to each of chunks
	- Overlap reduces risk of span between chunks
	- Model fine tuned on each chunk
- Improvements
	- Summarise context
	- Sliding window approach
	- Active research domain, not solved topic

**End-to-End neural open information extraction**
This can be modelled as a sequence labelling task
- For an input sentence
	- For each verb
		- Expand predicate P (rule based similar to reverb)
		- for each word
			- label as argument (ARGi) or non participating