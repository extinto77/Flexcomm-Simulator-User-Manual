# Flexibility 

## Contents
1. [flex.json](#flexjson)
    1. [File Format](#file-format-1)
2. [estimate.json](#estimatejson)
    1. [File Format](#file-format-2)

---

## flex.json
The `flex.json` file should include, for each network switch, the associated energy flexibility vector.

#### File Format <a id="file-format-1"></a>
```jsonc
{
  "switch1": [
    100,
    -200,
    ...
  ],
  "switch2": [
    300,
    50,
    ...
  ],
  ...
}
```

---

## estimate.json
The `estimate.json` file should include, for each network switch, the associated energy consumption estimate.

### File Format <a id="file-format-2"></a>
```jsonc
{
  "switch1": [
    1502,
    3000,
    ...
  ],
  "switch2": [
    5123,
    3012,
    ...
  ],
  ...
}
```

---


