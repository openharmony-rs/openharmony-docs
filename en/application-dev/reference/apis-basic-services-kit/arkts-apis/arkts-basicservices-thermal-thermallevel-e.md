# ThermalLevel

```TypeScript
export enum ThermalLevel
```

Enumerates thermal levels.

**Since:** 8

<!--Device-thermal-export enum ThermalLevel--><!--Device-thermal-export enum ThermalLevel-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

## COOL

```TypeScript
COOL = 0
```

The device is cool, and services are not restricted.

**Since:** 8

<!--Device-ThermalLevel-COOL = 0--><!--Device-ThermalLevel-COOL = 0-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

## NORMAL

```TypeScript
NORMAL = 1
```

The device is in the normal temperature range but it is getting warm. You need to downgrade or reduce the load of imperceptible services.

**Since:** 8

<!--Device-ThermalLevel-NORMAL = 1--><!--Device-ThermalLevel-NORMAL = 1-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

## WARM

```TypeScript
WARM = 2
```

The device is warm. You need to stop or delay some imperceptible services.

**Since:** 8

<!--Device-ThermalLevel-WARM = 2--><!--Device-ThermalLevel-WARM = 2-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

## HOT

```TypeScript
HOT = 3
```

The device is heating up. You need to stop all imperceptible services and downgrade or reduce the load of non- critical services.

**Since:** 8

<!--Device-ThermalLevel-HOT = 3--><!--Device-ThermalLevel-HOT = 3-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

## OVERHEATED

```TypeScript
OVERHEATED = 4
```

The device is overheated. You need to stop all imperceptible services and downgrade or reduce the load of major foreground services.

**Since:** 8

<!--Device-ThermalLevel-OVERHEATED = 4--><!--Device-ThermalLevel-OVERHEATED = 4-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

## WARNING

```TypeScript
WARNING = 5
```

The device is overheated and is about to enter the emergency state. You need to stop all imperceptible services and downgrade major foreground services to the maximum extent.

**Since:** 8

<!--Device-ThermalLevel-WARNING = 5--><!--Device-ThermalLevel-WARNING = 5-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

## EMERGENCY

```TypeScript
EMERGENCY = 6
```

The device has entered the emergency state. You need to stop all services except those for fundamental use.

**Since:** 8

<!--Device-ThermalLevel-EMERGENCY = 6--><!--Device-ThermalLevel-EMERGENCY = 6-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

## ESCAPE

```TypeScript
ESCAPE = 7
```

The device is about to enter the escape state. You need to stop all services and take necessary emergency measures such as data backup.

**Since:** 11

<!--Device-ThermalLevel-ESCAPE = 7--><!--Device-ThermalLevel-ESCAPE = 7-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager
