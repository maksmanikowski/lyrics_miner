# Lyrics Miner

In this project I analyze lyrics of most popular songs by a selected artist or band. It involves:
- [x] Lyrics preprocessing using regex formulas, lemmatization and stop words,
- [x] Finding how many unique terms occur overall and which of them are most frequent, 
- [x] Measuring similarity between songs.

To do:
- [ ] Songs clustering
- [ ] Topic extraction

### Data

I retrieved lyrics from [Genius.com](https://genius.com/) via their API. Gathering data process was done with help of [lyricsGenius](https://github.com/johnwmillr/LyricsGenius) library. 

Next, the data underwent following transformations:
1. Removing all the non-informative parts,
2. Removing punctuation and converting text to lowercase,
3. Tokenization along with lemmatization and stop words removal,
4. Vectorization using token counts 
5. TF-IDF transformation to account for frequently occuring terms

For counting and comparing phase I utilized `CountVectorizer()` and `TfidfTransformer()` classes from scikit-learn's [feature_extraction](https://scikit-learn.org/stable/modules/feature_extraction.html) module. 

### Analysis

**Note**: all the code used to generate following plots is contained in `notebook.ipynb`

With the matrix obtained in the 4. step of data processing I used summing along columns to receive each term frequency in all analyzed songs. 

![alt text](https://github.com/maksmanikowski/lyrics_miner/blob/main/popularity.png)

More than 8 occurences of "baby" term on average, that's so Pitbull. 

To measure the distance (i.e. similarity) between song's vectors I used cosine similiary metric. The results are visualized on the following heatmap.

![alt text](https://github.com/maksmanikowski/lyrics_miner/blob/main/heatmap.png)

It would be nice to check which terms are accountable for the highest similarity scores here.

### Summary

If you happen to know some of Pitbull's songs then I hope you find that analysis interesting.

You can paste the name of any artist along with number of most popular songs in `notebook.ipynb` and run the rest of the cells to get a similar output. 

The inspiration for this project vastly came from Melanie's Walsh online textbook [*Introduction to Cultural Analytics & Python*](https://melaniewalsh.github.io/Intro-Cultural-Analytics/welcome.html).
