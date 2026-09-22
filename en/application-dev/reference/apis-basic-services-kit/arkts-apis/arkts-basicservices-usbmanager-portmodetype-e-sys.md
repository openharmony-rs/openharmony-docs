# PortModeType (System API)

```TypeScript
export enum PortModeType
```

Enumerates USB port mode types.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## NONE

```TypeScript
NONE = 0
```

None.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## UFP

```TypeScript
UFP = 1
```

Upstream facing port, which functions as the sink of power supply.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## DFP

```TypeScript
DFP = 2
```

Downstream facing port, which functions as the source of power supply.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## DRP

```TypeScript
DRP = 3
```

Dynamic reconfiguration port (DRP), which can function as the DFP (host) or UFP (device). It is not supported currently.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## NUM_MODES

```TypeScript
NUM_MODES = 4
```

Not supported currently.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.
