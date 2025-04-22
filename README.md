# YouTube US Trending Videos Analysis

![Python](https://img.shields.io/badge/Python-3.8+-blue)
![Pandas](https://img.shields.io/badge/Pandas-1.3+-orange)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.4+-blueviolet)
![Seaborn](https://img.shields.io/badge/Seaborn-0.11+-yellowgreen)

A comprehensive exploratory data analysis (EDA) of YouTube trending videos in the US, examining content categories, publishing patterns, and engagement metrics.

##  Project Overview

This project analyzes:
- Content categories and their popularity
- Temporal publishing patterns (hourly/daily/yearly)
- Viewer engagement metrics (views, likes, comments)
- Video status (disabled features, removals)

## Dataset

**Source**: [YouTube US Videos Dataset](https://www.kaggle.com/datasets/datasnaek/youtube-new) on Kaggle  
**Size**: 40,000+ trending video records  
**Key Features**:
- `video_id`, `title`, `publish_time`
- `views`, `likes`, `dislikes`, `comment_count`
- `category_id` (mapped to 17 categories)

# Key Findings

###  Content Categories
- **Most Viewed**: Music, Entertainment, and Gaming
- **Most Frequent**: Entertainment, Comedy, and How-to/Style

### Publishing Patterns
- Peak upload hours: 2PM-5PM (EST)
- Highest upload year: 2018

###  Engagement
- Strong positive correlation between views and likes
- 5.2% of videos had comments disabled
- 1.8% were removed/errored



## Data Processing

### Data Enrichment & Feature Engineering
To enable richer analysis, the raw dataset was enhanced through the following transformations:

Datetime Extraction: Converted publish_time to datetime format and extracted:

publish_hour, publish_day, publish_month, publish_year, publish_date

### Engagement Ratios:

like_ratio = likes / views

comment_ratio = comment_count / views

### Category Mapping
Mapped category_id to human-readable category names using the official JSON metadata.
Mapped category IDs to names
category_map = {
    1: 'Film & Animation',
    2: 'Autos & Vehicles'
    
}
data['category_name'] = data['category_id'].map(category_map)

### Status Flags:

Created binary flags for: comments_disabled, ratings_disabled, video_removed
# Converted publish_time to datetime
data['publish_time'] = pd.to_datetime(data['publish_time'])

