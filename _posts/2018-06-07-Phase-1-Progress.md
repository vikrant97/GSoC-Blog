By the end of community bonding period, I was done with all the requirements elicitation and the designing process.
During this phase, I read many research papers and by drawing inspiration from my research work on Hindi<->English
Machine Translation, I reached a conclusion to build a Multilingual Neural Machine Translation System for TV News 
using **Reinforcement Learning** on the top of neural **attention based encoder-decoder** architecture. This system is 
different from normal NMT system which employs **maximum log-likelihood** training on a given dataset.

This phase is directly headed towards the coding phase of the project. I list down my progress on the project in a
week-wise manner.

# Week-1 (14 May - 20 May, 2018)

Data preparation and preprocessing are very important steps for any Natural Language Processing Task. Machine Translation
being one of the NLP tasks, requires a large parallel corpus. I used the large open source parallel dataset available on
[Europarl](http://www.statmt.org/europarl/) site. As documented in my proposal, I have to deliver a working **German->English
Machine Translation** system at the end of the Phase-1 of the coding period. So, I took the German-English Europarl parallel corpus at first, containing approximately 19 Lakhs parallel sentences and started building a data preprocessing pipeline for the same. Assuming the data to be in a parallel text format, I went forward to write preprocessing scripts for the dataset, which would handle tokenization, removal of some unwanted characters and removal of puctuation marks if needed. I trained
a model on this dataset using my code but later realised that this code contain some empty lines and mismatch of those lines too. So, I wrote a new script **strip.py** that handles the removal of empty lines and its correspondances from the parallel text. After this, I checked the effectiveness of the processed dataset by training a model on this dataset. With this I was done with data preparation and processing pipeline for our MT system.

# Week-2 (21 May - 27 May, 2018)

After completing data processing pipeline in week-1, I started on working on main codebase. As I have to build the entire pipeline on **CASE HPC**. I gathered the information about all the required packages that are needed to be installed on HPC. 
I installed all the required packages in Python2 virtual environment and freezed it to get a **requirements.txt** file. I soon got access to the redhen servers, thanks to Mr. Mark Turner. Then I soon started setting up the entire codebase over there. I used libraries for encoder-decoder architecture that have been included in **lib** folder of the source code on github. I spent the rest of the week in building training module and checking its effectiveness on the given dataset and its performance on HPC cluster. Performance of the code can be increased with respect to the availability of many number of CPU nodes on HPC and will take up this task later.

# Week-3 (28 May - 3 June, 2018)

After successfully building the training module in the past week, I proceeded towards the development of the translation module. In the early days of this week, I spend time on building the translation module for any general monolingual text corpus. I got a BLEU score of 26.27 on newstest2016 and used newstest2014 as a validation test set. The translations for newstest2016 were quite good with a few number of words marked as unknown (<unk>) and so I proceeded further on building the pipeline for Redhen's TV News Transcripts. I wrote two python scripts for handling the input and output format for the input news transcripts and the translated news transcipts. With this I got the required output format for the translated transcripts containing a Header Block at the start, a Credit Block at the middle and then we have translated news captions having timing information at  the sentence level.
  
# Week-4 (4 June - 10 June, 2018)

With the translation module being built during last week, I translated a sample German news transcript and found that the my model is not perfect for this TV News domain and had many words marked as <unk> in the translated output. So, I searched for another freely available corpora and found CommonCrawl and NewsCommentary Corpus. I concatenated these datasets with my Europarl dataset to get a huge parallel corpus of size 45 Lakhs. The main advantage of this is that the model get more training samples and one that's more important is that I am training a model on a data which contains sample from news domain too. I further applied Byte Pair Encoding to the processed dataset with the help of subword-nmt. This reduces the vocabulary size of the model to a huge extent and also incorporates subword features in the training set. This procedure increased the BLEU score for the newstest2016 to almost 34.30, that is a huge increase indeed. 
  
## End-Product of Phase-1

With the end of Phase-1 of the coding period for GSoC'18, I deliver a working **German->English Neural Machine Translation System**. The entire codebase is available on my github repository and the pipeline is properly working on my account on **CASE HPC**. I have coded it in such a way that any new language pair can be added easily by just providing the processed dataset using my data processing scripts. With this I conclude that I have achieved the milestones as per documented in my proposal.


