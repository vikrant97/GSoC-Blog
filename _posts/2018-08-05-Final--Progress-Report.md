# Google Summer of Code'18: Work submission 

Hello all!
So 12 weeks of coding period ends today & its time to submit my final working product that would be running on 
CASE High Performance Computing(HPC) cluster. My GSoC project titled "Mutlilingual Neural Machine Translation for 
TV News" was developed under Red Hen Lab.
During the 12 weeks I developed the project on CASE HPC only & the source code can be found at [Neural-Machine-Translation](https://github.com/RedHenLab/Neural-Machine-Translation). The users can go through the project's README for instructions on 
how to use the code for translation purposes, & here I summarise my work.

## Summary:
I am done with a Neural Translation system that is capable of translating source news transcripts & other simple text files
in the following source languages where the target language is English:

1) German
2) French
3) Russian
4) Czech
5) Spanish
6) Portuguese
7) Danish
8) Swedish
9) Chinese

I developed a seperate data processing module for preparation of training data, given the raw data. Training can be done by using 
both RL & normal attention-based encoder-decoder architecture. The default training script uses only attention-based encoder-decoder 
architecure & it can be further fine-tuned with RL to get some improvements. This architecture can be exploited in future for languages
which have low source data. For translation purposes I made two options i.e. one can translate news transcripts with an argument "0" at 
the end of command or argument "1" for translating normal text files.

## How can the MT system be improved?
For the first 5 languages listed above, my NMT system outputs very nice translations & are comparable with that of Google translate.
But the last 4 are not that good as comparable to the first 5. The major reason behind this is the lack of high amount of 
parallel data. For the first 5 we have data around 10 Million sentence pairs whereas for the rest we have only data of 2 million sentences 
pairs. So in future if we get more open source parallel data available, then we can improve the system further. Moreover, one can also try 
out leveraging monolingual data for MT.

## Chinese-English
For Chinese->English MT, I used CWMT corpus, which is the only parallel corpora I am aware of for this language pair & it resulted into a 
BLEU score of only 17 points on the test set of size 3000. The following could be the reasons for such low BLEU score:
1) The training corpora is not 100% parallel. I mean to say, that it have been extracted from various web sources and the sentence alignment
precision is close to 90% on an average. 
2) Word segmentation: Chinese language contains no spaces between words & phrases. So one needs to do word segmentation first before proceeding 
for Machine Translation. For this purpose I used Stanford Segmenter.  This tool uses statistical approaches like CRF classfier for segmenting text. 
I think Neural Net based approach would be more efficient. The developers can spend time on introducing a better segmentation approach targetting 
improvements in the BLEU score for NMT. 

Note: The MT results & other stats of remaining language pairs can be found in my previous blogs. 

## Conclusion
I am very thankful to all of my mentors Prof. Francis Steen & Karan Singla. Also, I would like to thank Michael Pacchioli sir, for all the help 
he provided on Red Hen Lab’s Slack channel. I express my gratitude to Prof. Mark Turner for all the support.
I had a very wonderful experience working with Red Hen Lab under GSoC'18 & hope to remain in touch and keep contributing.

