# YouTube Cannibalization Prediction Project
---
This project focuses on **predicting the cannibalization effect of featured YouTube videos** resulting from collaborations.

It represents my Master's thesis for Information Management at National Taiwan University (#1 National). The thesis title is: *“Is Your Guest an Ally or an Enemy? Predicting Cannibalization Effects for Featured Videos on Social Media Platforms”*

### Skills used
* **PyTorch** - Built a deep learning model to solve a business-related research problem
  * Natural Language Processing (NLP) - Leveraged BERT to exploit text features
  * Image Processing - Encoded thumbnail images for augmented features
* **NumPy, Pandas, Matplotlib** - Extensive data preparation, cleaning, and visualization
* **Sklearn** - Machine learning techiniques such as data encoding and model evaluation
* **Webscraping with parallelization** - Efficient webscraping using YouTube API to answer the proposed research question

## Overview

This section is only meant to offer a concise, high-level overview with simplified details.

For a comprehensive understanding of the outlined steps' logic and reasoning, please consult the the `Full_Presentation.pdf` file, the exact file utilized during my thesis defense presentation.

### WHY IT MATTERS - Problem Statement
Collaboration between influencers/YouTubers is a prominent strategy to increase popularity, but it's not always mutually beneficial. **Cannibalization can cause unintended harm**, in which a host channel's popularity drops significantly after collaborating with a guest. **Predicting cannibalization beforehand helps avoid harmful collaborations** that would in turn compromise a YouTuber's channel popularity and value.

### WHAT TO DO - Task Description
Our task is a 3-class classification problem given past data of host and guest channels.

We want to predict whether a given featured video is
- `Cannibalized`: The views of host’s next $k$ videos dropped $θ$
- `Boosted`: The views of host’s next $k$ videos rose $θ$
- `Unaffected`: The views of host’s next $k$ videos did not change over $θ$

given the below:
- Channel features from both sides (host and guests)
- Features of host’s past $k$ videos prior to a given featured video
- Features of guests’ past $k$ videos prior to a given featured video

### WHAT I DID - Proposed Model (CIIE)
The model architecture is shown in the following. It was implemented using the popular PyTorch framework.

![image](https://github.com/ching-yao-lin/youtube-cannibalization-prediction/assets/45042477/c6b40e04-c0b2-4401-bfb9-22206fd15d19)

* Host/Guest Influencer Encoders: Model components extracting crucial information from individual YouTuber data.
* Mean Pooling: Combines representations of multiple guests with a host, generating an aggregate guest representation.
* Classifier: Utilizes host and guest data to generate a probability distribution for each class

### RESULT - Model Evaluation
**The proposed model (CIIE) outperforms all benchmarks across most metrics**. Despite the severe class imbalance in the dataset, it is impressive that this model not only excelled in macro averages but also demonstrated superiority in handling minority classes like `cannibalized` and `boosted`.

![image](https://github.com/ching-yao-lin/youtube-cannibalization-prediction/assets/45042477/64bf362e-6a99-4dc7-ad52-285926c8517e)

---

All relevant code is provided in the `code` folder, including:
* `1_DataScraping.ipynb`: Collected channel and video data of top Taiwanese YouTubers using YouTube API
* `2_MergeFiles.ipynb`: Merged all scraped files into dataframes and saved them locally as parquet files.
* `3_DatasetCreationAndSummaryStatistics.ipynb`: Created features and labels to obtain the full dataset
* `4_Benchmarks.ipynb`: Built benchmark models to compare against
* `5_ModelAndExperiments.ipynb`: Built the proposed model and ran experiments and ablation studies

--- 

Special thanks to [Prof. Chih-ping Wei](https://management.ntu.edu.tw/IM/faculty/teacher/sn/15),  my advisor, for offering me guidance on this interesting yet challenging project for my master thesis. It was a truthfully amazing experience that I would remember for my entire life.
