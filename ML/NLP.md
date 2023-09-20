- Tibetan is **Scriptio continua** (continuous script)
	- We do not use spacing between units of meaning.
	- We punctuate syllables : does that mean Text to Speech is an easier problem ?

* Tokenizer
	* Break up the string into units of meaning
	* Classify the words into types (nouns, verbs, adjectives, or punctuation)
	* Evaluate each word with a function

- Some ways to address Continuous Script
	- develop more complex heuristics
	- querying a table of common special-cases
	- fitting the tokens to a [language model](https://en.wikipedia.org/wiki/Language_model "Language model") that identifies collocations in a later processing step.
		- [[language model]]
			- A probability distribution over words or word sequences.
			- Trigram Probability
				- [[Context problem]] due to Markov assumption
				- Sparsity problem : most next words have the same probability
			- A Fixed-window neural language modal
				- Context problem
				- solves the Sparsity problem
			- [[RNNs]]
				- [[LSTM]] and [[GRU]]
				- no possibility for parallelization
				- solves the Sparsity problem
			- Transformers
				- [[Attention]] : the model can learn which inputs deserve more attention than others in certain cases.
				- makes parallelization possible
				
<hr>

## ChatGPT

Tokenizing a scriptio continua language like modern Tibetan can be a challenging task because there are no explicit word boundaries in the text. Here are a few approaches you can try:

1.  Use a pre-trained word embedding model: There are pre-trained word embeddings available for Tibetan, such as the one provided by Google's word2vec. You can use these embeddings to tokenize the text by clustering the embeddings into words.
    
2.  Use a morphological analyzer: Tibetan is an inflected language, which means that the ending of a word changes to indicate tense, mood, person, etc. You can use a morphological analyzer to segment the text into its component morphemes, which are the smallest units of meaning in a word.
    
3.  Use a statistical segmenter: You can use a statistical model, such as a hidden Markov model (HMM) or a conditional random field (CRF), to segment the text into words based on patterns in the data. These models can be trained on a labeled dataset of Tibetan text, where the segments are annotated by human experts.
    
4.  Use a rule-based segmenter: You can use a set of predefined rules to segment the text based on [[morphological]], [[syntactic]], or [[orthographic]] features of the language. This approach may not work well for all languages, but it can be effective for Tibetan since it has regular orthography, and rich morphological features.
    

It is important to note that there is no single best approach to tokenizing scriptio continua language, and it is highly dependent on the dataset, the task, and the quality of the data. It is also important to evaluate and compare different tokenization methods in terms of their performance.