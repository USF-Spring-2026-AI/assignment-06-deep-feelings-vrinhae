[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/mW4WPbr-)
# A06 - Deep Feelings

## enhancement implements
the enhanced system used:
- stopword removal
- lemmatization (wordnet)
- bigram features

as well as an indivudal test for each enhancement to see how they each performed on their own

## results

system  |   accuracy
====================
baseline    |   62.22%
stopwords only  |   61.36%
lemmatization only  |   61.80%
bigrams only    |   63.80%
all 3 combined  |   64.78%
embeddings (spaCy)  |   55.83%

## analysis

### enhanced system (did improve performance)

**what was the magnitude of the performance increase ?**
    the enhanced system-stopwords rmoval, lemmatization, and bigrams-improved the accuract from 62.22% to 64.78%, a 2.56% increase. While minimal, an improvement is still an improvement. Detecting sentiment in tweets is difficult, even humans have issues picking up on tone online sometimes.

**could the performance increase be due to other factors ?**
    yes. when tested on its own, stopwords removal and lemmatization both have a slighty lower accuracy score than the baseline. bigrams was the only enhancement that increased the accuracy on its own. regardless, the best result came from combining all three. this suggests that the enhancements have a compounding effect; bigrams provide additional contexts that makes the reduced, lemmatized vocabulary more meaningful.

## embedding systems (did not improve performance)

**why didnt it work ?**
    the spaCy en_core_web_md model was trained on formal english text such as news articles and web content, thus gets confused with the modern, slang filled language of social media. when spaCy encounters an unknown token, i.e misspelling, abbrevation, or internet specific expressions, it returns a zero vector, leading to a large portion of the tweet content getting lost. this results in the tweet vectors consisently unrepresenting the acutal sentiment of the text and underperform.

**how can it be improved?**
    the most firect improvement would be using a model that is pre-trained on social media lingo, like a twitter specific word embedding model, so that common slang and abbreviations are better represented. however, this still comes with limitations, social media lingo is deeply tied to the current internet culture and is constantly evolving and changing at a speed a model cannot follow. an alterative possibility is to fine-tune a large language model like bert on tweet sentiment data, as these modesl have a larger vocabulary and better handle on unkown terms. at the end of the day though, the informal, niche nature of tweets means there will be a ceiling on how well any pre-trained embedding model can perform without continuous retraining.