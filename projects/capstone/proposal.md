# Machine Learning Engineer Nanodegree
## Capstone Proposal
Mario Henrique A. C. Adaniya

December 12nd, 2017

## Proposal

### Domain Background

Back in the days, we couldn't choose what to watch or listen, because we had a media centralized source. The Internet and the advances in technology came as a breakthrough into entertaiment industry. Now, we don't need to listen to what the DJ radio puts in the air, we can just open some music streaming app and choose what to listen. The same for entertaiment in TV, if we can't find nothing interesting to watch, just open a video streaming service and choose something. And to engage more the customer, these streaming services shows always something interesting to us. For example, if you watched a comedie movie, next time you open the movie streaming app, it will recommend some others comedies movies. In music streaming apps, if you listen to a genre, it will suggest other songs and bands from the same genre. 

These are simple examples of **recommender systems**, a system that based on your profile, usage and others data, try to recommend similar items. The 11th ACM International Conference on Web Search and Data Mining (WSDM 2018) challenged the Kaggle ML community to build a better music recommendation system using a donated dataset from KKBOX. The challenge consist in build a music recommendation system. The challenge is that a person can listen to different kinds of genres, sometimes it just like one song from one singer of that genre, and like bands from another genre that is completely the opposite. 

#### Interest

The main problem in recommendation is interesting because there are a lot of techniques that could be applied and mixed up to improve the results. And in this challenge, the dataset is from real users, where some extreme or outlier scenarios might occur and mislead the algorithm. 


### Problem Statement

Nowadays, streaming services are present in our daily life. Video and music recommendations are common as well. If you listen to some genre, the probability that you would listen to another band or song of that genre is higher. But if you like "opposites" genres, it is more difficult to the streaming service suggest something for you. KKBOX, Asia's leading music streaming service and the 11th ACM International Conference on Web Search and Data Mining (WSDM 2018) created a challenge to build a better music recommendation system.

### Datasets and Inputs

The dataset is provided by KKBOX and is available at the WSDM - KKBox's Music Recommendation Challenge. It have a training and a testing dataset where `target` is marked `1` if there are recurring listening event(s) within a month after the user's very first observable listening event, and marked `0` otherwise. Dataset consists of information of the first observable listening event for each unique user-song pair within a specific time duration. Metadata of each unique user and song pair is also provided by KKBOX.

The challenge provides the following files:
- `train.csv` : contains user id, song id, username in screen, the entry point where user listened the song and target.
- `test.csv` : contains the same info from `train.csv`, except target.
- `songs.csv` : song id, length in ms, genre, artist name, composer, lyricist and language.
- `members.csv` : user id, city, age, gender, registration method, registration init and expiration.
- `song_extra_info.csv` : song id, name o the song and ISRC (International Standard Recording Code). 


### Solution Statement

A hybrid approach might help improve the results. As we have the target in training, we could use a supervised learning method and combine with a unsupervised learning method to find new groups into the groups we already discovered in the supervised. Tha supervised method applied will be the K-means clustering, depending on the results and groups created, it will be the input for an unsupervised learning method, ensemble method using random forest. As the ensemble is built from a sample and using the random forest, the final tree is constructed using the best split among random subset of the features trees, it could improve the final result.

### Benchmark Model

The benchmark model will be the public leaderboard from Kaggle. 

### Evaluation Metrics

To evaluate the proposed solution, basics metrics will be used:

 - False-positive rate = False-positive/Number of normal data
 - True-positive rate = True-positive/Number of normal data
 - Precision rate = True-positive/True-positive+False-positive

To help visualize the results and parameters, the Receiver Operating Characteristics (ROC) graph will be used as well. It is a technique to visualize the performance based on the parameters and demonstrated the better trade-off between false-positive rate and true-positive-rate.

To evaluate the clustering, the Davies-Bouldin, Dunn's indexes and Silhoutte will be applied.

### Project Design

The solution will be following some steps:

1. **Data cleaning:** Methods to clean the dataset will be applied, such as outliers cleaning, nil or missing values might be excluded or some technique to fill the missing value might be applied.

2. **Summary data:** Statistical Inference will be applied, to analyse expected values, variability, distribution of dataset to conclude and infer some hypothesis.

3. **Supervised method:** The K-means will be applied to split the data in a first phase of the solution. It will create groups, these groups will be evaluated using some clustering metrics: Davies–Bouldin index, Dunn's index and Silhouette. Thus, after finding the best centers and groups, it will be the input for the unsupervised phase.

4. **Unsupervised method:** Applied ensemble method using random forest, where each tree in the ensemble is built from a sample drawn with replacement from the training set. When the node will be splitted during the construction of the tree, the split that is chosen is the best split among a random subset of the features. 

5. **Evaluating:** This step is the final step, after training the dataset into the supervised and unsupervised steps, the results of the classification will be summarized and organized to get a conclusion if the solution did a good job or not. 
