# Week-5 (10 June - 17 June, 2018)

This week was the evaluation week and I handled the issues in my NMT pipeline raised by Redhen members. 
My system was giving very good translations for standard nestests but it gave very poor translations for
German news transcript. Thanks to Prof. Francis Steen for raising an issue in the translation. I forgot 
to apply the shared word piece vocabulary to the input news transcript. But I removed all the discrepancies
in the code, and now the translations for the news transcript are at par with Google translate. Moreover, I
have also initiated experiments on German->English translation to improve the translations further.
          I have also started working on French->English Translation. I have used Europarl and CommonCrawl
corpus. Since, we are dealing with TV news domain, any samples of text in TV news domain would help a lot in
learning some patterns. With this aim, I extracted the files from Galina software of redhenlab which contains
French transcripts and also contain English translations too. So, I tried extracting parallel copora from these 
news transcripts but faced a few problems:
1) In an ideal case, a sentence with CC1 tag should be followed by a sentence with a CC2 tag and vice versa.
2) But in some cases, a CC1 tag was followed by a CC1 tag or CC2 tag was followed by a CC2 tag.

So, to tackle this I wrote a python script to extract parallel data from these news transcripts by taking only
those instances where a CC1 tag was followed by a CC2 tag. I avoided wasting any piece of information while processing
and succeeded in generating a Parallel TV News  corpus of size 2.45 Lakhs for French-English. Combining this dataset with
Europarl and CommonCrawl data, I prepared a dataset of size 5.4 Million. Its a huge dataset, I am expecting a nice BLEU
score which would comparable to scores mentioned in research papers. In the next week, I am taking up the task to increase
the performance of the system my extending it to use Multiple GPUs and Distributed systems.
