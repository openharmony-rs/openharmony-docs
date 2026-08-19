# PortModeType（系统接口）

USB端口模式类型。

**起始版本：** 23

<!--Device-usbManager-export enum PortModeType--><!--Device-usbManager-export enum PortModeType-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## NONE

```TypeScript
NONE = 0
```

无。

**起始版本：** 23

<!--Device-PortModeType-NONE = 0--><!--Device-PortModeType-NONE = 0-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## UFP

```TypeScript
UFP = 1
```

数据上行，需要外部供电。

**起始版本：** 23

<!--Device-PortModeType-UFP = 1--><!--Device-PortModeType-UFP = 1-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## DFP

```TypeScript
DFP = 2
```

数据下行，对外提供电源。

**起始版本：** 23

<!--Device-PortModeType-DFP = 2--><!--Device-PortModeType-DFP = 2-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## DRP

```TypeScript
DRP = 3
```

既可以做DFP（HOST），也可以做UFP（DEVICE），当前不支持。

**起始版本：** 23

<!--Device-PortModeType-DRP = 3--><!--Device-PortModeType-DRP = 3-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

## NUM_MODES

```TypeScript
NUM_MODES = 4
```

当前不支持。

**起始版本：** 23

<!--Device-PortModeType-NUM_MODES = 4--><!--Device-PortModeType-NUM_MODES = 4-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

