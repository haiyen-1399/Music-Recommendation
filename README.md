# Project Overview

Objective

- Analyze personal Spotify streaming history and public track metadata to understand listening patterns and generate personalized track recommendations.

Key highlights

- Data sources: personal Spotify streaming exports (`Spotify Extended Streaming History/`) combined with public track CSVs in `Track Data/` for enrichment.
- Data processing: cleaned and merged streaming events with track metadata (normalize names/IDs, parse timestamps, and compute listening counts and session summaries).
- Model approach: a lightweight recommendation pipeline combining content-similarity (audio features) with popularity and recency weighting to produce top-N personalized recommendations.
- Key insights from the analysis:
	- Listening behavior is concentrated around a small subset of artists and tracks; top 10% of tracks account for a large share of plays.
	- The model tends to recommend a mix of familiar favorites (high play-count, high popularity) and less-popular but similar tracks (high content similarity) to encourage discovery.
	- Time-based patterns (weekday vs weekend, hour-of-day) influence short-term recommendations when recency is weighted.
	- Audio-feature clustering (tempo, energy, danceability) helps surface tracks that match the user's typical listening “mood.”
	- Evaluation (interactive in the notebook) shows the pipeline balances relevance and novelty; use the notebook cells to view precision/diversity trade-offs on your data.

## Results

- Artifacts produced by the analysis:
	- Cleaned, merged dataframes of streaming events and enriched track metadata.
	- Visualizations of listening trends, most-played artists/tracks, and audio-feature distributions.
	- A ranked set of recommended tracks per user-profile snapshot (top-N lists), produced by the content+popularity pipeline.
	- Lightweight evaluation outputs (e.g., precision@K, recommendation diversity and novelty summaries) computed in the notebook.

## Next steps

- Convert the notebook's recommendation pipeline into a small script (`scripts/generate_recs.py`) so recommendations can be generated non-interactively.
- Add automated unit tests for data-loading and normalization steps to prevent schema regressions when adding new CSVs.
- Experiment with collaborative filtering or hybrid models (e.g., matrix factorization or factorization machines) to improve personalization.
- Add a simple web UI or static export (CSV/JSON) for viewing the top-N recommendations and example explanations (why a track was recommended).

