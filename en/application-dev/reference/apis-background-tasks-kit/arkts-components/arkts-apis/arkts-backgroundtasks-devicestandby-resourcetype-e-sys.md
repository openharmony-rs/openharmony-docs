# ResourceType (System API)

```TypeScript
export enum ResourceType
```

The type of exemption resources requested by the application.

@enum { int }

**Since:** 10

<!--Device-deviceStandby-export enum ResourceType--><!--Device-deviceStandby-export enum ResourceType-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## NETWORK

```TypeScript
NETWORK = 1
```

The resource for non-standby network access.

**Since:** 10

<!--Device-ResourceType-NETWORK = 1--><!--Device-ResourceType-NETWORK = 1-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## RUNNING_LOCK

```TypeScript
RUNNING_LOCK = 1 << 1
```

The resource for non-standby cpu running-lock.

**Since:** 10

<!--Device-ResourceType-RUNNING_LOCK = 1 << 1--><!--Device-ResourceType-RUNNING_LOCK = 1 << 1-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## TIMER

```TypeScript
TIMER = 1 << 2
```

The resource for non-standby timer.

**Since:** 10

<!--Device-ResourceType-TIMER = 1 << 2--><!--Device-ResourceType-TIMER = 1 << 2-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## WORK_SCHEDULER

```TypeScript
WORK_SCHEDULER = 1 << 3
```

The resource for non-standby workscheduler.

**Since:** 10

<!--Device-ResourceType-WORK_SCHEDULER = 1 << 3--><!--Device-ResourceType-WORK_SCHEDULER = 1 << 3-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## AUTO_SYNC

```TypeScript
AUTO_SYNC = 1 << 4
```

The resource for non-standby automatic synchronization.

**Since:** 10

<!--Device-ResourceType-AUTO_SYNC = 1 << 4--><!--Device-ResourceType-AUTO_SYNC = 1 << 4-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## PUSH

```TypeScript
PUSH = 1 << 5
```

The resource for non-standby push-kit.

**Since:** 10

<!--Device-ResourceType-PUSH = 1 << 5--><!--Device-ResourceType-PUSH = 1 << 5-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## FREEZE

```TypeScript
FREEZE = 1 << 6
```

The resource for non-standby freezing application.

**Since:** 10

<!--Device-ResourceType-FREEZE = 1 << 6--><!--Device-ResourceType-FREEZE = 1 << 6-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.
