# ThermalLevel

热档位信息。

**起始版本：** 8

<!--Device-thermal-export enum ThermalLevel--><!--Device-thermal-export enum ThermalLevel-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

## COOL

```TypeScript
COOL = 0
```

表明设备处于清凉状态，业务执行不受热控的限制。

**起始版本：** 8

<!--Device-ThermalLevel-COOL = 0--><!--Device-ThermalLevel-COOL = 0-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

## NORMAL

```TypeScript
NORMAL = 1
```

表明设备温度正常，但邻近温热状态，无感知业务应降低规格和负载。

**起始版本：** 8

<!--Device-ThermalLevel-NORMAL = 1--><!--Device-ThermalLevel-NORMAL = 1-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

## WARM

```TypeScript
WARM = 2
```

表明设备进入温热状态，无感知业务应暂停或延迟运行。

**起始版本：** 8

<!--Device-ThermalLevel-WARM = 2--><!--Device-ThermalLevel-WARM = 2-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

## HOT

```TypeScript
HOT = 3
```

表明设备发热明显，无感知业务应停止，非关键业务应降低规格及负载。

**起始版本：** 8

<!--Device-ThermalLevel-HOT = 3--><!--Device-ThermalLevel-HOT = 3-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

## OVERHEATED

```TypeScript
OVERHEATED = 4
```

表明设备发热严重，无感知业务与非关键业务应停止，前台关键业务应降低规格及负载。

**起始版本：** 8

<!--Device-ThermalLevel-OVERHEATED = 4--><!--Device-ThermalLevel-OVERHEATED = 4-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

## WARNING

```TypeScript
WARNING = 5
```

表明设备过热即将进入紧急状态，整机资源供给大幅降低，停止所有非关键业务，前台关键业务应降低至最低规格。

**起始版本：** 8

<!--Device-ThermalLevel-WARNING = 5--><!--Device-ThermalLevel-WARNING = 5-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

## EMERGENCY

```TypeScript
EMERGENCY = 6
```

表明设备已经进入过热紧急状态，整机资源供给降至最低，设备功能受限，仅保留基础功能可用。

**起始版本：** 8

<!--Device-ThermalLevel-EMERGENCY = 6--><!--Device-ThermalLevel-EMERGENCY = 6-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

## ESCAPE

```TypeScript
ESCAPE = 7
```

表明设备即将进入热逃生状态，所有业务将被强制停止，业务需做好逃生措施，例如保存重要数据等。

**说明**: 从API version 11开始支持。

**起始版本：** 11

<!--Device-ThermalLevel-ESCAPE = 7--><!--Device-ThermalLevel-ESCAPE = 7-End-->

**系统能力：** SystemCapability.PowerManager.ThermalManager

