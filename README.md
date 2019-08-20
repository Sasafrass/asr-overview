# Overview of ASR software
This github was instantiated with the intent of providing an overview of Systematic Review Software available to researchers. First and foremost, a distinction is made between two types of software products: ones that use machine learning techniques to expedite the abstract screening process of systematic reviews and ones that do not use machine learning techniques. A short summary follows of each software product, which is also summarized in the following table:

# Table Overview of ASR software that use machine learning techniques
| Feature  | Automated Systematic Review | Rayyan | Abstrackr | Swift | RobotAnalyst
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| Input | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Textual  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Clustering  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Keywords  |   | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Stemming  |   | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Active Learning  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Algorithm  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Stopping Criterion  |  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Ready to use | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Simulations run | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Maintained  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |
| Results | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: |


# Software products that use machine learning techniques

## Automated Systematic Review

## Rayyan
Rayyan takes a set of references as input and yields the subset of relevant references as output.  Rayyan currently supports importing a set of references in RIS, BibTex, CSV, PubMedXML,  Web  of  Science,  and  EndNote  formats  (Ouzzani  etal., 2016).  Moreover, Rayyan uses textual features such as MeSH terms in the form a word cloud, and a user-specified list  of  keywords  that  signify  either  inclusion  or  exclusion. All words are represented by their stems and these features are  used  as  input  to  a  support  vector  machine  (Ouzzani  etal., 2016).  When it comes to active learning, Rayyan uses a  5-star system  to  present  the relevance  of  each reference, and by default the references are ranked based on their level of relevance, presenting those references that are most likely to be relevant on top. The stopping criterion Rayyan uses is when all of the references have been labeled or when no further improvements to the model can be made (Ouzzani et al., 2016).

## Abstrackr
Abstrackr is  another  software  product  that  aims  to  aid reviewers by automating systematic reviews using machine learning techniques. Abstrackr accepts a set of PubMed IDs, an RIS file or a file delimited by tabs (Wallace et al., 2012). Similar to Rayyan, both the labels for the features, words or n-grams,  and the labels for citations are fed into a support vector machine (Wallace et al., 2012). Abstrackr also makes use of the dual supervision paradigm,  enabling researchers to  specify  sets  of  keywords  that  may  indicate  relevance or  irrelevance,  thereby  leveraging  their  domain  knowledge(Wallace et al., 2012). Next, the  lead  reviewer  is  prompted  to  select  the  active  learning  strategy  they  wish  to  use: certainty-based, uncertainty-based or random sampling.  This strategy determines the order in which the references are presented. However, in active learning it is frequently assumed that we are dealing  with  one  oracular  annotator  who  makes  no  errors when providing classifications (Wallace et al., 2012). This is an assumption which may not always be satisfied.  Multiple annotators with different levels of expertise may be working on the same dataset. A new component in active learning is  proposed,  in  which  most  labeling  is  done  by  less  experienced reviewers, and whenever they encounter references that they experience as more troublesome to classify, these references are re-assigned to the more experienced reviewers to ensure rapid yet highly accurate classifications (Wallace etal., 2012).  Finally, the stopping criterion Abstrackr has implemented is that the process stops when the model predicts that none of the remaining unlabeled references are possibly relevant (Wallace et al., 2012)

## Swift-ActiveScreener
Thirdly,  SWIFT-ActiveScreener also  uses  text  mining and machine learning techniques to expedite the systematic review process. It accepts EndNote, Mendeley, Zotaro, andSWIFTReview  files,  a  set  of  PubMed  IDs  or  an  exported XML  file  of  a  PubMed  search  as  input, and it outputs a set of relevant references (Howard,  2009). For its textual features, SWIFT-ActiveScreener uses a bag-of-words model, including bi- and trigram  representations and its words are represented by their respective stems.  Moreover, SWIFT-ActiveScreener    uses    length-normalized    TF-IDF representations  and  latent  dirichlet  allocation  (Blei  et  al., 2003) for clustering purposes (Howard et al., 2016). Subsequently,  these  word  score  features  and  topic features are fed into a logistic regression model. Using these features and a set of manually screened  references  it  will train a logistic regression model which will output a 1 or a 0 for an inclusion or an exclusion respectively (Howard et al., 2016). As of yet, further active learning has not been implemented, although it is stated that implementing active learning is being looked into as a means of improving SWIFT-ActiveScreener’s classification model (Howard et al., 2016). Ultimately,  it  was  ascertained  again  that  finding  a  suitable stopping  criterion  for  when  to  signal  the  reviewer  to  stop screening is not an easy task, and that finding a suitable solution is being looked into (Howard et al., 2016). SWIFT-ActiveScreener currently uses random sampling, and on top of this an extra model has been implemented to predict the remaining amount of classifications to be made (Przybyła et al., 2018)

## RobotAnalyst
RobotAnalyst currently accepts a set of references in RIS format. A number of these references have to be classified manually in order for RobotAnalyst to train an initial model. For its textual features, each document is passed through a Part-Of-Speech tagger which also performs stemming on all words. Subsequently, similar to SWIFT-ActiveScreener, latent dirichlet allocation is used for topic modelling purposes. Further clustering is done using spectral clustering which also uses TF-IDF scores. These feature representations are ultimately fed into a support vector machine.

## Colandr
Colandr aims to assist reviewers with screening references by taking in a set of references in BibTeX format. Colandr requires the manual classification of 10 references as included before it will train an initial model. For its machine learning implementation, Colandr makes use of the word2vec model. The word2vec model is used to learn word vector representations which can subsequently be used to look for patterns based on the search terms. Colandr then uses a linear model to learn which combinations of these vectors indicate relevant references. Similar in a sense to the way in which active learning is employed by Rayyan, Abstrackr, and RobotAnalyst, Colandr uses the reviewer's classifications to improve the model and to calculate the references' predicted relevance to determine which reference to present next using certainty-based active learning. Currently it is not clear what stopping criterion Colandr uses for this active learning cycle so the decision is left to the reviewer.

## EPPI-Reviewer
EPPI-Reviewer is a text-mining tool that takes in a set of references in a variety of formats which can be converted to the accepted RIS Format by using their RIS export utility. EPPI-Reviewer is then able to apply document clustering by using Lingo3G clustering. Next, by using automatic term recognition, EPPI-reviewer finds terms in prior included references which can be used to retrieve other relevant references. Active learning is implemented for priority screening and the remaining references are ordered by their potential relevance. The stopping criterion is left to the reviewer.

# Software products that do not use machine learning techniques
