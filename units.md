# Units 
<!-- For more details on Time and Data Rate units refer to [ns-3's documentation](https://www.nsnam.org/doxygen/) -->

## Contents

1. [Time](#time)
2. [Data Rate](#data-rate)

---

### Time 

Time fields follow the format:
`"<value><unit>"`

- Supported units:

  ```
  ns (nanoseconds)
  us (microseconds)
  ms (milliseconds)
  s (seconds)
  min (minutes)
  h (hours)
  ```

- Examples:
  ```
  "1ns"
  "60s"
  "30min"
  "24h"
  ```

---

### Data Rate

Data Rate fields follow the format: `"<value><unit>"`

- Supported units:

  ```
  bps, b/s, Bps, B/s
  kbps, kb/s, kBps, kB/s, Kbps, Kb/s, KBps, KB/s
  Kips, Kib/s, KiBps, KiB/s
  Mbps, Mb/s, MBps, MB/s, 
  Mibps, Mib/s, MiBps, MiB/s
  Gbps, Gb/s, GBps, GB/s, 
  Gibps, Gib/s, GiBps, GiB/s
  ```

- Examples:
  ```
  "128kb/s"
  "1MBps"
  "1Gbps"
  "1024GiB/s"
  ```

- Conversion:

  | Prefix | Value |
  | ------ | ----- |
  | "b" | 1 |
  | "k", "K" | 1000 |
  | "Ki" | 1024 |
  | "M"	| 1000000 |
  | "Mi" | 1024 Ki |
  | "G" | 10^9 |
  | "Gi" | 1024 Mi |

  | Symbol | Meaning |
  | ------ | ------- |
  | "b" | bits |
  | "B" | 8-bit bytes |
  | "ps", "/s" | per second |