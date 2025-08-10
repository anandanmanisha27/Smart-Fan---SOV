# Smart Fan Brand Analysis: Share of Voice & Sentiment

This repository contains a Python project that analyzes YouTube data to measure the **Share of Voice (SoV)** and **consumer sentiment** for various smart fan brands, with a special focus on **Atomberg**.

The project fetches video data, statistics, and comments using the YouTube Data API, identifies brand mentions, calculates SoV based on multiple metrics, and performs keyword extraction and sentiment analysis on user comments.


---

##  Table of Contents

- [Features](#-features)
- [Project Overview](#-project-overview)
- [Methodology](#-methodology)
- [Getting Started](#-getting-started)
- [Usage](#-usage)
- [Results](#-results)

---

##  Features

- **YouTube Data Extraction**: Fetches video details, stats (views, likes), and comments via the YouTube API.
- **Share of Voice (SoV) Analysis**: Calculates SoV using three different metrics:
  - **Volume Share**: Based on the number of video mentions.
  - **Engagement Share**: A weighted score of views, likes, and comments.
  - **Positive Sentiment Share**: Based on the proportion of positive comments for each brand.
- **Keyword Extraction**: Uses `KeyBERT` to identify the most discussed topics and technical terms in user comments.
- **Sentiment Analysis**: Leverages `VADER` to analyze the sentiment of comments and associates it with specific keywords.
- **Data Visualization**: Generates bar charts to clearly display SoV comparisons, keyword frequencies, and sentiment distributions.

---

##  Project Overview

The analysis is conducted in a Jupyter Notebook (`.ipynb`) and follows these main steps:

1.  **Setup**: Installs and imports all necessary libraries and initializes the YouTube API client with an API key.
2.  **Data Collection**: Searches YouTube for videos using queries like "Atomberg fan" and "Atomberg fan review". It fetches video details, statistics, and comments for the top 100 videos based on view count.
3.  **Brand Identification**: A predefined list of fan brands [cite: 178, 180] [cite_start]is used to scan video titles and descriptions to tag videos with the brands they mention.
4.  **SoV Calculation**: The notebook computes the Share of Voice for each brand based on volume, engagement, and positive sentiment.
5.  **Comment Analysis**: User comments are cleaned, and `KeyBERT` is used to extract key topics. `VADER` then performs sentiment analysis on these topics.

---

##  Methodology

### Data Source
The primary data source is the **YouTube Data API v3**. The analysis focuses on videos and comments related to smart fan brands.

### Share of Voice (SoV)
SoV is a measure of a brand's market visibility. This project calculates it using these formulas:

-   **Volume Share**: The proportion of brand mentions relative to the total mentions of all competing brands
-   **Engagement Share**: A weighted score that accounts for user interaction, calculated based on views, likes, and comments.
-   **Positive Sentiment Share**: The percentage of positive comments for a brand compared to its total comments, indicating public perception.

### Keyword & Sentiment Analysis
-   **Qdrant**: Comments are embedded and stored in a Qdrant vector database for efficient retrieval and analysis.
-   **KeyBERT**: This tool extracts keywords and phrases to identify what consumers are talking about most.
-   **VADER**: Chosen for its effectiveness on social media text, VADER assigns a sentiment score (positive, negative, neutral) to comments.

---

##  Getting Started

### Installation

1. install these:
    ```bash
    pip install google-api-python-client pandas textblob vaderSentiment qdrant-client sentence-transformers keybert matplotlib
    ```

---

## ⚙️ Usage

1.  **Add API Key**: Open the notebook and replace `"YOUR_API_KEY"` with your YouTube Data API key in the designated cell.
2.  **Customize Brands**: If needed, modify the `brands` list to include other competitors you wish to analyze.
3.  **Run the Notebook**: Execute the cells in the Jupyter Notebook sequentially from top to bottom. The script will handle data fetching, analysis, and visualization.

---

## 📈 Results

The final output of the project includes:

-   **Share of Voice DataFrames**: Tables showing the calculated SoV for each brand across different metrics.
-   **Visualizations**:
    -   A grouped bar chart comparing the Volume, Engagement, and Positive Sentiment SoV for Atomberg and its competitors.
    -   Bar charts detailing the frequency of top keywords discussed in comments.
    -   A stacked bar chart showing the sentiment distribution (positive, neutral, negative) for each major keyword.
-   **Keyword Insights**: A list of the top technical and non-technical terms, revealing what features and issues are most important to consumers (e.g., `bldc fan`, `rpm`, `noise`, `air delivery`).

These results provide valuable insights into brand performance, competitive standing, and consumer perception in the smart fan market.
