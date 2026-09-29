# PortModeType (System API)

```TypeScript
export enum PortModeType
```

Enumerates USB port mode types.

**Since:** 9

<!--Device-usbManager-export enum PortModeType--><!--Device-usbManager-export enum PortModeType-End-->

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## NONE

```TypeScript
NONE = 0
```

None.

**Since:** 9

<!--Device-PortModeType-NONE = 0--><!--Device-PortModeType-NONE = 0-End-->

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## UFP

```TypeScript
UFP = 1
```

Upstream facing port, which functions as the sink of power supply.

**Since:** 9

<!--Device-PortModeType-UFP = 1--><!--Device-PortModeType-UFP = 1-End-->

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## DFP

```TypeScript
DFP = 2
```

Downstream facing port, which functions as the source of power supply.

**Since:** 9

<!--Device-PortModeType-DFP = 2--><!--Device-PortModeType-DFP = 2-End-->

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## DRP

```TypeScript
DRP = 3
```

Dynamic reconfiguration port (DRP), which can function as the DFP (host) or UFP (device). It is not supported currently.

**Since:** 9

<!--Device-PortModeType-DRP = 3--><!--Device-PortModeType-DRP = 3-End-->

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

## NUM_MODES

```TypeScript
NUM_MODES = 4
```

Not supported currently.

**Since:** 9

<!--Device-PortModeType-NUM_MODES = 4--><!--Device-PortModeType-NUM_MODES = 4-End-->

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.
