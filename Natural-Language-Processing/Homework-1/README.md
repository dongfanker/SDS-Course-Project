# NLP-course-project
### Final result
My model reach 92\% accuracy in the eval test for add-k method, and 93\% accuracy for the kneser\_key method, the result is concluded in result.txt

### Environment
Python 3.6.3

numpy 1.13.1
### Language model
#### ADD-k model
I use add-k thought in the first language model

I also use the word after the wrong word to implement bigram
. I calculate the result of the following and multiply them together

#### Kneser-Ney model
I implement it in bigram way, 

I also use the word after the wrong word to implement bigram
. I calculate the result of the following and multiply them together

### Channel model
#### Confusion Matrix
##### detail
1. I used the count\_1edit dataset provided by Peter Norvig to compute my confusion matrix [\url {http://norvig.com/ngrams/count_1edit.txt}]

2. I use trie to find the word within edit\_distance, it turn out work efficiency

### Final Model
#### detail
1. The combination of the language model and the channel model can be concluded into the following formulas:


2. I treat the edit-distance of transpose as 1 instead of 2, which is defined in Damerau-Levenshtein distance instead of Levenshtein distance. Making transpose 1 edit-distance broaden the choice of 1 edit-distance, which is reasonalbe for transposing quite frequently appearing.

3. Further thought for the implementation: my result of kneser\_key method is quite close to the add-k method，which mean I maybe didn't make the best use of its advantage. It may get better result in more gram stage.



### code explanation
#### kgram.py
initCount() is implemented at first to tokenize the reutersCorpus.txt for counting the number of grams.

initCount2() is implemented when I use the reuters in nltk, it turn out to be a better result.

Count.pk is the result delivering file from kgram to spellCorrction.py, cutting the time for future initial
#### confusionMatrix.py
initMatrix() is implemented at first to make the matrix of spell-error for channel model, but since I use nearly all of the letter and signal, the matrix is really sparse. 

initMatrix() is implemented when I use the count\_1edit.txt to make the matrix of channel. The result turn out better.

Matrix.pk is the result delivering file from confusionMatrix to spellCorrection.py, cutting the time for future initial
#### spellCorrection.py
def Pxw(): it is used for calculating the channel result

def kneser\_key(): it is used for calculating the language model result in kneser\_key way

def add\_k(): it is used for calculating the the language model result in add\_k way

def P(): it is used for calculating the unigram frequecy of word 

def get\_candidate(): it is used for searching the result within the edit\_distance
