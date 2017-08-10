# DH2017
This repository contains the notebooks I used to create my poster for DH2017, "Playing with Time". I have included a principle component visualization of all of the models for reference in the "models" folder.

These notebooks are provided as reference. 

## Methodology

I downloaded 13,000 PDF files from the Seventh-day Adventist Office of Archives, Statistics, and Research, split by page, and extracted the text into 197,943 txt files.

+ The corpus is composed of 30 different English language titles produced from four regions within the United States.
+ The corpus represents approximately 50% of the materials published during this time and in these places.

I cleaned all of the documents to address standard OCR errors, including line-endings, split words, and burst words. I did not standardize spelling.

I organized the corpus according to five periodization schemes. The text for all five sets of models was preprocessed and modeled using Gensim.

+ Schemes were: Full Corpus, Corpus by Decade, Corpus by Historical Period (1849-1858, 1859-1875, 1876-1896, 1897-1909, 1910-1920), Corpus by Cumulative Decade (2 decade rolling window), Corpus by Cumulative Historical Period (2 period rolling window).
+ I preprocessed each corpus window separately, removing all non-alpha-numeric characters and all words that occurred in less than 20 documents and in more than 30% of documents, and connecting regularly occurring noun phrases.
+ I modeled each corpus window using the LDA modeling algorithm with the “auto” alpha parameter and a random_state of “12”. The number of topics was around 30, though I varied this based on window size, along with the number of iterations and passes, to create the best model for each corpus window. 

To evaluate the models, I compared them across one time slice, as demonstrated in this poster. I selected topics related to health and religious beliefs, and examined the ease of labeling, the match between the topic identification and the document, and the distribution of topics over time. I computed topics prevalence over time by taking the percentage of the total topic weights for each topic which highlights the relative presence of the topic, but is sensitive to missing data.

## References
### Notes
+ [1] Schmidt, Benjamin M. "Words Alone: Dismantling Topic Models in the Humanities" in *Journal of Digital Humanities* 2.1 (2012). http://journalofdigitalhumanities.org/2-1/words-alone-by-benjamin-m-schmidt/ (accessed 01 Nov. 2016). Additional explorations of time and computational modeling include Ted Underwood, "What Can Topic Models of PMLA Teach Us About the History of Literary Scholarship?" in *Journal of Digital Humanities* 2.1 (2012). http://journalofdigitalhumanities.org/2-1/what-can-topic-models-of-pmla-teach-us-by-ted-underwood-and-andrew-goldstone/ (accessed 01 Nov. 2016) and Bethany Nowviskie's recent discussions of the logics of time and archival practices in "Speculative Collections," *Nowviskie.org*, 27 October 2016. http://nowviskie.org/2016/speculative-collections/ (accessed 01 Nov. 2016).
### Sources
+ “Online Archives | Periodicals.” Office of Archives, Statistics, and Research of the Seventh-Day Adventist Church. Accessed 2013. http://documents.adventistarchives.org/Periodicals/Forms/AllFolders.aspx.
### Software
+ Hunter, J. D. “Matplotlib: A 2D Graphics Environment.” *Computing In Science & Engineering* 9, no. 3 (2007): 90–95. doi:10.1109/MCSE.2007.55.
+ McKinney, Wes. “Data Structures for Statistical Computing in Python.” *Proceedings of the 9th Python in Science Conference*, 2010, 51–56.
+ Pérez, Fernando, and Brian E. Granger. “IPython: A System for Interactive Scientific Computing.” *Computing in Science and Engineering* 9, no. 3 (June 2007): 21–29. doi:10.1109/MCSE.2007.53.
+ Řehůřek, Radim, and Petr Sojka. “Software Framework for Topic Modelling with Large Corpora.” In *Proceedings of the LREC 2010 Workshop on New Challenges for NLP Frameworks*, 45–50. Valletta, Malta: ELRA, 2010. https://radimrehurek.com/gensim/tut1.html.

