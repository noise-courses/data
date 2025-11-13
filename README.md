# Noise Lab Course Datasets

This repository contains datasets used across various Noise Lab courses. The data is organized by assignment/course topic.

## Contents

### Anomaly Detection (`anomaly-detection/`)

All files for the anomaly detection assignment:

- **demo.pcap** (2.1 MB) - Demo traffic from the University of New Brunswick's Intrusion Detection Systems dataset
- **demo.csv** (3.1 MB) - Labels for the demo traffic
- **google_home.pcap** (74 MB) - Google Home device traffic with voice queries and music playing
- **google_home_labels.txt** - Activity timestamps (voice queries, music playing start/stop)
- **nestcam_live.pcap** (9.7 MB) - Nest camera traffic with livestream and motion detection
- **nestcam_live_labels.txt** - Event timestamps (livestream, motion detection)
- **tplink_switch.pcap** (52 KB) - TP-Link smart switch traffic

### Latency Geo-Clustering (`latency-geo-clustering/`)

All files for the latency geo-clustering assignment:

- **Chicago_speedtests.csv** (23.7 MB) - Ookla speed test measurements from Chicago (January 2022 - May 2023), Comcast subscribers only
- **City_boundaries.csv** (484 KB) - Chicago city boundary data for spatial analysis

### Video Conference QoE (`video-conference-qoe/`)

All files for the video conference QoE assignment:

- **teams.csv** (32 MB) - Microsoft Teams video conference traffic data

### Video QoE (`video-qoe/`)

Files for the video QoE assignment:

- **netflix.pcap** (22 MB) - Netflix video streaming traffic capture

**Large Dataset File (separate download required):**

The main dataset file `video_dataset.pkl` (105 MB) exceeds GitHub's file size limits and must be downloaded separately from Google Drive:

```bash
# Download video_dataset.pkl (105 MB)
curl -L "https://drive.usercontent.google.com/download?id=1iI1tos08p9FJBI-ADR9b_iFObWRwXANX&export=download&confirm=t" -o video_dataset.pkl
```

This file contains 4000 video sessions from Netflix, YouTube, Twitch, and Amazon Prime Video for training video quality inference models.

## Usage

Clone this repository to access the datasets:

```bash
git clone https://github.com/noise-courses/data.git
```

Then reference the data in your assignments using the appropriate paths.

## Attribution

- Demo data (demo.pcap, demo.csv): University of New Brunswick Intrusion Detection Systems dataset
- Smart home device traces: Noise Lab device captures
