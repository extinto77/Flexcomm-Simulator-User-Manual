# links.toml

This file is used to describe and configure the links present in the simulation. 

## Contents

1. [File format](#file-format)
2. [Configuring a Link](#configuring-a-link)

---

### File format
**Each link name has to be unique.**

```toml
[link1]
#<link configs>

[link2]
#<link configs>
#...
```

---

### Configuring a link
```toml
[link]
edges = ["node1", "node2"]
dataRate = "10Gbps"
delay = "100ms"
```

- `edges`: List containing the two nodes connected by this link.

- `dataRate`: The data rate of this link. The default value is `"1Gbps"`.

- `delay`: The delay of this link. The default value is `"1ns"`.
**At the moment, '`delay`' parameter have no impact.**

---

