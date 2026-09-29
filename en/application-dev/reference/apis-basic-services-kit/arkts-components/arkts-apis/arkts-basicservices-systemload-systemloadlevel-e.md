# SystemLoadLevel

```TypeScript
export enum SystemLoadLevel
```

Enumerates system load levels.

**Since:** 12

<!--Device-systemLoad-export enum SystemLoadLevel--><!--Device-systemLoad-export enum SystemLoadLevel-End-->

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

## LOW

```TypeScript
LOW = 0
```

The device temperature and load are low.

**Since:** 12

<!--Device-SystemLoadLevel-LOW = 0--><!--Device-SystemLoadLevel-LOW = 0-End-->

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

## NORMAL

```TypeScript
NORMAL = 1
```

The device temperature and load are normal but are approaching the medium range. You need to downgrade or reduce the load of imperceptible services.

**Since:** 12

<!--Device-SystemLoadLevel-NORMAL = 1--><!--Device-SystemLoadLevel-NORMAL = 1-End-->

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

## MEDIUM

```TypeScript
MEDIUM = 2
```

One or more device temperature or load items are slightly high, or the device temperature is in the medium range but the load is high. You need to stop or delay some imperceptible services.

**Since:** 12

<!--Device-SystemLoadLevel-MEDIUM = 2--><!--Device-SystemLoadLevel-MEDIUM = 2-End-->

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

## HIGH

```TypeScript
HIGH = 3
```

The device temperature and load are relatively high. You need to stop all imperceptible services and downgrade or reduce the load of non-critical services.

**Since:** 12

<!--Device-SystemLoadLevel-HIGH = 3--><!--Device-SystemLoadLevel-HIGH = 3-End-->

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

## OVERHEATED

```TypeScript
OVERHEATED = 4
```

The device temperature and load are high, and the device is overheated. You need to stop all imperceptible services and downgrade or reduce the load of major foreground services.

**Since:** 12

<!--Device-SystemLoadLevel-OVERHEATED = 4--><!--Device-SystemLoadLevel-OVERHEATED = 4-End-->

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

## WARNING

```TypeScript
WARNING = 5
```

The device is overheated or heavily loaded and is about to enter the Warning state. You need to stop all imperceptible services and downgrade major foreground services to the maximum extent.

**Since:** 12

<!--Device-SystemLoadLevel-WARNING = 5--><!--Device-SystemLoadLevel-WARNING = 5-End-->

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

## EMERGENCY

```TypeScript
EMERGENCY = 6
```

The device is overheated or significantly heavy loaded and is about to enter the Emergency state. You need to stop all services except those for fundamental use.

**Since:** 12

<!--Device-SystemLoadLevel-EMERGENCY = 6--><!--Device-SystemLoadLevel-EMERGENCY = 6-End-->

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

## ESCAPE

```TypeScript
ESCAPE = 7
```

The device is overheated or extremely heavy loaded and is about to enter the Escape state. You need to stop all services and take necessary emergency measures such as data backup.

**Since:** 12

<!--Device-SystemLoadLevel-ESCAPE = 7--><!--Device-SystemLoadLevel-ESCAPE = 7-End-->

**System capability:** SystemCapability.ResourceSchedule.SystemLoad
