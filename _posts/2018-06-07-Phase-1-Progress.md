By the end of community bonding period, I was done with all the requirements elicitation and the designing process.
During this phase, I read many research papers and by drawing inspiration from my research work on Hindi<->English
Machine Translation, I reached a conclusion to build a Multilingual Neural Machine Translation System for TV News 
using **Reinforcement Learning** on the top of neural **attention based encoder-decoder** architecture. This system is 
different from normal NMT system which employs **maximum log-likelihood** training on a given dataset.

This phase is directly headed towards the coding phase of the project. I list down my progress on the project in a
week-wise manner.

# Week-1 (14 May - 21 May, 2018)

Data preparation and preprocessing are very important steps for any Natural Language Processing Task. Machine Translation
being one of the NLP tasks, requires a large parallel corpus. I used the large open source parallel dataset available on
[Europarl](http://www.statmt.org/europarl/) site. As documented in my proposal, I have to deliver a working **German->English
Machine Translation** system at the end of the Phase-1 of the coding period. So, I took the German-English Europarl parallel corpus at first, containing approximately 19 Lakhs parallel sentences and started building a data preprocessing pipeline for the same. Assuming the data to be in a parallel text format, I went forward to write preprocessing scripts for the dataset, which would handle tokenization, removal of some unwanted characters and removal of puctuation marks if needed. I trained
a model on this dataset using my code but later realised that this code contain some empty lines and mismatch of those lines too. So, I wrote a new script **strip.py** that handles the removal of empty lines and its correspondances from the parallel text. After this, I checked the effectiveness of the processed dataset by training a model on this dataset. With this I was done with data preparation and processing pipeline for our MT system.
