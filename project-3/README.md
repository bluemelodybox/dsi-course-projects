# Project 3: Web APIs & Classification
### Problem Statement
The intend of this project is to build different classification models that can accurately classify between subreddit topics based on text posts and find out which model gives the best accuracy.

### General approach
- Scrape subreddit data
- Clean text, lemmatize and remove stopwords
- Convert processed text to vectors using countvectorizor or tf-idf
- Perform grid search over all parameters for all models
- Evaluate models base on accuracy score
- Find out frequently occurring words that are classified correctly and wrongly

### Data Source

Two sets of 2 subreddits are scrapped :

Set 1: [r/datascience](https://www.reddit.com/r/datascience) | [r/learnprogramming](https://www.reddit.com/r/learnprogramming) 

```
Number of rows in subreddit datascience : 827
Number of rows in subreddit learnprogramming : 976
Baseline accuracy: 0.5413200221852468
```

Set 2:  [r/python](https://www.reddit.com/r/python) | [r/learnpython](https://www.reddit.com/r/learnpython)

```
Number of rows in subreddit python : 577
Number of rows in subreddit learnpython : 976
Baseline accuracy: 0.6284610431423052
```

### Data Cleaning

1. Remove all non alphabets charaters
2. Remove default stopwords from nltk and customized stopwords
3. Apply stemmer to text

### Word Embedding

- Count Vectorizer 

  Best parameters:

  - 0.5 max df
  - 2500 max features
  - 1 gram

- TF-IDF

### Model results with best grid search parameters for r/datascience and r/learnprogramming

TP - Classify as r/datascience and is correct

FP - Classify as r/learnprogramming but is suppose to be r/datascience

TN - Classify as r/learnprogramming and is correct

FN - Classify as r/datascience but is suppose to be r/learnprogramming

| Models               | Test Score | TP   | FP   | TN   | FN   | Precision | Recall | F1    |
| -------------------- | ---------- | ---- | ---- | ---- | ---- | --------- | ------ | ----- |
| Logistic Regression  | 0.907      | 233  | 31   | 176  | 11   | 0.882     | 0.955  | 0.917 |
| K-Nearest Neighbours | 0.894      | 233  | 37   | 170  | 11   | 0.863     | 0.955  | 0.907 |
| Naive Bayes          | 0.883      | 238  | 47   | 160  | 6    | 0.835     | 0.976  | 0.900 |
| Random Forest        | 0.896      | 232  | 35   | 172  | 12   | 0.879     | 0.951  | 0.914 |
| Extra Trees          | 0.880      | 226  | 36   | 171  | 18   | 0.863     | 0.927  | 0.894 |
| Ada Boost            | 0.858      | 218  | 38   | 169  | 26   | 0.852     | 0.893  | 0.872 |

Top words correctly classified for datascience:

```python
['science','work','scientist','time','job','r','project']
```

Top words correctly classified for learnprogramming

```python
['programming','code','string','c','java','python','int','learning']
```

Top words misclassified for datascience

```python
['r','python','people','need','work','best','tests']
```

Top words misclassified for learnprogramming

```python
['science','time','information','incbit','artificial','intelligence','commercial']
```





### Model results with best grid search parameters for r/python and r/learnpython

TP - Classify as r/learnpython and is correct

FP - Classify as r/python but is suppose to be r/learnpython

TN - Classify as r/python and is correct

FN - Classify as r/learnpython but is suppose to be r/python

| Models               | Test Score | TP   | FP   | TN   | FN   | Precision | Recall | F1    |
| -------------------- | ---------- | ---- | ---- | ---- | ---- | --------- | ------ | ----- |
| Logistic Regression  | 0.877      | 234  | 73   | 72   | 10   | 0.762     | 0.959  | 0.849 |
| K-Nearest Neighbours | 0.748      | 233  | 77   | 68   | 21   | 0.752     | 0.917  | 0.823 |
| Naive Bayes          | 0.676      | 243  | 1    | 20   | 125  | 0.996     | 0.660  | 0.794 |
| Random Forest        | 0.817      | 227  | 54   | 91   | 17   | 0.891     | 0.930  | 0.865 |
| Extra Trees          | 0.817      | 226  | 53   | 92   | 18   | 0.810     | 0.926  | 0.864 |
| Ada Boost            | 0.807      | 217  | 48   | 97   | 27   | 0.819     | 0.889  | 0.853 |

Top words correctly classified for python:

```python
['code','github','using','made','data','project','application']
```

Top words correctly classified for learnpython

```python
['print','self','file','code','list','get']
```

Top words misclassified for python

```python
['self','file','backup','c','would','pygame','data']
```

Top words misclassified for learnpython

```python
['use','code','application','jupyter','overlayed','using','notebooks','love']
```



### Conclusion

- Different model works well in different subreddit
- There is no one model that can work well for all subreddit
- Best model is logistic regression
- Best parameters for count vectorizer is 1 gram tokenize with 2500 max features, using tfidf transform
- Some of the misleading words that is oftenly misclassified includes 'python', 'r', 'people', 'work', 'science' for data science and 'artificial', 'intelligence', 'information', 'time' for learn programming