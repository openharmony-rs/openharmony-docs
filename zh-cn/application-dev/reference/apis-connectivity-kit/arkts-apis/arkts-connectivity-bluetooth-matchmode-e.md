# MatchMode

枚举，硬件过滤匹配模式。

从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [MatchMode](arkts-connectivity-bluetoothmanager-matchmode-e.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## MATCH_MODE_AGGRESSIVE

```TypeScript
MATCH_MODE_AGGRESSIVE = 1
```

表示硬件上报扫描结果门限较低，比如扫描到的功率较低或者一段时间扫描到的次数较少也触发上报，默认值。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [MATCH_MODE_AGGRESSIVE](arkts-connectivity-bluetoothmanager-matchmode-e.md#match_mode_aggressive)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## MATCH_MODE_STICKY

```TypeScript
MATCH_MODE_STICKY = 2
```

表示硬件上报扫描结果门限较高，更高的功率门限以及扫描到多次才会上报。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [MATCH_MODE_STICKY](arkts-connectivity-bluetoothmanager-matchmode-e.md#match_mode_sticky)

**系统能力：** SystemCapability.Communication.Bluetooth.Core
