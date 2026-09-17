# TimerOptions (System API)

Defines the initialization options for the system timer.

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { systemTimer } from '@kit.BasicServicesKit';
```

## callback

```TypeScript
callback?: () => void
```

Callback to be executed by the user.

The default value is empty.

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## autoRestore

```TypeScript
autoRestore?: boolean
```

Whether the timer is restored after the device is restarted.

The value **true** means that the timer is restored after the restart, and the value **false** means the opposite.

This parameter can be set to **true** only for timers that are not of the **TIMER_TYPE_REALTIME** type and have **wantAgent** configured.

The default value is **false**.

**Type:** boolean

**Since:** 15

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## interval

```TypeScript
interval?: number
```

Interval between two consecutive timers, in milliseconds.

For a repeating timer, the minimum value of **interval** is 1s and the maximum value is 365 days. It is recommended that the value be greater than or equal to 5000 ms.

For a one-shot timer, the value is **0**.

Default value: **0**.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## name

```TypeScript
name?: string
```

Timer name, with a maximum length of 64 bytes.

A UID cannot contain two timers with the same name. If a timer with the same name as an existing timer is created, the existing timer is destroyed.

The default value is an empty string.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## repeat

```TypeScript
repeat: boolean
```

Whether the timer is a repeating timer. The value **true** means that the timer is a repeating timer, and **false** means that the timer is a one-shot timer.

**Type:** boolean

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## type

```TypeScript
type: number
```

Timer types. Use pipe (|) symbol

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

**WantAgent** object of the notification to be sent when the timer expires. (An application **MainAbility** can be started, but not a **ServiceAbility**.)

The default value is empty.

**Type:** [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md)

**Since:** 7

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.
