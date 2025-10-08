# 🎧 Spotify Streaming Analysis and Context-Aware Recommendation System

---

## 📝 Project Overview

The primary goal of this project was to leverage personal music listening data and external audio feature data to analyze streaming habits and build a context-aware music recommendation system.

### Key Highlights

* **Dual Data Integration:** The system integrates two critical data sources: the user's personal streaming history (including duration, skips, etc.) and a public dataset containing detailed audio features (e.g., danceability, energy, valence) for tracks.

* **Personalized Analysis:** Clean and analyze individual Spotify streaming history to understand listening habits across different times and seasons.

* **Content-Based Recommendation:** Implement a Content-Based Filtering system using k-Nearest Neighbors (NearestNeighbors) to suggest novel music.

* **Contextualization:** Incorporate engineered features like season and time_of_day to generate recommendations tailored to the user's current listening context.

---

## 📈 Modeling: Content-Based Recommendation

**Modeling Approach: Content-Based Filtering**

* The system employs **Content-Based Filtering**. Tracks are recommended based on their similarity to the average characteristics (audio features) of music the user has previously enjoyed within a specific time and seasonal context.

**Algorithm: k-Nearest Neighbors (k-NN)**
* The NearestNeighbors algorithm from sklearn was used to find similar tracks.

* The prediction logic involves:

1. Context Filtering: Isolate historical tracks matching the user's current context (e.g., "Autumn - Morning").

2. Centroid Calculation: Calculate the mean feature vector (centroid) of all audio features for the historically listened tracks in that context.

3. Similarity Search: Use k-NN on the entire library to find the k tracks whose feature vectors are closest to the calculated centroid.

4. Novelty Filter: Apply the rule to exclude tracks by the user's Top 20 artists before presenting the final recommendations.
