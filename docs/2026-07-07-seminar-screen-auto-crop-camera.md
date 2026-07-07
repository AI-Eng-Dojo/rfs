---
idea: true
title: "Seminar Screen Auto-Crop Camera"
summary: "A camera app that auto-detects a projected seminar screen and zooms and crops the shot automatically, so attendees no longer manually aim, zoom, and shoot."
date: 2026-07-07
tags: [mobile, productivity, events]
lang: en
translation_key: 2026-07-07-seminar-screen-auto-crop-camera
alternate_url: /2026-07-07-seminar-screen-auto-crop-camera-ja.html
---

# Seminar Screen Auto-Crop Camera

## Summary

A camera app built for tech seminar and conference attendees. It automatically detects the projected screen, zooms in, and crops the shot to the slide area, replacing the manual "aim, zoom, shoot" sequence attendees repeat throughout an event.

## Problem

At technical seminars and conferences, attendees who want to keep a copy of a slide repeat the same manual sequence every time: raise the phone, zoom in on the screen, and shoot. This is slow, distracts from listening, and often produces shaky, poorly framed photos that include the venue background or other attendees.

## Why Now

On-device machine learning for real-time rectangle detection is now common and cheap enough to run in consumer apps, as shown by document- and business-card-scanning apps. Applying the same approach specifically to projected seminar screens is a narrow, achievable product given current mobile camera and ML capability.

## First Product

A mobile app (iOS/Android). On opening the camera, the app auto-detects the projected screen area as a rectangle, then automatically zooms and crops to that area before capturing a still image. Perspective/keystone correction for angled shots is a candidate feature to evaluate after the core detection flow works.

## Potential Users

- Attendees of technical seminars and conferences
- Employees at internal company study sessions
- University students who want to record lecture slides

## Validation

The submitter and one other person have personally experienced this friction at seminars. A prior app with similar functionality, Microsoft Pix, appears to have existed but is not currently found on the App Store, which may indicate either a market-size problem or a discontinued Microsoft initiative — this needs further research.

## Open Questions

- Why did Microsoft Pix apparently get discontinued — weak market demand, or an unrelated Microsoft product strategy change? This should be researched before committing further.
- How much do document-scanner apps (e.g., CamScanner-style rectangle detection) already cover this use case, and what is the concrete differentiator (seminar-specific auto-zoom, burst capture, OCR of slide text, etc.)?
- How reliable is rectangle detection under venue lighting glare, screen keystone angles, and partial occlusion by other attendees?
- Presenters' slides are typically copyrighted; unauthorized capture or resharing could create legal or venue-policy risk. Many venues or organizers also restrict photography.
- Validation so far is limited to two people's personal experience; no broader user interviews have been conducted yet.

## Tags

mobile, productivity, events

## Sources

No external sources are included. The reference to Microsoft Pix is based on the submitter's recollection and was not independently verified against a primary source.
