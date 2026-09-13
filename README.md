# CourtSight Tennis Analyzer

CourtSight is a SwingVision-style tennis analysis prototype. It lets a player upload match or training footage and review detected shot types, estimated ball speed, and where the ball lands on the court.

## What it does

- Upload a local tennis video
- Show analysis states for shot detection
- Label strokes like forehand topspin, forehand slice, backhand topspin, backhand slice, serve, and volley
- Display estimated ball speed
- Plot ball landing positions on a tennis court map
- Show session metrics and stroke breakdowns

## Current prototype

This first version is a front-end prototype that uses sample analysis data after a video is loaded. It is designed to show the user experience and product flow before connecting real computer-vision models.

## Next model work

A production version would add:

- Ball tracking across frames
- Player pose estimation
- Court line detection and calibration
- Stroke classification model
- Camera-to-court coordinate projection
- Speed estimation using frame rate and court scale

## Run locally

Open `outputs/tennis-vision-app.html` in a browser.
