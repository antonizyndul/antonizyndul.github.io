---
layout: post
title: "Building a MOCAP annotation pipeline with ELAN"
date: 2025-04-10
description: "Notes from the POST-GEST project on aligning motion capture output with ELAN annotation tiers for gesture and posture."
tags: [methods, ELAN, MOCAP]
---

Getting motion capture data and ELAN to talk to each other is more involved than it sounds. Here are the practical notes from the POST-GEST project.

## The basic challenge

MOCAP systems export time-series data at high frame rates — typically 100–200 Hz. ELAN works with video, usually at 25–50 fps. The annotation tiers in ELAN are linked to a video track, so the first task is getting a synchronised video that you can use as the reference.

We used a setup where a GoPro recorded the session alongside the MOCAP capture, with a manual sync point (a visible hand clap at the start of each trial). Not elegant, but reliable.

## Extracting usable video

The pipeline looked like this:

```bash
# Export video from the MOCAP software at 25fps
# Then align to session start using ffmpeg
ffmpeg -i raw_session.mp4 -ss 00:00:02.4 -c copy aligned_session.mp4
```

The offset (`00:00:02.4` here) was determined manually from the sync clap.

## ELAN tier structure

For the POST-GEST study, the main tiers were:

- `gesture_phase` — preparation / stroke / hold / retraction
- `posture` — upright / lean_forward / lean_back / lateral
- `gesture_form` — open hand / point / grip / etc.

Each tier was time-aligned to the video, which gave us timestamps we could then cross-reference with the MOCAP frame data.

## Lessons learned

The biggest pain point was drift — even with a clean sync point, tiny differences in frame rate between the GoPro and the MOCAP system accumulated over long sessions. For the next study I'd use a hardware sync trigger rather than a manual clap.

If you're setting up a similar pipeline and want to compare notes, feel free to get in touch.
