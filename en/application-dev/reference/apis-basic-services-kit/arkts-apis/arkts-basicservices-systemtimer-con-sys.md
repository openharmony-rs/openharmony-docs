# Constants (System API)

## TIMER_TYPE_EXACT

```TypeScript
const TIMER_TYPE_EXACT: number
```

Exact type. (If the system time is changed, the offset may be 1s at most.)

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## TIMER_TYPE_IDLE

```TypeScript
const TIMER_TYPE_IDLE: number
```

Idle timer type (supported only for system services).

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## TIMER_TYPE_REALTIME

```TypeScript
const TIMER_TYPE_REALTIME: number
```

CPU time type. (The start time of the timer cannot be later than the current system time.)

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## TIMER_TYPE_WAKEUP

```TypeScript
const TIMER_TYPE_WAKEUP: number
```

Wakeup type. (If the wakeup type is not set, the system does not wake up until it exits the sleep state.)

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.
