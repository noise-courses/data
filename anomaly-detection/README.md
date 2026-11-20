# Anomaly-detection traces

Label files are `HH:MM:SS, description`, one event per line. **All times are
wall-clock time in America/New_York, the zone the captures were taken in.**
Packet timestamps in a pcap are UTC; convert them to New York time before
comparing with the labels (for example `pd.to_datetime(ts, unit="s", utc=True)
.dt.tz_convert("America/New_York")`). Reading the pcap in your own machine's
local zone is the usual reason the labels look misaligned.

| Trace | First packet (New York) | Last packet | Labels |
|---|---|---|---|
| `nestcam_live.pcap` | 2016-07-29 16:10:03 | 16:30:03 | `nestcam_live_labels.txt` |
| `google_home.pcap` | 2017-12-07 15:48:41 | 16:26:21 | `google_home_labels.txt` |
| `tplink_switch.pcap` | | | none |
| `demo.pcap` | | | `demo.csv` (netml demo) |

## google_home.pcap

The Google Home is `172.24.1.51`. The capture has two parts:

- **15:48:41 to 16:12:22, setup.** The device joins the network, checks in, and
  at 16:09:41 downloads a software update from `dl.google.com` (about 13 MB),
  then restarts at 16:12:22. Treat this part as idle or setup, not as device
  interaction. (There are also a few short media fetches between 15:51 and
  15:55, during setup.)
- **16:12:22 to 16:26:21, the experiment.** Voice interactions show up as
  bursts of about 200 KB *uploaded* to the Assistant endpoint
  (`www.google.com`, `216.58.219.196`), one burst per utterance, with little
  downloaded. Music shows up as a *download* stream from a Google media server
  (`r5---sn-....googleusercontent.com`, `74.125.174.139`): a 6.6 MB buffer
  fill at 16:18:01, then about 1.1 MB every 26 seconds until 16:19:42.

`google_home_labels.txt` was rebuilt from the traffic on 2026-11-20. The
original log (`google_home_labels_original.txt`) was written against a clock
that does not match the capture (its times run from 1:45:00 to 1:57:00), and
it omits several interactions. Anchoring its "1:51:00, started playing music"
to the stream start at 16:18:01 puts its 1:47:00 query at 16:14:01, its
1:55:00 music request at 16:22:01 and its 1:53:00 stop at 16:20:01, all within
a few seconds of what the traffic shows, so the rebuilt file keeps the original
event names where they match and adds the interactions the log left out.
Two things to know: the second music request (16:22:03, three attempts) was
not followed by any stream, so there is no second music period; and
"stopped playing music" is the last stream data at 16:19:42, after which the
device played out its buffer.

The restart at 16:12:22 and the interactions in the first minute after it
(16:12:35 to 16:12:57) are real activity but noisy; it is fine to start your
analysis at 16:13:00.

## nestcam_live.pcap

Labels alternate `livestream` and `motion` every two to three minutes from
16:10:00; the capture starts three seconds later, so no offset is needed.
