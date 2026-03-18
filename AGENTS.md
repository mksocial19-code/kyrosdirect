# AGENTS.md — Fix Hero-to-Canvas Seam

## The Problem
kyrosdirect/index.html has a video hero (star warp) that fades into a canvas wave animation below. There is a visible horizontal line/seam between the two — a light stripe where the video ends and the canvas begins.

## Your Job
Make the transition seamless. The video should fade into the canvas wave section with no visible line or color boundary.

## Current Setup
- `<video>` is inside `.hero` div, `position:absolute`, full coverage
- `.hero::after` has a bottom gradient fade — currently ends at `#000818`
- Canvas `#c` (id changed to `wave-bg`) is `position:absolute` inside the first `<section>` below the hero
- `.wave-top-fade` div sits above canvas, fades from `#000818` to transparent
- Canvas background gradient: `#000005` → `#000818` → `#000005`
- Body background: `#000818`

## What to Try
The seam is likely caused by one or more of these — diagnose and fix all that apply:
1. The video opacity at the bottom of the hero is not fully zero before the canvas starts
2. The hero fade gradient color doesn't exactly match the canvas top color
3. The canvas `resize()` function uses `parent.offsetHeight` — may not be sizing correctly, leaving a gap
4. There may be a margin/padding gap between the hero and first section

## Constraints
- Do NOT change any copy, layout, or section order
- Do NOT touch the canvas wave animation code (the ribbon drawing logic)
- Do NOT touch pricing cards, nav, or any other sections
- Keep the star warp video in the hero
- The fix should be CSS/JS only — no new libraries

## Done = Receipts
1. Describe exactly what was causing the seam
2. List every line changed
3. Confirm no new gaps or visual breaks introduced
