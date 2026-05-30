# @ohos.stationary (Device Status Awareness Framework)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

The **stationary** module provides APIs to report the device status, including absolute still and relative still.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module cannot run on the x86 platform.

## Modules to Import

```ts
import { stationary } from '@kit.MultimodalAwarenessKit';
```

## ActivityResponse

Defines the response interface to receive the device status.

**System capability**: SystemCapability.Msdp.DeviceStatus.Stationary

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| state | [ActivityState](#activitystate) | No| No| New device status.|

## ActivityType

type ActivityType = 'still' | 'relativeStill'

Enumerates the device status types.

**System capability**: SystemCapability.Msdp.DeviceStatus.Stationary

| Type| Description|
| -------- | -------- |
| 'still' | Absolutely still.|
| 'relativeStill' | Relatively still.|

## ActivityEvent

Enumerates the device status events.

**System capability**: SystemCapability.Msdp.DeviceStatus.Stationary

| Name                            | Value   | Description                                      |
| ------------------------------ | ---- | ---------------------------------------- |
| ENTER         | 1    | Enter event.  |
| EXIT | 2   | Exit event.|
| ENTER_EXIT | 3   | Enter and exit events.|

## ActivityState

Enumerates the device statuses.

**System capability**: SystemCapability.Msdp.DeviceStatus.Stationary

| Name                            | Value   | Description                                      |
| ------------------------------ | ---- | ---------------------------------------- |
| ENTER         | 1    | Enter state.  |
| EXIT | 2   | Exit state.|

## stationary.on

on(activity: ActivityType, event: ActivityEvent, reportLatencyNs: number, callback: Callback&lt;ActivityResponse&gt;): void

Subscribes to the device status.

**System capability**: SystemCapability.Msdp.DeviceStatus.Stationary

**Parameters**

| Name                 | Type                                              | Mandatory| Description                         |
| -------------------- | -------------------------------------------------- | ---- | ---------------------------- |
| activity  | [ActivityType](#activitytype)  | Yes  | Device status type.             |
| event  | [ActivityEvent](#activityevent)  | Yes  | Event type.             |
| reportLatencyNs  | number  | Yes  | Report latency, in nanoseconds. The value range is [1000000000, 3000000000].             |
| callback             | Callback<[ActivityResponse](#activityresponse)\>  | Yes  | Callback used to receive reported data.   |

**Example**

```ts
let reportLatencyNs = 1000000000;
stationary.on('still', stationary.ActivityEvent.ENTER, reportLatencyNs, (data) => {
    console.info('data=' + JSON.stringify(data));
})
```

## stationary.once

once(activity: ActivityType, callback: Callback&lt;ActivityResponse&gt;): void

Obtains the device status.

**System capability**: SystemCapability.Msdp.DeviceStatus.Stationary

**Parameters**

| Name                 | Type                                              | Mandatory| Description                         |
| -------------------- | -------------------------------------------------- | ---- | ---------------------------- |
| activity  | [ActivityType](#activitytype)  | Yes  | Device status type.             |
| callback             | Callback<[ActivityResponse](#activityresponse)\>  | Yes  | Callback used to receive reported data.   |

**Example**

```ts
stationary.once('still', (data) => {
    console.info('data=' + JSON.stringify(data));
})
```

## stationary.off

off(activity: ActivityType, event: ActivityEvent, callback?: Callback&lt;ActivityResponse&gt;): void

Unsubscribes from the device status.

**System capability**: SystemCapability.Msdp.DeviceStatus.Stationary

**Parameters**

| Name                 | Type                                              | Mandatory| Description                         |
| -------------------- | -------------------------------------------------- | ---- | ---------------------------- |
| activity  | [ActivityType](#activitytype)  | Yes  | Device status type.             |
| event  | [ActivityEvent](#activityevent)  | Yes  | Event type.             |
| callback | Callback<[ActivityResponse](#activityresponse)\>  | No  | Callback used to receive reported data. If no value or **undefined** is passed, all callbacks associated with the specified event in the process will be unregistered. |

**Example**

```ts
stationary.off('still', stationary.ActivityEvent.ENTER);
```
