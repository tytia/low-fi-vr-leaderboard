# Low-Fi VR Leaderboard

A just-for-fun scoreboard for participants in the FIT3144 Low-Fi VR pointing study: an overall board and one board per technique (Gaze + Dwell, Hand Ray, Hand Touch), ranked by Fitts' throughput (bits/s).

It's a static page (`index.html`) that reads `scores.csv`, so GitHub Pages can host it as-is.

## Adding a participant

Only people with push access to this repo can change the board: the page just reads `scores.csv`. Results are added from the Godot project with `tools/add_to_leaderboard.py`:

```
python tools/add_to_leaderboard.py path/to/ID-1234-summary.csv --name "Speedy" --skip-pilot --push
```

It averages TP and MT over each condition's rings, appends one line per condition to `scores.csv`, and with `--push` commits and pushes. Without `--push` it only edits the file. Copy the summary CSV off the phone first (`Android/data/<package>/files/Documents/LowFiVR/`).

`scores.csv` columns: `name,condition,tp,mt_ms,error_pct,date`. If the same name and condition appear twice, the later line wins, so to correct a result just append a new line (or edit the file on GitHub).

## Local preview

`fetch` doesn't work from `file://`, so serve the folder:

```
python -m http.server 8000
```

then open http://localhost:8000.
