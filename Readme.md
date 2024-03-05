# Summary of my Approach :

- First of all, I thought of drawing some conclusions out of the given training dataset, like one of the conclusions I drew was that in a given word, the probability of finding a vowel is good until it constitutes about 45-48% of the given word length. I meticulously detailed all my precomputations in the attached notebook.
- Apart from that, I decided to use the n-grams model, and here, I am using 1 (unigram), 2 (bigrams), and 3 (trigrams) up to 5 (five-grams). Although I experimented with 6 (six-grams), it yielded marginal improvement, prompting me to settle on five as the optimal cutoff. This decision aligns with intuition, as longer sequences tend to become a concatenation of shorter ones

- The model is trained on a dictionary of approximately 250,000 words. This dictionary is used to determine the n-gram frequencies. For example, the following structure for the bigram frequencies are:

```
word length (n-gram frequencies depend on the length of the word)
first letter
second letter
second letter frequency (this indicates how many letter1-letter2 sequences there are)
```

Also, I have used different weights for the different grams like as shown below:

```
unigram_lambda = 0.10
bigram_lambda = 0.20
trigram_lambda = 0.30
fourgram_lambda = 0.40
fivegram_lambda = 0.45
```

Also, My model is using what I can say is <b>dynamic n-grams</b>, like for a 3-letter word, I am calculating bigrams and unigrams to calculate required probabilities and results.
Also, Some more <b>optimizations</b> I've applied are like:

1. Removing the incorrect words at a benchmark of 3, i.e. I am recalibrating n-grams when my 3 tries are used, this is improving the result by decreasing the weightage of those elements which are leading to incorrect guesses.
2. Dynamically deciding the weightage of vowels while guessing the letters. According to some statistics which I showed as the pre-computations, I observed that we can give some extra weightage to vowels and only up to a certain limit, so, Incorporating this optimization leads to a good improvement.
3. Utilising the EM algorithm for optimizing the weights for the n-grams (unigram lambda, bigram lambda, etc.) to obtain improvement.

By using the above model and doing some greedy and strategic optimizations, I managed to achieve an overall success rate of <b>53.4%</b> (1000 games played).
