---
{"dg-publish":true,"permalink":"/osu-replay-viewer/"}
---

Related: #
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-08-2023
***

# OSU Replay Viewer

Goal: Be able to view and edit osu replay files, then export them as .osr files

- Input .osr file
- Process it
- Allow the client to **view** the process replay
- Allow the client to **edit** the replay
- Export
	- As .osr or maybe as a video

## Possible [[Design Patterns\|Design Patterns]]

- Adapter pattern (for LZMA algorithm)
- [[Model-View-Controller\|Model-View-Controller]]