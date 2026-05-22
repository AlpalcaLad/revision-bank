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