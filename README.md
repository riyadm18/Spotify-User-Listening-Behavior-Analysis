# Spotify-User-Listening-Behavior-Analysis

Analysis of personal Spotify streaming history to uncover patterns in listening habits, favorite artists, songs, and usage behavior, along with classification modeling to predict skip behavior.

## Business Problem
Streaming services like Spotify collect vast amounts of user listening data. This project aims to:
- Identify most played artists and songs.
- Understand listening behavior patterns (time-of-day, skipping habits, new vs repeat).
- Build a classification model to predict whether a song will be skipped.

## Dataset Overview
**Dataset:** spotify.csv  
**Rows:** 149,860  
**Columns:** 11  

**Key Columns:**
- `spotify_track_uri`: Unique track identifier  
- `ts`: Timestamp of play event  
- `platform`: Device/platform used  
- `ms_played`: Duration played (ms)  
- `track_name`, `artist_name`, `album_name`: Song metadata  
- `reason_start`, `reason_end`: Playback start/stop reasons  
- `shuffle`: Whether shuffle was on  
- `skipped`: Whether track was skipped (target for classification)

## Workflow

### 1. Data Cleaning
- Removed nulls in `reason_start` and `reason_end`.
- Converted `ts` to datetime and extracted year, month, day, hour.
- Filtered out plays shorter than 30 seconds.

### 2. Exploratory Data Analysis (EDA)
- **Top Artists**: Count plays by `artist_name`.
- **Top Songs**: Count plays by `track_name`.
- **Skipping Behavior**: Analyzed skip rates per song.
- **Listening Time-of-Day**: Grouped plays by hour to identify listening peaks.
- **New vs Repeat Listening**: Compared first-time plays vs repeats.

### 3. Classification Modeling
**Goal:** Predict `skipped` (Yes/No) using features like `ms_played`, `hour`, `platform`, `shuffle`, `reason_start`, and `reason_end`.

#### Models Used:
- Logistic Regression
- Decision Tree Classifier
- Random Forest Classifier
- Gradient Boosting Classifier

#### Evaluation Metrics:
| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| Logistic Regression | 0.9479 | 0.98 | 0.94 | 0.96 |
| Decision Tree | 0.9947 | 0.95 | 0.95 | 0.95 |
| Random Forest |  0.9958 | 0.98 | 0.94 | 0.96 | 		
| Gradient Boosting | 0.9942 | 1.00 | 0.98 | 0.94 |

### 4. Visualizations
- Bar charts for top artists and songs.
- Bar charts for hourly listening trends.
- Pie charts for skip rate distribution.

## Results Summary
- **Most played artist:** The Beatles  
- **Most played song:** Concerning Hobbits
- **Overall best classification model:** Random Forest with accuracy **99.5%**.

## Future Scope
- Tune hyperparameters for higher classification accuracy.
- Use deep learning models for skip prediction.
- Integrate with Spotify API for live data and recommendations.

## Files in Repository
| File | Description |
|------|-------------|
| spotify.csv | Raw Spotify streaming data |
| spotify.ipynb | Full EDA and classification notebook |
