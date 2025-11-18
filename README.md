EDA Folder
2 files:
1. QBS_181_Final_Proj_EDA.Rmd
2. Bin_Analysis_EDA.Rmd

Overview:
This folder analyzes YouTube Shorts and TikTok trend data from 2025, with a special focus on understanding differences between viral and non-viral videos.
The analysis includes:
- Genre and category distributions
- Upload hour patterns
- Watch-time differences
- Comparative visualizations (bar plots, line graphs)
- Exploration of a labeled dataset identifying virality
- RYANS ANALYSIS

All code is written in R, using dplyr, ggplot2, and base functions.

QBS_181_Final_Proj_EDA.Rmd

Data Cleaning & Preprocessing:
This file imports the youtube_shorts_tiktok_trends_2025_labeled.csv and removes variables not required for the analysis.
The labeled dataset is then filtered into two groups: Viral videos (viral == 1) and Non-viral videos (viral == 0). These subsets form the basis of all downstream visualization and summary analyses.

Analyses & Visualizations:
1. Genre Distribution: Viral vs Non-Viral
   - A bar chart comparing the percentage breakdown of genres.
2. Category Distribution Comparison
   - Similar visualization for content categories.
4. Ranking Viral-Dominant Genres & Categories
   - Top genres/categories for viral content are ranked using:
6. Upload Timing Trends
   - A line plot compares upload hour patterns between viral and non-viral videos.
8. Average Watch Time by Day of Week
   - A grouped bar chart visualizes how watch-time performance varies throughout the week for each group.


NLP (Bert Topic modeling) & Title Tiktok Dataset Exploration.

1. First enter in the NLP_and_title_data_wrangling folder. 
2. There would be two files as showb below: 

Filename I: topic_modeling_example.ipynb. This notebook performs an end-to-end topic modeling workflow for YouTube/TikTok short-form video titles. 
It loads the raw dataset, cleans each title with clean_text(x) to remove emojis, links, and noise, and then trains a BERTopic model on the cleaned 
text to generate topic embeddings, topic assignments, and topic probabilities. The model is saved, reloaded, and applied again to ensure consistent 
topic labels across the full dataset. The script extracts topic keywords, filters out low-quality topics, selects the top viral topics based on 
frequency among viral videos, and builds both cleaned_topics and topic_labels for downstream analysis. It then produces the three primary visual 
outputs—hierarchical dendrogram of topic structure, intertopic semantic distance map, and viral-lift performance chart—and also exports a full 
keyword table (topic_keywords_2.csv) with every topic–word–weight combination. Final outputs include topic_dendrogram_clean.png, 
topic_intertopic_viral.png, viral_topic_lift.png, and topic_keywords_2.csv.

Filename II: hse_181_project.Rmd. This R Markdown file analyzes whether video title length is related to average watch time specifically for Friday uploads. 
It loads the dataset youtube_shorts_tiktok_trends_2025_labeled.csv, uses a pre-filtered dataframe friday_df, and creates a scatterplot of title_length 
versus avg_watch_time_sec with a smooth LOESS curve to capture nonlinear patterns. The plot applies a custom high-contrast theme, distinguishes viral 
from non-viral videos through color, and formats the visualization for clarity and presentation. The script then exports the final figure as a 
high-resolution PNG suitable for use in reports and slides. The primary output is friday_title_length_watchtime_600dpi.png.


