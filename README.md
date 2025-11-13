# Noise Lab Course Datasets

This repository contains datasets used across various Noise Lab courses. The data is organized by assignment/course topic.

## Contents

### Anomaly Detection (`data/anomaly-detection/`)

All files for the anomaly detection assignment:

- **demo.pcap** (2.1 MB) - Demo traffic from the University of New Brunswick's Intrusion Detection Systems dataset
- **demo.csv** (3.1 MB) - Labels for the demo traffic
- **google_home.pcap** (74 MB) - Google Home device traffic with voice queries and music playing
- **google_home_labels.txt** - Activity timestamps (voice queries, music playing start/stop)
- **nestcam_live.pcap** (9.7 MB) - Nest camera traffic with livestream and motion detection
- **nestcam_live_labels.txt** - Event timestamps (livestream, motion detection)
- **tplink_switch.pcap** (52 KB) - TP-Link smart switch traffic

## Usage

Clone this repository to access the datasets:

```bash
git clone https://github.com/noise-courses/data.git
```

Then reference the data in your assignments using the appropriate paths.

## Attribution

- Demo data (demo.pcap, demo.csv): University of New Brunswick Intrusion Detection Systems dataset
- Smart home device traces: Noise Lab device captures
