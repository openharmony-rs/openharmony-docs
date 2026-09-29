# ExemptedAppInfo (System API)

```TypeScript
export interface ExemptedAppInfo
```

Information about an exempted application.

@interface ExemptedAppInfo

**Since:** 10

<!--Device-deviceStandby-export interface ExemptedAppInfo--><!--Device-deviceStandby-export interface ExemptedAppInfo-End-->

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

<!--Device-ExemptedAppInfo-duration: int--><!--Device-ExemptedAppInfo-duration: int-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## name

```TypeScript
name: string
```

The application name.

**Type:** string

**Since:** 10

<!--Device-ExemptedAppInfo-name: string--><!--Device-ExemptedAppInfo-name: string-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

## resourceTypes

```TypeScript
resourceTypes: number
```

The set of resource types that an application requests.

**Type:** number

**Since:** 10

<!--Device-ExemptedAppInfo-resourceTypes: int--><!--Device-ExemptedAppInfo-resourceTypes: int-End-->

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.
