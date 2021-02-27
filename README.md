# AI and-Big Data Project -- Hate Speech Detection

The aim of this project is to detect hate speech and offensive speech from normal sayings on social media.  
**WARNING:** The data, lexicons, and notebooks all contain content that is racist, sexist, homophobic, and offensive in many other ways.

## Dataset : 
The model is built based on 3 sets of data collected from Twitter and Gab, an American alt-tech social networking service known for its far-right userbase to diversify the samples and to encounter the unbalanced dataset.  

### First Dataset : 
The base dataset contains around 25000 tweets with 3 categories: hate speech, offensive language and neither collected by [Thomas Davidson, Dana Warmsley, Michael Macy, and Ingmar Weber(2017)](https://data.world/thomasrdavidson/hate-speech-and-offensive-language). 5 columns in the dataset represents the following :  

`count` = number of CrowdFlower users who coded each tweet (min is 3, sometimes more users coded a tweet when judgments were determined to be unreliable by CF).

`hate_speech` = number of CF users who judged the tweet to be hate speech.  

`offensive_language` = number of CF users who judged the tweet to be offensive.  

`neither` = number of CF users who judged the tweet to be neither offensive nor non-offensive.  

`class` = class label for majority of CF users.  
0 - hate speech,  
1 - offensive language,  
2 - neither  

`tweet` = content of the tweet  

### Second Dataset : 
On top of the first dataset, we add extract hate speech tweets from [Kaggle](https://www.kaggle.com/dv1453/twitter-sentiment-analysis-analytics-vidya?select=train_E6oV3lV.csv) provided by [Analytics Vidhya](https://datahack.analyticsvidhya.com/contest/practice-problem-twitter-sentiment-analysis/#LeaderBoard). Since this dataset (train.csv) only contains hate speech and non-hate speech, the non-hate speech tweets cannot be told if they are offensive or normal tweets. Thus **2177 tweets of hate speech** are added to enrich the number of hate speech tweets in the first dataset after screening some of the hate speech manually. **Ambiguous or short tweets** (i.e. <= 3 words) and **pornography advertisements** are **removed** from the dataset deployed in this project.

`label` = class label for Hate Speech  
0 - non-hate speech  
1 - hate speech  

`tweet` = content of the tweet

### Third Dataset : 
This dataset is one of the dataset collected by [Jing Qian, Anna Bethke, Yinyin Liu, Elizabeth Belding, William Yang Wang(2019)](https://github.com/jing-qian/A-Benchmark-Dataset-for-Learning-to-Intervene-in-Online-Hate-Speech). The Gab dataset is used in the project since it is much closer to Twitter comparing to Reddit. Moreover, Gab is known as a haven for extremists including neo-Nazis, white supremacists, white nationalists, the alt-right, and QAnon conspiracy theorists, it has attracted users and groups who have been banned from other social media and users seeking alternatives to mainstream social media platforms. Therefore, hate speech is not uncommon on this platform and this dataset can give us the diversity of hate speech in terms of topics and words.  

We select **7363 post** which is part of the dataset where `hate_speech_idx` is either '1' or '2' as we would like to not only keep the length of the sentences similar to tweets, but also identify the hate speech at the beginning of the conversion, i.e. spontaneous hate speech, instead of hare speench provoked by other users.   

The struture of the dataset :   
`id` =	the ids of the post in a conversation segment  
`text` =	the text of the posts in a conversation segment  
`hate_speech_idx` =	a list of the indexes of the hateful posts in this conversation  
`response` =	a list of human-written responses  

### Data Distribution in Total :   
```
hate speech:
    Total: 34323
    hate: 10970 (31.96% of total)

offensive speech:
    Total: 34323
    Offensive: 19190 (55.91% of total)

neither:
    Total: 34323
    Neither: 4163 (12.13% of total)
```
    
    
## Acknowledgements :
https://arxiv.org/abs/1909.04251 
https://data.world/thomasrdavidson/hate-speech-and-offensive-language 
https://datahack.analyticsvidhya.com/contest/practice-problem-twitter-sentiment-analysis/#LeaderBoard
