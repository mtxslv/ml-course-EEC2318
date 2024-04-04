# Intro

Even though the funny part (the curriculum focus) of ML is modelling, data mishandling can sink the entire ML operation. It happens because it is  full of potential bias, caused by collection, sampling, or labelling. Once the models are trained on them, these issues are perpetuated. Moreover, data in production is constantly changing in volume and characteristic. Thus, obtaining or creating training data is fundamental, as this iterative process evolves through the project lifecycle.

# 10 Key Points

## _On Sampling_

1. Often overlooked in ML coursework, sampling happens across the ML lifecycle: we sample data to create training data, we sample to generate split sets, and we even sample events for debugging models. In many cases, this is necessary because we cannot collect all the data we need, or because we have too much data to look at everything. Thus, we should understand sampling methods to avoid biases and improve the data efficiency.

2. We may sample without caring for probability criterias, only by convenience. It happens by using any data we got, or scraping a website, or by slicing data by categories. This includes selection biases, but sometimes is everything you have to start your project. To make your models reliable, you'll use a probability based sampling.

3. The simplest form of random sampling is to consider everybody has the same chance: easy to implement, but prone to leave rare events out of your samples. To solve it, you can sample from groups inside your data, this way ensuring even rare clases appear (stratified sampling). Another way is to weight samples, and use it as a proxy to probability of being selected. Other ways exist, like Reservoir Sampling (for streaming data), but I'll skip it. 

## _On Labeling_

4. Current production models are supervised. It is not surprise we need good quality labeled data to train them on. Then, as long as you want your ML systems to work you'll need a labeling team.

5. The catch? Hand labeling needs subject matter expertise (expensive), it threatens data privacy (can your insurance see your medical records?), and it goes at snail's pace (have you ever tried to organize your smartphone's camera roll?). Moreover, labelling in general may be ambiguous (label multiplicity) and difficult to version (data lineage).

6. But don't fret: all not is lost. Sometimes, the task has natural ground truth labels (the predictions can be automatically full/partially evaluated by the system). For instance, recommender systems know the suggestion worked when the customer indeed buy the product. In other scenarios, we can collect user feedback (Google let users submit alternative translations).

7. Ok, sometimes we're at rock bottom: no sufficient labeled data at all. Even in that situation we still have workarounds. We can extract labels by applying a set of simple heuristics (weak suppervision). Other possibility is to train a model on few lable samples and then on top predictions or on similar unlabelled data (semi-supervision). A last possibility is to reuse models in a similar, but different, task.

## _On Class Imbalance_

8. Sometimes, in classification tasks, each class has a different amount of samples (i.e., detection of medical conditions). This messes up our model for a number of reasons, but to summarize notice that our model may just output the majority class and even so their accuracy will be good. And worse: probably the minority class has a high cost!

9. To solve this we change the following: the metric (less insensitive to imbalance), the data distribution itself (less imbalanced), or the learning model (more robust).

# _On Data Augmentation_

10. Originally created to increase the amount of training data, _data augmentation_ make models more robust to noise and adversarial attacks. The trick here rely on data format manipulation. For instance, we can randomly flip a image or replace synonyms in a sentence, preserving the label and effectively synthesizing more data points. Another way of doing so is training on noise-injected samples to improve decision-boundaries' weak points.

# Conclusion

The takeaway here is simple: look after your data with affection. Garbage in, garbage out, dig? Not just that, be mindful of how to sample, and how you are going to collect the labels. At last, do not worry... you can still get around with your current data by applying data augmentation and even data imbalance can be attenuated.