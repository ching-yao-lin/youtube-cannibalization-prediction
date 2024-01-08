# YouTube Cannibalization Prediction Project
---
This project is centered on predicting the cannibalization effect of featured videos on YouTube.

### WHY IT MATTERS - Problem Statement
Collaboration between influencers/YouTubers is a prominent strategy to increase popularity.  However, such collaborations are not always beneficial to both sides. **Cannibalization can cause unintended harm** to a social media business when pursuing such a collaboration strategy. In this study, it is said to occur when **the popularity of the host channel dropped significantly after collaborating** with the invited guest influencer.

Cannibalization is a risk that should be identified and prevented in advance. If we can predict cannibalization before a decision on featuring another channel, we can avoid harmful collaborations that would in turn compromise the popularity and value of a YouTubers’s channel.

### WHAT TO DO - Problem Formulation
Our task is a 3 class classification problem given past data of host and guest channels.

We want to predict whether a given featured video is
- `Cannibalized`: The views of host’s next k videos dropped θ
- `Boosted`: The views of host’s next k videos rose θ
- `Unaffected`: The views of host’s next k videos did not change over θ

Given the below:
- Channel features from both sides (host and guests)
- Features of host’s past k videos prior to a given featured video
- Features of guests’ past k videos prior to a given featured video

---

All relevant code is provided in the `code` folder, including:
* `1_DataScraping.ipynb`: Collected channel and video data of top Taiwanese YouTubers using YouTube API
* `2_MergeFiles.ipynb`: Merged all scraped files into dataframes and saved them locally as parquet files.
* `3_DatasetCreationAndSummaryStatistics.ipynb`: Created features and labels to obtain the full dataset
* `4_Benchmarks.ipynb`: Built benchmark models to compare against
* `5_ModelAndExperiments.ipynb`: Built the proposed model and ran experiments and ablation studies
