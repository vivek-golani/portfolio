---
layout: page
title: Sentimental Analysis of Short Texts
description: Enhanced accuracy of CharSCNN model by 1.5% using unsupervised pre-training.
img: assets/img/proj6_title.jpg
importance: 3
category: NLP
---

Sentiment analysis of short texts such movie reviews and tweets is challenging because of the limited contextual information. To deal with limited context, the paper proposed a convolution based neural network that exploits from character- to sentence-level information to perform sentiment analysis of short texts. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj6_title.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Convolutional approach for character-level feature extraction.
</div>

The model uses character-level embeddings and word-level embeddings to capture shape and syntactic information from a sentence respectively. Once the embeddings for each character are assigned, a convolutional layer is applied to each window of k characters. A max pooling operation is then applied to calculate the word embedding. We then apply another convolutional layer to a window of words followed by a max-pool layer resulting in a sentence embedding.

The sentence embedding is then passed through a binary classification layer resulting in the overall sentiment of the sentence. 
For speeding up training and better accuracy, I also performed an unsupervised pre-training of word embeddings.
