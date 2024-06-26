# Intro

Believe it or not, but having the right features gives a bigger performance boost than clever algorithmic techniques (SotA models with bad set of features sucks anyway). It is not surprise, then, that ML engineering/data science tasks revolve around coming up with useful features. Actually, there is a proper name for it: feature engineering.

Even though we have deep learning (or feature learning) capable of learning representation automatically, it is not like all features can be automated. Moreover, current production ML applications aren't DL at all: sometimes we need subject matter expertise to craft features for our systems to be useful.

# Main Points

Given the ubiquity of feature engineering in ML, many techniques have been developed. Let's disscuss some...

## Techniques
### Missing Values

When dealing with real-world data, you'll certainly encouter data whose values are missing. It can happen because of several reasons:
- _Missing not at random_: the data is missing because of its true value, like when survey respondents do not disclose income. Too high to say aloud, dig?
- _Missing at random_: value is missing because of another observed variable. Suppose a given gender "A" not disclosing their age.
- _Missing Completely at Random_: no pattern. This is what we expect in general. What we might not expect is that this type of missing is very rare. When data misses, you should investigate.

Ok, so now we know what kinda missing data we may encounter. Cool. The real question is: what to do with them?

Well, the easiest thing to do is to delete them. For insance, if a given column has the majority of the rows null, you might want to get rid of it. If we have fewer data missing (less than 10%), we might just delete the rows containing the missing values. Be careful, though. Removing data can reduce the accuracy of the model or worse: create biases in it.

Another thing to do is to fill missing values with some number. Which number? That's the real deal. We can use the mean, the median or the mode, and they may work well. You should avoid filling missing spots with possible numbers, because this makes hard to distinguish between missing-imputed and an already valid row input.

At last, just keep in mind there is no fool proof way of handing missing data. They are annoying and all ways of fixing it will have their weaknesses.

### Scaling

ML models don't understand features have different interpretations. If a feature have a number around thousands and another one is just dozens, it will give more importance to the former without a second thought.

Bottomline: before inputting features, scale them to similar ranges. You can get them in the range $[0,1]$, or $[-1,1]$, or even an arbitrary range by normalizing them so that they have zero mean and unit variance. 

A similar, but different, struggle are skewed distributions (long tail on the side). To mitigate it, you can log-transform the feature. Again: not a silver bullet, so check if the performance really improves.

Pay attention to data drift between training-test environments. Since scaling needs global statistic, if they changes significantly, they won't be useful anymore.

### Discretization

Discretization (a.k.a. quantization or binning) turns a continuous feature into a discrete one by creating buckets and putting samples in it. This way, instead of havint to learn an infinite range (or large amount of categorical possibilities), it will instead focus on learning only a handful of categories.

### Encoding Categorical Features

Ok, we kinda know we can turn continuous features into categorical features. But how we handle categorical features? It is important to know categories evolve over time, making 'put everybody in buckets' an actually hard task. One solution is to hash categories, generating an index in a space whose size can be controlled. This can cause collision (two categories randomly ending in the same index) though, but you can attenuate it by using a customized hash function or a space large enough to reduce collision.

### Feature Crossing

It stands for combining two or more features to generate new ones and is cool because it models nonlinear relationships between them. There is a caveat worth knowing: it makes the feature space blow up.

### Positional Embeddings

Current positional embeddings in models like BERT are vectors accounting for a word (actually a token) position in a sentence. They are learned during trained and have the same size of the word (token) embedding in order to make sum available.

## Data Leakage

_Data leakage_ refers to the phenomenom when a form of label 'leaks' into the features used for predictions during training. Detecting it is challenging because often the leakage is not obvious and dangerous because it can cause the model to fail terribly (even after careful evaluation and testing).  

Some common causes for it are:
- randomly splitting time-correlated data instead of doing it by time: sometimes time itself carry information, and by letting future samples go back to training data, we might be giving the model a unwanted help;
- scaling before splitting: scaling involves global statistics. If they are calculated before splitting, the model certainly sees hints of the test set;
- filling missing data with test-split statistics: kinda the same... we calculate stats for filling using the test set
- poor handling of duplicates: duplicates or near-duplicates can appear on both train and test sets;
- group leakage: samples more correlated with the labels end up in both splits.
- data generation: the way data is generates imprints information regarding the label in a obscure way.

Ok, but how to detect it? First, measure predictive power for each feature. If one of them is unusually highly correlated, check if it makes sense. Second, ablation studies: if removing a feature hurts the model so bad or adding a new one makes it super, why is it so important?

Talking about adding features, go easy on doing so.. it might leak data, or overfit the model, for instance. Regularize training to ensure only useful features are priorized. 


# Best Practices Summary

- For missing data: at first try to input them (median, mean, or mode). If too many rows are missing in a col, you might drop the feature. Check how this decision affects the model's metrics and keep in mind possibility of bias, noise or leakage.
- Before feeding data to models, scale them to similar ranges. If data is skewed, you can log-transform them. And at last, keep checking for statistics in prod to be sure they do not differ too much from training data's.
- Discretization may not help that much. But it may be important to know it exists.
- Categories change over time. To account for varying categories, consider using customized hashing functions.
- Crossing features models nonlinear relationships in the expense of blowing the feature space up.
- Positional embedding uses vactors instead of numbers because the neural net work better with the former.
- Data Leakage may happen to anyone. Even so, it is rarely covered in ML curricula. Be wary of that!
- In order to know the importance of features, take a look in model-agnostic methods, like SHAP
- At last, good features should generalize (not necessarily equally) to unseen data. So, if a feature misses too much, it'll hardly be generalizable.
