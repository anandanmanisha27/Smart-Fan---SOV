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
- [Results and Key Insights](#-results-and-key-insights)

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
### 1. **Volume Share**
Measures the percentage of total brand mentions attributable to the target brand.

$$
\text{SoV}_{\text{volume}} = \frac{\text{Brand Mentions}}{\text{Total Brand Mentions}} \times 100
$$

---

### 2. **Engagement Share**
A weighted score combining views, likes, and comments.

$$
\text{Engagement Score} = \text{Views} + (5 \times \text{Likes}) + (10 \times \text{Comments})
$$

---

### 3. **Positive Sentiment Share**
Percentage of brand comments that are positive.

$$
\text{SoV}_{\text{positive}} = \frac{\text{Positive Brand Comments}}{\text{Total Brand Comments}} \times 100
$$

---


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

##  Usage

1.  **Add API Key**: Open the notebook and replace `"YOUR_API_KEY"` with your YouTube Data API key in the designated cell.
2.  **Customize Brands**: If needed, modify the `brands` list to include other competitors you wish to analyze.
3.  **Run the Notebook**: Execute the cells in the Jupyter Notebook sequentially from top to bottom. The script will handle data fetching, analysis, and visualization.

---

##  Results and Key Insights

The analysis of YouTube data provided a clear picture of the competitive landscape and consumer priorities in the smart fan market.

### Share of Voice Dominance
- **Atomberg leads the conversation**: Atomberg overwhelmingly dominates online discussions, securing **~74% of the volume share** from video mentions. This is significantly higher than its closest competitors, Havells (~9%) and Crompton (~8%).
- **Engagement is sky-high**: The brand's dominance is even more pronounced in engagement, where it captures nearly **80% of the engagement share**. This indicates that content featuring Atomberg is highly interactive and viewed extensively.
- **Sentiment shows opportunity**: While its overall sentiment is positive, Atomberg's positive sentiment share is slightly lower than competitors like Havells and Bajaj. This suggests that while the brand is popular, there is an opportunity to improve overall public perception and address negative feedback.

### Consumer Priorities and Keyword Analysis
- **Focus on technology and performance**: Customer comments primarily revolve around core technical and purchasing factors. The most frequently discussed topics are **`bldc fan`**, **`price`**, **`rpm`**, and **`noise`** . This shows that consumers are well-informed and interested in the fan's technology, cost, and key performance metrics.
- **Brand name is a key topic**: The term "Atomberg" itself is one of the most common keywords, highlighting strong brand recognition and direct discussion about the company.

### Specific Product & Service Feedback
- **Pain points revealed**: While overall sentiment for "bldc fan" is very positive, the analysis also uncovers specific customer issues.
- **Actionable feedback**: Recurring themes in the comments provide direct feedback, including problems with the **`fan remote`** , questions about **`service`** , compatibility issues with a **`switch board`** , and reports of **`rubbing sound`** or defective fans. This data points to clear areas for product and customer service improvements.
