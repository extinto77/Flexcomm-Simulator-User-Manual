# nodes.toml

This file is used to describe and configure the nodes present in the simulation. 

## Contents 
1. [File format](#file-format)
2. [Configuring a Node](#configuring-a-node)
    1. [Configuring a Host](#configuring-a-host)
    2. [Configuring a Switch](#configuring-a-switch)
        1. [Energy Models](#energy-models)
            1. [Chassis](#chassis)
            2. [Interfaces](#interfaces)

---

### File format
**Each node name has to be unique.**
```toml
[node1]
# <node1 configurations>

[node2]
# <node2 configurations>
# ...
```

---

### Configuring a Node

```toml
[node]
type = "<type>"
```

- `type`: The type of this node. The available types are `host` and `switch`

---

#### Configuring a Host
```toml
[node]
type = "host"
```

**At the moment, hosts have no other extra parameters.**

---

#### Configuring a Switch
```toml
[node]
type = "switch"
cpuCapacity = "1Gbps"
zoneId = "Europe"
# intfModes = ["1Gbps", "2400Mbps", "10Gbps"] # unused parameter
```

- `cpuCapacity`: The CPU capacity of this switch. The default value is `"100Gb/s"`.
- `zoneId`: The zone where this switch is located. The default value is `""`.
- `intfModes`: The available interface modes of this switch. The default value is `[]`.

**At the moment, '`intfModes`' parameter have no impact.**

---

##### Energy Models
 
With ECOFEN, different energy models can be assigned to switches. 
<!-- A switch can have just a `Chassis` energy model, or both `Chassis` and `Interface` energy models.  -->

Any type of energy model can be defined exclusively for a particular switch, or a previously defined template in [energy-templates.toml](energy-templates.md) can be referenced.

---

###### Chassis
Reference a template:
```toml
[node.chassis]
template = "<template name>"
```

or define a new model:
```toml
[node.chassis]
model = "<model>"
#<model configs>
```

---

###### Interfaces
Reference a template:
```toml
[node.interfaces]
template = "<template name>"
```

Or define a new model:
```toml
[node.interfaces]
model = "<model>"
#<model configs>
```

For more details on how to define an energy model refer to [energy-templates.toml](energy-templates.md).

---
