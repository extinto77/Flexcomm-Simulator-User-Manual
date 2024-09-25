# configs.toml

This file is used to set global simulator configurations. 

rever !!!

## Contents
1. [File format](#file-format)
    1. [[simulator]](#simulator)
    2. [[ecofen]](#ecofen)
    3. [[switchStats]](#switchstats)
    4. [[linkStats]](#linkstats)
    5. [[pathHistory]](#pathhistory)

---

### File format
The configuration file is composed of multiple sections. Each section controls different components of the simulator.

```toml
[simulator]
stopTime = "30min" 

[ecofen]
logFile = true
logInterval = "30s"

[switchStats]
enable = true
logInterval = "30s"

[linkStats]
logFile = true
logInterval = "30s"

[pathHistory]
logFile = true
```

---

##### [simulator]

- `stopTime`: When to stop the simulation. This can be considered as the simulation duration. The default value is `"60s"`, and the value can't be greater than 1 day (`"24h"`).

---

<!-- ##### [log] -->

<!-- - Log components that when set to true, will output log messages in Debug builds. -->

<!-- **This section can be left empty.** -->

<!-- --- -->

##### [ecofen]

- `logFile`: When `true`, ECOFEN trace files are generated. The default value is `false`.

- `logInterval`: The interval to log energy consumption. The default value is `"5s"`.

---

##### [switchStats]

- `enable`: When `true`, trace files with switch statistics are generated. The default value is `false`.

- `logInterval`: The interval to log information. The default value is `"5s"`.

---

##### [linkStats]

- `logFile`: When `true`, trace files are generated. The default value is `false`.

- `logInterval`: The interval to log information. The default value is `"5s"`. 

---

##### [pathHistory]

- `logFile`: When `true`, trace files with path updates are generated. The default value is `false`.

---