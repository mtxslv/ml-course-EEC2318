# Intro

Even though the funny part (the curriculum focus) of ML is modelling, data mishandling can sink the entire ML operation. It happens because it is  full of potential bias, caused by collection, sampling, or labelling. Once the models are trained on them, these issues are perpetuated. Moreover, data in production is constantly changing in volume and characteristic. Thus, obtaining or creating training data is fundamental, as this iterative process evolves through the project lifecycle.

# 10 Points

## _On Sampling_

Often overlooked in ML coursework, sampling happens across the ML lifecycle: we sample data to create training data, we sample to generate split sets, and we even sample events for debugging models. In many cases, this is necessary because we cannot collect all the data we need, or because we have too much data to look at everything. Thus, we should understand sampling methods to avoid biases and improve the data efficiency.

We may sample without caring for probability criterias, only by convenience. It happens by using any data we got, or scraping a website, or by slicing data by categories. This includes selection biases, but sometimes is everything you have to start your project. To make your models reliable, you'll use a probability based sampling.

The simplest form of random sampling is to consider everybody has the same chance: easy to implement, but prone to leave rare events out of your samples. To solve it, you can sample from groups inside your data, this way ensuring even rare clases appear (stratified sampling). Another way is to weight samples, and use it as a proxy to probability of being selected. Other ways exist, like Reservoir Sampling (for streaming data), but I'll skip it. 

## _On Labeling_

Current production models are supervised. It is not surprise we need good quality labeled data to train them on. The catch? As long as you want your ML systems to work you'll need a labeling team.



## _On Class Imbalance_


# Conclusion

---
_Suggestions_
- sampling
- label multiplicity,
- lack of labels
- class implanace
- data augmentation