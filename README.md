# CineMatch Music Recommender

A Streamlit application that recommends songs with similar lyrics. The project ships with a pre-trained catalogue of 5,000 songs and a precomputed cosine-similarity matrix, so it is ready to run without retraining.

## Features

- Select a song from the searchable dropdown.
- Receive maximum five lyric-based song recommendations.

## Run locally

Create and activate a virtual environment, then install the required packages:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install streamlit pandas numpy
```

Start the application from the repository root:

```powershell
streamlit run app.py
```

Streamlit will print a local URL (normally `http://localhost:8501`) to open in a browser.

## Project files

| File | Purpose |
| --- | --- |
| `app.py` | Streamlit user interface and recommendation flow. |
| `TrainingModel.ipynb` | Notebook used to prepare the data and train the recommender. |
| `spotify_millsongdata.csv` | Source lyric dataset. |

## How recommendations work

The training notebook samples 5,000 tracks, cleans and stems their lyric text, transforms the lyrics using TF-IDF, and compares the resulting vectors using cosine similarity.
`app.py` ranks the five closest tracks to the selected song and omits the selected recording itself.

## Notes

The saved model artifacts must remain alongside `app.py`. Recommendation quality reflects lyric similarity only; it does not account for audio features, genre, release date, or listener behavior.

## Future Enhancements

- **Mood-based discovery:** Let listeners choose a mood such as uplifting, reflective, energetic, or calm, then blend lyric sentiment with the current similarity score.
- **Explainable matches:** Show a short “Why this match?” note that highlights meaningful shared lyric themes instead of returning a black-box list.
- **Taste profile:** Allow users to like, skip, and save songs so recommendations adapt to their personal listening patterns during a session.
- **Discovery paths:** Turn one song into an interactive trail of related tracks, helping users move gradually between artists, eras, and themes.
- **Audio-aware recommendations:** Combine lyric similarity with tempo, genre, key, and acoustic features for more balanced suggestions.
- **Playlist export:** Let users collect recommendations into a shareable playlist file or a downloadable CSV.
