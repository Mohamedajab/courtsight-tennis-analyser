# CourtSight Tennis Analyzer

CourtSight is a SwingVision-style tennis analysis prototype. It lets a player upload match or training footage and review detected shot types, estimated ball speed, confidence, rally shape, and where the ball lands on the court.

## What it does

- Upload a local tennis video
- Show staged analysis states for court calibration, pose tracking, ball tracking, and stroke classification
- Label strokes like forehand topspin, inside-out forehand, forehand slice, backhand topspin, backhand slice, serve, return, and volley
- Display estimated ball speed, confidence, rally number, and landing depth
- Plot ball landing positions on a tennis court map
- Highlight court pressure zones for deep and short landing patterns
- Filter the shot timeline by stroke family
- Show session metrics, rally stats, attack rate, and stroke breakdowns
- Export the analysis as JSON

## Current prototype

This is a front-end prototype that uses sample analysis data after a video is loaded. It is designed to show the user experience and product flow before connecting real computer-vision models. The upload flow, timeline, filters, metrics, landing map, zone summaries, insights, and JSON export all run in the browser.

## Next model work

A production version would add:

- Ball tracking across frames
- Player pose estimation
- Court line detection and calibration
- Stroke classification model
- Camera-to-court coordinate projection
- Speed estimation using frame rate and court scale
- Backend video processing queue for longer clips
- Accounts, saved sessions, and player comparison history

## Run locally

Open `outputs/tennis-vision-app.html` in a browser.

## Architecture

See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) for the current browser-only
prototype architecture, proposed computer-vision pipeline, event schema,
evaluation plan, deployment/privacy considerations and an interview walkthrough.
