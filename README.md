# Lyrics Miner

In this project I analyze lyrics of n most popular songs by a selected artist. The project was part of a Search Systems course at my university. It involves:
* lyrics preprocessing using regex formulas and custom lemmatization,
* finding how many terms occur overall and which are the most popular, 
* comparing songs to each other with TF-IDF vectorization.

### Data

I downloaded raw lyrics from [Genius.com](https://genius.com/) via their API. Gathering data process was done with help of [lyricsGenius](https://github.com/johnwmillr/LyricsGenius) library. The inspiration vastly came from comming across Melanie's Walsh online textbook [*Introduction to Cultural Analytics & Python*](https://melaniewalsh.github.io/Intro-Cultural-Analytics/welcome.html)

### Analysis

The following example is about top 25 songs of Pitbull. 

Before finding most popular terms lyrics had to be preprocessed in such way that removes all the non-informative parts and isn't a part of the song. I decided to remove also most of the punctuation and then perform lemmatization to have words transformed into their root form. 

For counting and comparing phase I utilized `CountVectorizer()` and `TfidfTransformer()` classes from scikit-learn's [feature_extraction](https://scikit-learn.org/stable/modules/feature_extraction.html) module. It allowed to get the lyrics represented by vectors in the form of a sparse matrix. Transforming the matrix into numpy's array and using its function for summation along columns yielded the number of occurences for each term. 

![alt text](https://github.com/maksmanikowski/lyrics_miner/blob/main/popularity.png)

More than 8 occurences of "baby" term on average, that's so Pitbull. 

For getting the distance measure (i.e. similarity) between song's vectors I used cosine similiary metric. The results are visualized on the following heatmap.

![alt text](https://github.com/maksmanikowski/lyrics_miner/blob/main/heatmap.png)

It would be nice to check in the future which terms are accountable for the highest similarities.

### End

If you happen to know some of Pitbull's songs then I hope you find that interesting. But you can also use this code to perform an analysis of any artist of your choice. 
