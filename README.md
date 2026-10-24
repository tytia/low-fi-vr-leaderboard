# Low-Fi VR Leaderboard

A just-for-fun scoreboard for participants in the FIT3144 Low-Fi VR pointing study: an overall board and one board per technique (Gaze + Dwell, Hand Ray, Hand Touch), ranked by Fitts' throughput (bits/s).

It's a static page (`index.html`) that reads `scores.csv`, so GitHub Pages can host it as-is.

## Adding a participant

1. Copy `ID-xxxx-summary.csv` off the phone (`Android/data/<package>/files/Documents/LowFiVR/`).
2. Open the live site, expand **Experimenter: add a participant**, type the name they want shown, and drop the CSV in. It's processed in the browser only.
3. Copy the generated lines and paste them at the end of `scores.csv` (on GitHub: open the file, click the pencil, paste, then **Commit changes**). The site updates within about a minute.

`scores.csv` columns: `name,condition,tp,mt_ms,error_pct,date`. If the same name and condition appear twice, the later line wins, so to correct a result just append a new line.

## Local preview

`fetch` doesn't work from `file://`, so serve the folder:

```
python -m http.server 8000
```

then open http://localhost:8000.
