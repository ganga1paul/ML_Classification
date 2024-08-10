**Why So Harsh Project Report**

 
**Missing Value Checking:**  Checked for any missing values in the training set. Found there were no missing values in the training set  


**Visualization of the distribution of tags:** We wanted to check how many comments are tagged in each category, as in how many comments are tagged as ‘harsh’, how many comments are tagged as ‘vulgar’ etc.  
From the chart it is evident most of the tags are not evenly spread out, most of the comments are tagged as ‘harsh’, ‘vulgar’ or ‘disrespect’ whereas threatening is very few. So we could get an idea that **multiple tags** are associated with each comment.

**Checking Multi-tagging:** Then we checked how many comments are multi tagged. So there are 1415 comets which are tagged in 4 different categories. Similarly found there are 29 comments which are tagged in all 6 categories


**Correlation plot to check which comments go together most often:**  
Found that ‘harsh’ comments are mostly tagged as ‘vulgar’ and/or ‘targeted hate’ as well, as these are showing good correlation. Also noticed that ‘vulgar’ comments are mostly tagged as ‘disrespect’ too.


But as these comments are ‘categorical’ so it is not a very good idea to try ‘Pearson Correlation’, so we tried to check the correlation with the confusion matrix also.  
We did a crosstab analysis of all 6 classes with ‘Harsh Category’.   
We can see how ‘harsh’ comments are also tagged in other categories.   
We can see only 75 comments are tagged as ‘targteted\_hate’ as well as ‘harsh’  

**Exploratory Data Analysis:**

**Word Cloud for most frequent words:**   

**Violin plot for checking if ‘longer comments’ are more toxic:**   
Found there is no such relation between ‘longer sentences’ and toxicity. So we can’t really tell if longer sentences ought to be toxic comments.  

**Checking if ‘unique words’ are more toxic or not:**  
We can see that from the violin plots, more unique words means more chance of being toxic.

Plotted a bar chart to see ‘how many comments’ are having less than 30% unique words in each category. Found that mostly ‘harsh’ comments have a lot of repetitive words, more than 270 ‘Harsh’ comments contain less than 30% unique words which can be an important criteria for classifying. Similarly, ‘vulgar’ ad ‘disrespect’ categories all contain quite a few comments with less than 30% unique words.  


**Then checked for ‘spam comments’ where one toxic comment is repeated multiple times**  
Example of a spam comment from ‘Harsh Category’:  


**Preprocessing Steps:**

Preprocessing steps include 

1) **Removing special characters,digits**

2) **Replacing repeating characters  by one character**

3) **Replacing abbreviations with full form**


4) **Tokenization**

5) **Removing stop words**

6) **Lemmatization**  

**Feature Engineering Methods**

**Word2Vec**   

**CountVectorizer**

CountVectorizer creates a matrix in which each unique word is represented by a column of the matrix, and each text sample from the document is a row in the matrix.Inside CountVectorizer, these words are not stored as strings. Rather, they are given a particular index value. In this case, ‘at’ would have index 0, ‘each’ would have index 1, ‘four’ would have index 2 and so on.

**TF-IDF (Term Frequency Inverse Document Frequency):**

This technique is used to quantify words in a set of documents where we compute the score for each word to signify the importance of that word in the document and the corpus. ML algorithms can’t work with textual data so we vectorize these textual data into numbers.

**Stop Words**: Stop words were removed from the document while calculating TF-IDF score. Stop words are the words that occur very frequently in the text but they carry very little information. Examples of stop words in English are “a”, “the”, “is”, “are” and etc. 

**Term Frequency:** Measures the frequency of the word in the document.  
If the term doesn’t exist in a particular document, that particular TF value will be 0 for that particular document. In an extreme case, if all the words in the document are the same, then TF will be 1\. The final value of the normalized TF value will be in the range of \[0 to 1\]

**Document Frequency:** DF is the count of **occurrences** of term t in the document set N. In other words, DF is the number of documents in which the word is present. 

**Inverse Document Frequency:**  IDF is the inverse of the document frequency which measures the informativeness of term t. It penalizes words/terms that are too frequent in the text such as stop words.   
Then finally we find the TF-IDF value for each word by multiplying TF and IDF values.

**Unigrams :** Used TF-IDF vectorizer to find the most occurring unigram and plotted the occurrence of words  



**TF-IDF top words per class (bigrams)**  
Bigrams are two consecutive words in a sentence whereas unigrams are single words.  
Found which two words are occuring most frequently and plotted the frequency in each class.  

**Model building using Direct Features:** 

Checked the presence of null values in test data. Found there are some null values in test data. Filled the NA values with empty space.  
**TF-IDF Vectorization for word and characters:**  
Used the TfidfVectorizer function from sklearn and created a word vector of unigrams, bigrams and trigrams. Took into account 20000 max features, and made lowercase= True, so that there won’t be any discrepancy between upper and lower case letters so this will convert all the words into lowercase. Make stop\_words \= ‘english’ so that very common stop words that are very frequent in the english language will be removed while calculating the TF-IDF score. Ngram\_range is chosen as (1,3) so it will take into account all n grams in between 1 and 3\. Analyzer \= ‘word’ so that we are creating only word vectors for now. 

Then if we put analyzer \= ‘char’ then we will create character n gram vectors where also we chose the max\_features as 40000 and ngram\_range \= (3,6) so we took tri gram to 6-gram character vectors.

Then we used fit\_transform to fit and transform the training text data according to the word and character n gram vector. Then we used these vectors to transform the test text data.  

Stacked the word vector and character vectors of the training and test data. As these are mostly sparse matrices, so use the sparse.hstack() function. 

**Model Building :**

1) **Logistic Regression Model**

2) **Multinomial Naive Bayes Model**  
 
3) **SGD Classifier Model:**  
   
4) **SGD Classifier with squared hinge loss function:**  

5) **SGD Classifier with  hinge loss function:**

6) **Multilayer perceptron**

7) **Word2Vec with Logistic Regression**

8) **XGBoost** 

9) **Feature Extraction**


