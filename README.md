# Flexcomm Simulator Documentation 

## Contents

1. [Configuration Files](#configuration-files)
    1. [Topologies Directory Structure](#topologies-directory-structure)
    2. [Files](#files)
2. [Makefile Runtime Flags](#makefile-runtime-flags)
3. [EnergyApi](#energyapi)

---

## Configuration files

#### Topologies Directory Structure

The configurations for each topology should be placed inside the `topologies` folder and follow the following structure:

```
...
├── topologies
│   ├── energy-templates.toml
│   ├── topology1
│   │   ├── applications.toml
│   │   ├── configs.toml
|   |   ├── energy-templates.toml
│   │   ├── estimate.json
│   |   ├── estimate1.json
│   |   ├── estimate2.json
│   │   ├── flex.json
│   │   ├── flex1.json
│   │   ├── flex2.json
│   │   ├── links.toml
│   │   └── nodes.toml
│   └── topology2
│       ├── applications1.toml
│       ├── applications2.toml
│       ├── configs.toml
│       ├── flex.json
│       ├── links.toml
│       └── nodes.toml
... 
```

#### Files
Each topology has its own configuration files:
  - [`nodes.toml`](nodes.md)
  - [`links.toml`](links.md)
  - [`applications.toml`](applications.md)
  - [`configs.toml`](configs.md)
  - [`energy-templates.toml`](energy-templates.md) (optional)
  - [`flex.json`](flexibility.md) (optional)
  - [`estimate.json`](flexibility.md) (optional)


The top-level `energy-templates.toml` file applies to all the configurations. However, each topology can also specify a local templates file. In this case, for templates with equal names, the local file overrides the global configuration. 

---

**For how to specify different measurement units in files, see [Units](units.md).**

---

## Makefile Runtime Flags

| Flag | Description | Default Value |
| ---- | ----------- | ------------- |
| DATE | The date of the simulation run | day of the run |
| OUTPUTS | The output path of log files | outputs |
| TOPO | The topology scenario to simulate | example |
| ROUTING | Which controller to use (`ospf.Ospf`, `my-controller.NewRoutingAlgo`, etc...) | ospf.Ospf |
| APPFILE | The applications file to load | applications.toml |
| ESTIFILE | The energy estimate file to load | estimate.json |
| FLEXFILE | The flexibility file to load | flex.json |

---

## EnergyApi
The `EnergyApi` can be used by Controllers to access all the energy data provided in the flexibility configuration files using the methods:
- `EnergyApi.get_flex_array_consumption(<id/zoneId>)`
- `EnergyApi.get_estimate_array(<id/zoneId>)`.

It is also possible to get just one value of the energy data using the methods:
- `EnergyApi.get_flex_by_swName(<id>, <index>)`
- `EnergyApi.get_flex_by_swZone(<id>, <index>)`
- `EnergyApi.get_estimate_by_swName(<id>, <index>)`
- `EnergyApi.get_estimate_by_swZone(<id>, <index>)`

---
