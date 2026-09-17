# ResourceType (System API)

The type of exemption resources requested by the application.

@enum { int }

**Since:** 10

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## NETWORK

```TypeScript
NETWORK = 1
```

The resource for non-standby network access.

**Since:** 10

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## RUNNING_LOCK

```TypeScript
RUNNING_LOCK = 1 << 1
```

The resource for non-standby cpu running-lock.

**Since:** 10

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## TIMER

```TypeScript
TIMER = 1 << 2
```

The resource for non-standby timer.

**Since:** 10

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## WORK_SCHEDULER

```TypeScript
WORK_SCHEDULER = 1 << 3
```

The resource for non-standby workscheduler.

**Since:** 10

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## AUTO_SYNC

```TypeScript
AUTO_SYNC = 1 << 4
```

The resource for non-standby automatic synchronization.

**Since:** 10

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## PUSH

```TypeScript
PUSH = 1 << 5
```

The resource for non-standby push-kit.

**Since:** 10

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## FREEZE

```TypeScript
FREEZE = 1 << 6
```

The resource for non-standby freezing application.

**Since:** 10

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.
