# YouTube Cannibalization Prediction Project
---
This project is centered on predicting the cannibalization effect of featured videos on YouTube.

It presents the work of my Master's thesis at M.B.A in Information Management, National Taiwan University (#1 National): *“Is Your Guest an Ally or an Enemy? Predicting Cannibalization Effects for Featured Videos on Social Media Platforms”*

### Skills used
* **PyTorch** - Built a **deep learning** model to solve a business-related research problem
  * **Natural Language Processing (NLP)** - Leveraged BERT to exploit text features
  * **Image Processing** - Encoded image data with ResNet model
* **NumPy, Pandas, Matplotlib** - Extensive data preparation, cleaning, and visualization
* **Sklearn** - Machine learning techiniques such as data encoding and model evaluation
* Webscraping with parallelization - Efficient webscraping using YouTube API to answer the proposed research question

## Overview

This section is only meant to provide the highest-level overview, with most details removed for simplicity.

To follow the logic and reasoning for the steps outlined below, please refer to the `Full_Presentation.pdf` file. It is the exact presentation file I used to present my work in the thesis defense.

### WHY IT MATTERS - Problem Statement
Collaboration between influencers/YouTubers is a prominent strategy to increase popularity, but it's not always mutually beneficial. **Cannibalization can cause unintended harm**, in which a host channel's popularity drops significantly after collaborating with a guest. Predicting cannibalization beforehand helps avoid harmful collaborations that would in turn compromise a YouTuber's channel popularity and value.

### WHAT TO DO - Task Description
Our task is a 3 class classification problem given past data of host and guest channels.

We want to predict whether a given featured video is
- `Cannibalized`: The views of host’s next k videos dropped θ
- `Boosted`: The views of host’s next k videos rose θ
- `Unaffected`: The views of host’s next k videos did not change over θ

given the below:
- Channel features from both sides (host and guests)
- Features of host’s past k videos prior to a given featured video
- Features of guests’ past k videos prior to a given featured video

### WHAT I DID - Proposed Model (CIIE)
The model architecture is shown in the following. It was implemented using the popular PyTorch framework.

![image](https://github.com/ching-yao-lin/youtube-cannibalization-prediction/assets/45042477/c6b40e04-c0b2-4401-bfb9-22206fd15d19)

* Host/Guest Influencer Encoders: The model's building blocks that extract essential information from each YouTuber's data.
* Mean Pooling: A host might have multiple guests; therefore, the representations of the guests are averaged to generate an overall guest representation
* Classifier: It takes in host and guest information to generate a probability distribution for each class

### RESULT - Best-performing model
The proposed model (CIIE) outperforms all benchmarks in most metrics. Notably, the dataset suffers from severe class imbalance. The proposed model not only stood out as the best in the macro averages but was also robust when it comes to minority classes (cannibalized & boosted).

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
