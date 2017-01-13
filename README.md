## Trumpiest Sentences

You could say that Donald Trump has a... distinct way of speaking. He doesn't talk the way other politicians do (even ignoring his accent), and the contrast between him and Clinton is pretty strong. But can we figure out what differentiates them? And then, can we find the most... Trump-ish sentence? 

That was the challenge my friend [Spencer](http://www.clearerthinking.org) posed to me as my first major foray into data science, the new career I'm starting. It was the perfect project: fun, complicated, and requiring me to learn new skills along the way. To find out the answers, read on! The results shouldn't be taken too seriously, but they're amusing and give some insight into what might be important to each candidate and how they talk about the political landscape. Plus, it serves to demonstrate the data science techniques I'm learning for as a portfolio project. 

If you want to play with the model yourself, I also put together an [interactive javascript page for you:](https://rawgit.com/jessegalef/TrumpiestSentences/master/interactive.html) you can test your judgment compared to its predictions, browse the most Trumpish/Clintonish sentences and terms, and enter your own text for the model to evaluate. [![screen-shot-2016-10-19-at-7-25-47-pm](https://measureofdoubt.files.wordpress.com/2016/10/screen-shot-2016-10-19-at-7-25-47-pm.png)](https://rawgit.com/jessegalef/TrumpiestSentences/master/interactive.html) 


# The Trump-iest and Clinton-est Sentences and Phrases from the 2016 Campaign:

| Clinton | Trump |
| --- | --- |
| Top sentence: "That's why the slogan of my campaign is stronger together because I think if we work together and overcome the divisiveness that sometimes sets americans against one another and instead we make some big goals and I've set forth some big goals, getting the economy to work for everyone, not just those at the top, making sure we have the best education system from preschool through college and making it affordable and somp[sic] else." 
-- [Presidential Candidates Debate](http://www.c-span.org/video/?414227-1/presidential-nominees-debate-washington-university) 
Predicted Clinton: 0.99999999999
Predicted Trump: 1.04761466567e-11 | Top sentence: "As you know, we have done very well with the evangelicals and with religion generally speaking, if you look at what's happened with all of the races, whether it's in south carolina, i went there and it was supposed to be strong evangelical, and i was not supposed to win and i won in a landslide, and so many other places where you had the evangelicals and you had the heavy christian groups and it was just -- it's been an amazing journey to have -- i think we won 37 different states." 
-- [Faith and Freedom Coalition Conference](http://www.c-span.org/video/?410912-1/faith-freedom-coalition-holds-annual-conference) 
Predicted Clinton: 4.29818403092e-11 
Predicted Trump: 0.999999999957 |

# Top Terms

Clinton | Term Multiplier | Trump | Term Multiplier
 --- | --- | --- | ---
my husband | 12.95569231 | tremendous | 14.57693804
recession | 10.28021868 | guy | 10.25536396
attention | 9.7298399 | media | 8.60537408
wall street | 9.441752364 | does it | 8.24397873
grateful | 9.236325223 | hillary | 8.159573602
or us | 8.396391086 | politicians | 8.004534204
citizens united | 7.979481603 | almost | 7.831284383
mother | 7.20424566 | incredible | 7.428223404
something else | 7.170459383 | illegal | 7.165490368
strategy | 7.054860595 | general | 7.039792849
clear | 6.811276649 | frankly | 6.970085611
kids | 6.746295256 | border | 6.892996726
gun | 6.69476012 | establishment | 6.847398112
i remember | 6.514376761 | jeb | 6.767060387
corporations | 6.514201483 | allowed | 6.728067915
learning | 6.364835299 | obama | 6.485459632
democratic | 6.284717384 | poll | 6.246518578
clean energy | 6.243281841 | by the way | 6.216666573
well we | 6.147347271 | bernie | 6.204384831
insurance | 6.146318048 | ivanka | 6.091535276
grandmother | 6.123896207 | japan | 5.986565276
experiences | 6.004509308 | politician | 5.96476051
progress | 5.949958359 | nice | 5.934816536
auto | 5.909459505 | conservative | 5.900407426
climate | 5.892153302 | islamic | 5.777139198
over again | 5.858994648 | hispanics | 5.768403385
often | 5.803805491 | deals | 5.47324447
a raise | 5.715071741 | win | 5.431441417
about what | 5.687802158 | guys | 5.3453015
immigration reform | 5.627447962 | believe me | 5.324786849


## Other Fun Results:

![pronouns](https://measureofdoubt.files.wordpress.com/2016/10/pronouns.png)

## Cherrypicked pairs of terms:

| Clinton | | Trump | |
|---|---|---|---|
| **Term** | **Multiplier** | **Term** | **Multiplier** |
| president obama | 3.27 | obama | 6.49 |
| immigrants | 3.40 | illegal immigrants | 4.87 |
| clean energy | 6.24 | energy | 1.97 |
| the wealthy | 4.21 | wealth | 2.11 |
| learning | 6.36 | earning | 1.38 |
| muslims | 3.46 | the muslims | 1.75 |
| senator sanders | 3.18 | bernie | 6.20 |

# How the Model Works:

### Defining the problem: What makes a sentence "Trump-y?"

> I decided that the best way to quantify 'Trump-iness' of a sentence was to train a model to predict whether a given sentence was said by Trump or Clinton. The Trumpiest sentence will be the one that the predictive model would analyze and say "Yup, the chance this was Trump rather than Clinton is 99.99%". Along the way, with the right model, we can 'look under the hood' to see what factors into the decision. 

**Technical details:** The goal is to build a classifier that can distinguish between the candidate's sentences optimizing for ROC_AUC, and allows us to extract meaningful/explainable coefficients.

### Gathering and processing the data:

> In order to train the model, I needed large bodies of text from each candidate. I ended up scraping transcripts from events on C-SPAN.org. Unfortunately, they're uncorrected closed caption transcripts and contained plenty of typos and misattributions. On the other hand, they're free. I did a bit to clean up some recurring problems like the transcript starting every quote section with "Sec. Clinton:" or including descriptions like [APPLAUSE] or [MUSIC]. (Unfortunately, they don't reliably mark the end of the music, and C-SPAN sometimes claims that Donald Trump is the one singing 'You Can't Always Get What You Want.') 

**Technical details:** I ended up learning to use Python's Beautiful Soup library to identify the list of videos C-SPAN considers campaign events by the candidates, find their transcripts, and grab only the parts they supposedly said. I learned to use some basic regular expressions to do the cleaning. My scraping tool [is up on github](https://github.com/JesseGalef/TrumpiestSentences/blob/master/cspan%20candidate%20scraper.ipynb), and is actually configured to be able to grab transcripts for other people as well.

### Converting the data into usable features

> After separating the large blocks of text into sentences and then words, I had some decisions to make. In an effort to focus on interesting and meaningful content, I removed sentences that were too short or too long - "Thank you" comes up over and over, and the longest sentences tended to be errors in the transcription service. It's a judgement call, but I wanted to keep half the sentences, which set cutoffs at 9 words and 150 words. 34,108 sentences remained. A common technique in natural language processing is to remove the "stopwords" - common non-substantive words like articles (a, the), pronouns (you, we), and conjunctions (and, but). However, following [James Pennebaker's research](http://www.secretlifeofpronouns.com/), which found these words are surprisingly useful in predicting personality, I left them in. Now we have what we need: sequences of words that the model can consider evidence of Trump-iness. 

**Technical details:** I used NLTK to tokenize the text into sentences, but wrote my own regular expressions to tokenize the words. I considered it important to keep contractions together and include single-character tokens, which the standard NLTK function wouldn't have done. I used a CountVectorizer from sklearn to extract ngrams and later selected the most important terms using a SelectFromModel with a Lasso Logistic Regression. It was a balance - more terms would typically improve accuracy, but water down the meaningfulness of each coefficient. I tested using various additional features, like parts of speech and lemmas (using the fantastic Spacy library) and sentiment analysis (using the Textblob library) but found that they only provided marginal benefit and made the model much slower. Even just using 1-3 ngrams, I got 0.92 ROC_AUC.

### Choosing & Training the Model

> One of the most interesting challenges was avoiding overfitting. Without taking countermeasures, the model could look at a typo-riddled sentence like "Wev justv don'tv winv anymorev." and say "Aha! Every single one of those words are unique to Donald Trump, therefore this is the most Trump-like sentence ever!" I addressed this problem in two ways: the first is by using regularization, a standard machine learning technique that penalizes a model for using larger coefficients. As a result, the model is discouraged from caring about words like 'justv' which might only occur two times, since they would only help identify those couple sentences. On the other hand, a word like 'frankly' helps identify many, many sentences and is worth taking a larger penalty to give it more importance in the model. The other technique was to use batch predictions - dividing the sentences into 20 chunks, and evaluating each chunk by only training on the other 19\. This way, if the word 'winv' only appears in a single chunk, the model won't see it in the training sentences and won't be swayed. Only words that appear throughout the campaign have a significant impact in the model. 

**Technical details:** The model uses a logistic regression classifier because it produces very explainable coefficients. If that weren't a factor, I might have tried a neural net or SVM (I wouldn't expect a random forest to do well with such sparse data.) In order to set the regularization parameters for both the final classifier and for the feature-selection Lasso Logistic Regressor, I used sklearn's cross-validated gridsearch object, optimizing for ROC_AUC. During the prediction process, I used a stratified Kfold to divide the data in order to ensure each chunk would have the appropriate mix of Trump and Clinton sentences. It was tempting to treat the sentences more like a time series and only use past data in the predictions, but we want to consider how similar old sentences are to the whole corpus.

### Interpreting and Visualizing the Results:

> The model produced two interesting types of data: how likely the model thought each sentence was spoken by Trump or Clinton (how 'Trumpish' vs. 'Clintonish' it is), and how any particular term impacts those predicted odds. So if a sentence is predicted to be spoken by Trump with estimated 99.99% probability, the model considers it extremely Trumpish. The term's multipliers indicate how each word or phrase impacts the predicted odds. The model starts at 1:1 (50%/50%), and let's say the sentence includes the word "incredible" - a Trump multiplier of 7.42\. The odds are now 7.42 : 1, or roughly 88% in favor of Trump. If the model then sees the word "grandmother" - a Clinton multiplier of 6.12 - its estimated odds become 7.42 : 6.12, (or 1.12 : 1), roughly 55% Trump. Each term has a multiplying effect, so a 4x word and 2x word together have as much impact as an 8x word - not 6x. 

**Technical details:** In order to visualize the results, I spent a bunch of time tweaking the matplotlib package to generate a graph of coefficients, which I used for the pronouns above. I made sure to use a logarithmic scale, since the terms are multiplicative. In addition, I decided to teach myself enough javascript to learn to use the D3 library - allowing interactive visualizations and the guessing game where players can try to figure out who said a given random sentence from the campaign trail. There are a lot of ways the code could be improved, but I'm pleased with how it turned out given that I didn't know any D3 prior to this project.