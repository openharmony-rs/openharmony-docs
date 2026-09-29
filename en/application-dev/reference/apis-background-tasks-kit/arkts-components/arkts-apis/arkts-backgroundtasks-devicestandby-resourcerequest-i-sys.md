# ResourceRequest (System API)

```TypeScript
export interface ResourceRequest
```

The request of standby resources.

@interface ResourceRequest

**Since:** 10

<!--Device-deviceStandby-export interface ResourceRequest--><!--Device-deviceStandby-export interface ResourceRequest-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { deviceStandby } from '@kit.BackgroundTasksKit';
```

## duration

```TypeScript
duration: number
```

The exemption duration. <br>Unit:s

**Type:** number

**Since:** 10

<!--Device-ResourceRequest-duration: int--><!--Device-ResourceRequest-duration: int-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## name

```TypeScript
name: string
```

The application name.

**Type:** string

**Since:** 10

<!--Device-ResourceRequest-name: string--><!--Device-ResourceRequest-name: string-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## reason

```TypeScript
reason: string
```

The reason for the request.

**Type:** string

**Since:** 10

<!--Device-ResourceRequest-reason: string--><!--Device-ResourceRequest-reason: string-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## resourceTypes

```TypeScript
resourceTypes: number
```

The set of resource types that an application requests.

**Type:** number

**Since:** 10

<!--Device-ResourceRequest-resourceTypes: int--><!--Device-ResourceRequest-resourceTypes: int-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

The application uid.

**Type:** number

**Since:** 10

<!--Device-ResourceRequest-uid: int--><!--Device-ResourceRequest-uid: int-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.
