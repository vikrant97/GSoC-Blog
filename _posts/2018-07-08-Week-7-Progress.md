# Week-7 (25 June - 3 July, 2018)

During this work period I added two new language pairs to the NMT pipeline. 

## 1) Spanish->English

Spanish-English is an important language pair and is usually present in WMT shared tasks. Due to this I was able to find a good amount
of parallel corpora for this language pair. I used Europarl, News-commentary and UN-corpus as my training corpora. The total size of 
corpora amounts to 84 Lakhs. I was able to achieve very good translation quality on the newstests and TV news transcripts too. I compared
the translations of TV news transcripts with Google translate and it was almost similiar. I evaluated my model on newstest2013 and got a 
BLEU score of 61.6, 34.7, 21.9, 14.5 for 4-gram, trigram, bigram and unigram respectively.
        With the increasing the size of training corpora, some errors occur in the training and testing procedure. These errors are due to
an increase demand of CPU memory. SO I adjusted the Memory per CPU to 4 GB. One might need to increase it more, depending on the size of 
training corpus.

## 2) Portuguese->English

To the best of my knowledge, Portuguese->English language pair have never been introduced in the WMT shared tasks. Due to this, there is very 
less training corpora for Portuguese as compared to previous languages. I trained my system on Europarl corpus containing almost 19 Lakhs
parallel sentences. Since, there were no nestests for this language pair, I evaluated my model on a test set of size 3000 sentences extracted 
from the Europarl corpus only and achieved a BLEU score of 31. But, as my training corpus lacks data in news domain, I am not able to achieve 
good translations on the news transcript. They are just Ok or I would rather say that they are bad with the respect to the translations of 
previously dealt languages like Spanish. Moreover, Google also messes with the translations of the transcript in some way. I couldn't find a 
way to improve the system for Portuguese. I think, in future it could be improved with the help of adding parallel data of news domain. It might 
also be improved by using just a monolingual corpora of News domain and then do some bootstrapping.

