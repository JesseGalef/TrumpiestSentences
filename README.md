# TrumpiestSentences

![trumpheadshot](https://measureofdoubt.files.wordpress.com/2016/10/trumpheadshot.jpg)You could say that Donald Trump has a... distinct way of speaking. He doesn't talk the way other politicians do (even ignoring his accent), and the contrast between him and Clinton is pretty strong. But can we figure out what differentiates them? And then, can we find the most... Trump-ish sentence? That was the challenge my friend [Spencer](http://www.clearerthinking.org) posed to me as my first major foray into data science, the new career I'm starting. It was the perfect project: fun, complicated, and requiring me to learn new skills along the way. To find out the answers, read on! The results shouldn't be taken too seriously, but they're amusing and give some insight into what might be important to each candidate and how they talk about the political landscape. Plus, it serves to demonstrate the data science techniques I'm learning for as a portfolio project. If you want to play with the model yourself, I also put together an [interactive javascript page for you:](https://rawgit.com/jessegalef/TrumpiestSentences/master/interactive.html) you can test your judgment compared to its predictions, browse the most Trumpish/Clintonish sentences and terms, and enter your own text for the model to evaluate. [![screen-shot-2016-10-19-at-7-25-47-pm](https://measureofdoubt.files.wordpress.com/2016/10/screen-shot-2016-10-19-at-7-25-47-pm.png)](https://rawgit.com/jessegalef/TrumpiestSentences/master/interactive.html) To read about how the model works, I wrote a rundown with both technical and non-technical details below the tables and graphs. But without further ado, the results:

# The Trump-iest and Clinton-est Sentences and Phrases from the 2016 Campaign:

| Clinton | Trump |
| --- | --- |
| Top sentence: "That's why the slogan of my campaign is stronger together because I think if we work together and overcome the divisiveness that sometimes sets americans against one another and instead we make some big goals and I've set forth some big goals, getting the economy to work for everyone, not just those at the top, making sure we have the best education system from preschool through college and making it affordable and somp[sic] else." -- [Presidential Candidates Debate](http://www.c-span.org/video/?414227-1/presidential-nominees-debate-washington-university) Predicted Clinton: 0.99999999999 Predicted Trump: 1.04761466567e-11 Frustratingly, I couldn't download or embed the C-SPAN video for this clip, so here are two of the other top 5 Clinton-iest sentences: [wpvideo uOTaRvfu w=270] [Presidential Candidate Hillary Clinton Rally in Orangeburg, South Carolina](http://www.c-span.org/video/?405395-1/hillary-clinton-campaign-rally-orangeburg-south-carolina) [wpvideo E2mrhDua w=270] [Presidential Candidate Hillary Clinton Economic Policy Address](http://www.c-span.org/video/?327052-1/hillary-clinton-economic-policy-address) | Top sentence: "As you know, we have done very well with the evangelicals and with religion generally speaking, if you look at what's happened with all of the races, whether it's in south carolina, i went there and it was supposed to be strong evangelical, and i was not supposed to win and i won in a landslide, and so many other places where you had the evangelicals and you had the heavy christian groups and it was just -- it's been an amazing journey to have -- i think we won 37 different states." -- [Faith and Freedom Coalition Conference](http://www.c-span.org/video/?410912-1/faith-freedom-coalition-holds-annual-conference) Predicted Clinton: 4.29818403092e-11 Predicted Trump: 0.999999999957 Frustratingly, I couldn't download or embed the C-SPAN video for this clip either, so here are two of the other top 5 Trump-iest sentences: [wpvideo cZvP8Gip w=270] [Presidential Candidate Donald Trump Rally in Arizona](http://www.c-span.org/video/?406905-1/donald-trump-campaign-rally-phoenix-arizona) [wpvideo IeMZd06f w=270] [Presidential Candidate Donald Trump New York Primary Night Speech](http://www.c-span.org/video/?408385-1/donald-trump-primary-night-speech) |
| ## **Top Terms**
| Term | Multiplier |
| my husband | 12.95 |
| recession | 10.28 |
| attention | 9.72 |
| wall street | 9.44 |
| grateful | 9.23 |
| or us | 8.39 |
| citizens united | 7.97 |
| mother | 7.20 |
| something else | 7.17 |
| strategy | 7.05 |
| clear | 6.81 |
| kids | 6.74 |
| gun | 6.69 |
| i remember | 6.51 |
| corporations | 6.51 |
| learning | 6.36 |
| democratic | 6.28 |
| clean energy | 6.24 |
| well we | 6.14 |
| insurance | 6.14 |
| grandmother | 6.12 |
| experiences | 6.00 |
| progress | 5.94 |
| auto | 5.90 |
| climate | 5.89 |
| over again | 5.85 |
| often | 5.80 |
| a raise | 5.71 |
| about what | 5.68 |
| immigration reform | 5.62 |

 | 

| Term | Multiplier |
| tremendous | 14.57 |
| guy | 10.25 |
| media | 8.60 |
| does it | 8.24 |
| hillary | 8.15 |
| politicians | 8.00 |
| almost | 7.83 |
| incredible | 7.42 |
| illegal | 7.16 |
| general | 7.03 |
| frankly | 6.97 |
| border | 6.89 |
| establishment | 6.84 |
| jeb | 6.76 |
| allowed | 6.72 |
| obama | 6.48 |
| poll | 6.24 |
| by the way | 6.21 |
| bernie | 6.20 |
| ivanka | 6.09 |
| japan | 5.98 |
| politician | 5.96 |
| nice | 5.93 |
| conservative | 5.90 |
| islamic | 5.77 |
| hispanics | 5.76 |
| deals | 5.47 |
| win | 5.43 |
| guys | 5.34 |
| believe me | 5.32 |

 |

## Other Fun Results:

![pronouns](https://measureofdoubt.files.wordpress.com/2016/10/pronouns.png)

## Cherrypicked pairs of terms:

| Clinton | Trump |
|---|---|
| **Term** | **Multiplier** | **Term** | **Multiplier** |
| president obama | 3.27 | obama | 6.49 |
| immigrants | 3.40 | illegal immigrants | 4.87 |
| clean energy | 6.24 | energy | 1.97 |
| the wealthy | 4.21 | wealth | 2.11 |
| learning | 6.36 | earning | 1.38 |
| muslims | 3.46 | the muslims | 1.75 |
| senator sanders | 3.18 | bernie | 6.20 |