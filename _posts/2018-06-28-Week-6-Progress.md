# Week-6 ( 18 June - 24 June, 2018)

This week I took up the task for increasing the performance of the NMT pipeline in terms of time taken for training.
My NMT pipeline uses multiple CPUs and one GPU on a single node. I wanted to extend it to use multiple GPUs and multiple nodes.
Dataparallel module and distributed modules in pytorch are useful for this task. I am spend a lot of time in making the dataparallel 
module work in pytorch 0.3.1 but had no luck. Moreover in this week, I made a French->English translation model added it to the pipeline.
I have evaluated the model using BLEU score for different types of n-grams. The BLEU scores are 65.5, 39.0, 25.2, 16.7 for 4-gram, 
trigram, bigram and unigram respectively. The model is evaluated on newstest2014 and used newstest2013 as development set. I also extracted
parallel corpora from the Redhen news transcripts and used it for training.
