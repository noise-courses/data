# Performance Anomalies (FCC Measuring Broadband America)

Active measurements from FCC [Measuring Broadband America](https://www.fcc.gov/general/measuring-broadband-america) whiteboxes in ISP subscriber homes, March 2022. One row per test, keyed by `unit_id` (the measurement device) and `dtime` (UTC).

| File | Size | Test |
|---|---|---|
| `curr_httpgetmt.csv.gz` | 23 MB | multi-threaded HTTP download ("speed") |
| `curr_ping.csv.gz` | 0.9 MB | UDP/ICMP latency |
| `curr_webget.csv.gz` | 35 MB | web page fetch |
| `curr_dns_small.csv.gz` | 17 MB | DNS lookup |

`curr_httpgetmt` has a header row. **The other three do not**; their columns, in order, from the FCC data dictionary:

- `curr_ping`: `unit_id, dtime, target, rtt_avg, rtt_min, rtt_max, rtt_std, successes, failures` (times in microseconds)
- `curr_webget`: `unit_id, dtime, target, address, fetch_time, bytes_total, bytes_sec, objects, threads, requests, connections, reused_connections, lookups, request_total_time, request_min_time, request_avg_time, request_max_time, ttfb_total, ttfb_min, ttfb_avg, ttfb_max, lookup_total_time, lookup_min_time, lookup_avg_time, lookup_max_time, successes, failures` (times in microseconds)
- `curr_dns_small`: `unit_id, dtime, nameserver, lookup_host, response_ip, rtt, successes, failures` (`rtt` in microseconds)

A few rows are malformed; `pd.read_csv(..., on_bad_lines='skip')` drops them.
