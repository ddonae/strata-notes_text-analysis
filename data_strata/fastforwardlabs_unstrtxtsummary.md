### Fast Forward Labs
# Unstructured Text Summarization
@ Mike Williams, @mikepar, mike.place


H.P. Luhn: Automatic Creation of Literature Abstracts  
    1. turn text into numbers  
    2. ignore stopwords  
    3. determine top words (high frequency means more important)  
    4. select top words with cutoff (i.e. top 5)  
    5. score and select top sentences based on top words  

Traditional summarization process
- vectorize: document compression
- score: add heuristics to improve (e.g. early and ending sentences, sentences with "in summary")
- select: summarize using top scoring sentences with most words

Improving the vectorization
- this step has the most potential for improving our process
- in compressing the document, we lose a lot of meaning / value of the text
- e.g. searching only for frequent words, not synonyms (movie vs film vs director)

Topic modeling using LDA (Latent Dirichlet Allocation)
- search for frequently occuring topics instead of words
- define topics, consisting of words, map topics to documents, determine distribution of topics
- Creating document summary by using LDA in reverse
    1. use LDA on representative set of training documents to determine topics
    2. categorize distribution of new documents based on trained topics
    3. infer topic distribution for each sentence within the document
    4. to construct the summary, for topics that dominate the document, grab sentences dominated by those topics
- difficulties of LDA:
    - sometimes it is hard to label topics, given unclear word set assigned to each topic
    - LDA is unsupervised, needs humans to evaluate accuracy of model, which sometimes makes it hard to get agreement
- Example: Amazon book reviews: classifying opinions to summarize reviews

But this doesn't solve our compression problem... what are we still losing from the original document?
- doesn't take into account word order, this is important for sentiment
- looking at frequency only means we only judge the popular topics, should we care about the infrequent or unique topics?

Recurrent Neural Networks (RNN)
- using word2vec: quantifies words and relationships by plotting on a 2D plane
    - similar ideas / lines are closer together
    - length implies similar direction and relationship
- using sentence vectorization
    - sentence relatioship: before and after
    - doc2vec
    - SkipThoughts python package
- end to end supervised learning using SkipThoughts
    1. find a training set of summaries (i.e. thebrowser.com, which does pronoun resolution)
    2. score sentences based on similarity to summaries
    3. Use SkipThoughts to encode and vectorize
    4. Train RNN to predict scores given sentence vectors
    5. evaluate on out of sample set and use sentences with top scores for summary

comparing and ranking summarization methods
- amount of training data: RNN > LDA > Heuristics
- domain expertise: Heuristics > LDA > RNN
- computational cost: RNN > LDA > Heuristics
- interpretability: LDA > Heuristics > RNN

So why are we excited about RNN?
- It is great for when computers need to work with the semantic meaning of language
- Crucial for improving artificial intelligence
- Example: translation, google NMT, encoding mandarin characters and decoding to english words
- Check it out: Keras python package