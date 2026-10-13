# Using the CourtSight prototype

CourtSight is a browser-only interface demonstration. Its shot labels, speeds,
confidence values and landing positions come from a fixed sample dataset, even
when you select your own video. The staged analysis messages do not run computer
vision models. Do not interpret the displayed values as measurements of your clip.

## Open the app

Open `outputs/tennis-vision-app.html` in a modern browser. No package installation,
model download, API key or backend is needed.

If you prefer a local HTTP address and have Python installed, run this from the
repository root:

```bash
python -m http.server 8000 --bind 127.0.0.1
```

Then visit `http://localhost:8000/outputs/tennis-vision-app.html`. On systems where
Python is named `python3`, substitute that command. Stop the server with Ctrl+C.
This serves static files only; it does not add video processing or storage.

## Walk through the demo

1. Select **Use sample** to explore without supplying a video. This loads sample
   shot events, not a bundled video recording.
2. Use the stroke-family filters to narrow the event list. Select a row to update
   the shot overlay and timeline marker. Row selection does not seek the video.
3. Compare the landing map, stroke breakdown and summary metrics. Filters change
   the event list, not the full-session metrics or exported event set.
4. Optionally choose **Upload video** and select a local video your browser can
   play. The video is loaded through a browser object URL; the current app does
   not upload it to a server. Sample analysis starts automatically.
5. **Analyze** replays the simulated stages and restores the same sample events.
   A different clip does not produce different inferred strokes.
6. Select **Export JSON** to download `courtsight-analysis.json`.

The export contains `generatedAt`, `session` (the selected session mode) and
`events` (the current sample event array). It does not contain the original video
bytes or a filtered-only subset. Its timestamp is the export time, not the
recording date or evidence of an inference run.

## Reset and privacy boundaries

The clear control resets the visible panels and progress indicator. It does not
erase `currentEvents`, clear the video source or provide a secure deletion
guarantee; exporting afterwards can still include the sample events. Reload the
page to start a fresh interface session.

The app has no saved-session store or JSON import workflow. A downloaded export
is a separate local file; reloading does not reopen it. Handle any selected
personal footage according to your own consent and storage requirements.

## Troubleshooting

- **Video does not play:** `video/*` in the file picker is not a codec guarantee.
  Try a clip supported by your browser; opening the UI does not transcode it.
- **Results do not match the match footage:** expected for this prototype.
  Displayed events are samples, not model predictions.
- **Use sample shows no video:** the button supplies events only.
- **Filters do not change the export:** expected; export uses all current events.
- **Nothing appears after clearing:** select Use sample or Analyze to repopulate
  the visualisations.
- **Download does not appear:** check the browser's download settings and location.

## Manual review checklist

For a local UI check, confirm that sample events render, filters update the list,
row selection changes the overlay, a supported video plays, and the JSON export
contains the three top-level fields above. Keep this separate from model accuracy
testing: no model inference or accuracy evaluation is implemented here.

See [Architecture](ARCHITECTURE.md) for the proposed real CV pipeline and its
evaluation requirements.
