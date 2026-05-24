- The task of assigning a label $y_i$ to each token $x_i$ in an input token sequence X
- The output sequence Y will have the same length as X
- Direct alignment gives us a 1-1 mapping

**Part of speech tagging**
- Assign a part of speech (POS) tag to each word in sequence
- Input: sequence $x_1,x_2,\dots x_n$ of words and a tagset
- Ouput: sequence $y_1,y_2\dots y_n$ of tags where output yi corrosponds to input xi
- Can't use dictionary bc words have multiple meanings based on context
	- e.g. "Janet will back (verb) the bill" vs "I hurt my back (noun)"
- Tagsets
	- Penn Treebank
		- Fine grained classifications across categories
		- Highly detailed, can be unintuitive
	- Universal scheme
		- simpler e.g. noun, verb etc
		- Open classes update frequently, language evolves over time
		- Closed classes rarely change
		- ![[Pasted image 20260524202733.png|479]]
	- Both have support for other languages than English

**Semantic role labelling**
- Automatically find semantic role of each argument of each predicate
- in principle: predicate is pre-identified and part of the input
- in practice: most SRL models detect the predicate
- Definitions
	- Predicate: word(s) expressing event i.e. the what
	- Argument: participants in the event, i.e. who where when
	- Semantic role: role that each argument takes
	- ![[Pasted image 20260524203307.png]]
- One sentence can have more than one predicate
- No universally recognised set of semantic roles
	- Popular schemes
		- Proposition Bank (PropBank)
			- Roles are specific to verb and named with numbers
			- ARG0: agent (initiator of action)
			- ARG1: patient (target of action)
			- ARG2: etc. Depends on verb
		- FrameNet

**Named Entity Recognition**
Anything that can be referred to using a proper name
BUT also expressions like dates, time, amounts/prices
