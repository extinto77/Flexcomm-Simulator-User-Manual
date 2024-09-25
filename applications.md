# applications.toml

This file is used to describe and configure the applications present in the simulation. Applications generate traffic in the simulation. 

## Contents
1. [File format](#file-format)
2. [Configuring an Application](#configuring-an-application)
    1. [constSend](#constsend)
    2. [sinSend](#sinsend)

---

### File format
**Each application name has to be unique.**

```toml
[app1]
#<application configs>

[app2]
#<application configs>
#...
```

---

### Configuring an Application

```toml
[app]
type = "<type>"
startTime = "1s"
stopTime = "60s"
host = "host1"
remote = "host2"
```

- `type`: The type of the application. The available types are: `constSend` and `sinSend`.

- `startTime`: The time to start the application. The default value is `"1s"`, and this is the lowest acceptable value.

- `stopTime`: The time to stop the application. The default and max value equals the simulation stop time.

- `host`: The host where to install this application.

- `remote`: The remote host where to send the traffic.

---

##### constSend
This application generates traffic at a continuous Data Rate. See [OnOffApplication](https://www.nsnam.org/docs/release/3.35/doxygen/classns3_1_1_on_off_application.html) for more details.

```toml
[app]
type = "constSend"
dataRate = "1Mbps"
```

- `dataRate`: The sustained data rate to generate the traffic. The default value is `"500kb/s"`


---

##### sinSend

This application generates traffic with a Data Rate that changes in time following a `sin` function. The Data Rate $DR$ at a given time $t$ is given by: 
$$DR=A * sin(B * t + C) + Const$$ 

```toml
[app]
type = "sinSend"
const = "10Mbps"
a = "2Mbps"
b = 0.1
c = 3.0
unit = "min"
```

- `const`: The constant Data Rate. The default value is `"3Mb/s"`.

- `a`: The amplitude of the variation in the constant Data Rate. The default value is `"1Mb/s"`.

- `b`: This factor controls the function's frequency. The default value is `0.5`

- `c`: This factor shifts the function left and right. The default value is `0.0`

- `unit`: The time unit $t$ used to calculate the Data Rate. The default value is `"min"` (minutes).

---
