# SystemLoadLevel

系统负载融合档位。

**起始版本：** 12

<!--Device-systemLoad-export enum SystemLoadLevel--><!--Device-systemLoad-export enum SystemLoadLevel-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

## LOW

```TypeScript
LOW = 0
```

设备当前温度、负载比较低，无高负载场景。

**起始版本：** 12

<!--Device-SystemLoadLevel-LOW = 0--><!--Device-SystemLoadLevel-LOW = 0-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

## NORMAL

```TypeScript
NORMAL = 1
```

设备温度、负载正常，但邻近中等状态，无感知业务应降低规格和负载。

**起始版本：** 12

<!--Device-SystemLoadLevel-NORMAL = 1--><!--Device-SystemLoadLevel-NORMAL = 1-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

## MEDIUM

```TypeScript
MEDIUM = 2
```

设备温度、负载有一项或多项稍高，或者当前处于高负载场景，无感知业务应暂停或延迟运行。

**起始版本：** 12

<!--Device-SystemLoadLevel-MEDIUM = 2--><!--Device-SystemLoadLevel-MEDIUM = 2-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

## HIGH

```TypeScript
HIGH = 3
```

设备当前发热明显或负载比较高，或处于负载温度中等但处于高负载场景，无感知业务应停止，非关键业务应降低规格及负载。

**起始版本：** 12

<!--Device-SystemLoadLevel-HIGH = 3--><!--Device-SystemLoadLevel-HIGH = 3-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

## OVERHEATED

```TypeScript
OVERHEATED = 4
```

设备发热严重或者负载较重，无感知业务与非关键业务应停止，前台关键业务应降低规格及负载。

**起始版本：** 12

<!--Device-SystemLoadLevel-OVERHEATED = 4--><!--Device-SystemLoadLevel-OVERHEATED = 4-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

## WARNING

```TypeScript
WARNING = 5
```

设备过热或负载过重，或者温度较高但处于高负载场景，即将进入紧急状态，整机资源供给大幅降低，停止所有非关键，前台关键业务应降低至最低规格。

**起始版本：** 12

<!--Device-SystemLoadLevel-WARNING = 5--><!--Device-SystemLoadLevel-WARNING = 5-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

## EMERGENCY

```TypeScript
EMERGENCY = 6
```

设备已经进入过热状态或负载极高紧急状态，或接近紧急状态但处于高负载场景，整机资源供给降至最低，设备功能受限，仅保留基础功能可用。

**起始版本：** 12

<!--Device-SystemLoadLevel-EMERGENCY = 6--><!--Device-SystemLoadLevel-EMERGENCY = 6-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

## ESCAPE

```TypeScript
ESCAPE = 7
```

设备即将进入热逃生状态或当前负载已经不堪重负，或已经处于紧急状态且高负载状态，所有业务将被强制停止，业务需做好逃生措施，例如保存重要数据等。

**起始版本：** 12

<!--Device-SystemLoadLevel-ESCAPE = 7--><!--Device-SystemLoadLevel-ESCAPE = 7-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

