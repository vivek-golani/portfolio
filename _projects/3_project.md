---
layout: page
title: Covid-19 Resource Prediction
description: Quantifying mental health impact of the pandemic and predicting bed hospital bed deficits.
img: assets/img/proj3_title.jpg
# redirect: https://unsplash.com
importance: 1
category: Data Science & Machine Learning
---

The COVID-19 pandemic has had a significant impact on global public health, with many people
experiencing increased levels of stress and anxiety, social isolation, and economic hardship. As a result,
there has been a growing concern about the potential increase in substance abuse and mental health
issues during the pandemic. To address these concerns, our project aims to provide evidence of a surge
in substance abuse during the pandemic and quantify its impact on mental health. We also strive to
develop a forecasting model to predict hospital bed and staffing deficits with a one-week lead time,
which could help enhance preparedness for future pandemics.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj3_method.jpg" title="Methodologies" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Methodologies 
</div>

To gather our data for sentimental analysis, we utilized both existing COVID-19 Reddit datasets from 2018 to 2021 and also scraped data from 2021 to 2023 using Reddit's open-source APIs. The data was loaded into Spark RDDs and combined, and we performed preprocessing by filtering out posts not related to mental health or substance abuse. We also used engagement scores to filter the data for better results. The XLNet model, a transformers model, was used to classify the posts into five severity score classes: critical, major, moderate, minor, and cosmetic, through a zero-shot classification pipeline.

Using sentiment analysis, we categorized posts into 5 severity classes and plotted them by year from 2018 to 2023 to track changes in each category over time as seen below.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj3_sent_anal.jpg" title="Sentimental Analysis " class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Plots of frequency of posts of varied severities over time.
</div>

Next, we attempted to correlate the number of covid cases in a year with the number of posts classified as critical, major, moderate, minor, and cosmetic. Based on the heatmap presented below, it is evident that there exists a significant correlation
between the number of new COVID-19 cases and the frequency of posts classified as critical, major, and moderate.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj3_heatmap.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Heatmap signifying correlation between rising cases and severity of posts.
</div>

We then employed the ARIMA model, imported from statsmodels, using 90% of the data and test it against the remaining 10% for availability of inpatient and ICU beds for New York state and for the entire country. We also compared ARIMA, SARIMA and Holts models for forecasting bed availability and found ARIMA to be the best based on root mean squared error values.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj3_time_series_plot.jpg" title="Hospital bed availability Time series plots" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Time Series Plot of ARIMA model predictions of hospital bed availability for USA and New York State.
</div>

We then tabulated the predictions of ARIMA model for the period March to May 2023. The result tables show our predictions for inpatient and ICU bed availability. The values are in line with the actual values with slightly poor performance on ICU bed
availability at the country level. The proximity in train and test RMSE values indicated good generalization of the ARIMA model.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj3_time_series_table.jpg" title="Hospital bed availability Time series plots" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Time series prediction results from March to May 2023.
</div>