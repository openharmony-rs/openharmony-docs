# CallLogInfo

```TypeScript
interface CallLogInfo
```

Call log information. Provides detailed information about a call log entry, including call duration, direction (incoming/outgoing), timestamp, and SIM card slot used.

**Since:** 26.1.0

<!--Device-telephonyManager-interface CallLogInfo--><!--Device-telephonyManager-interface CallLogInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## createTime

```TypeScript
createTime: number
```

Time when a call record is created(timestamp, in seconds). When an incoming call is made, the ringing start time is displayed. When an outgoing call is made, the ringing start time is displayed.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CallLogInfo-createTime: number--><!--Device-CallLogInfo-createTime: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## endTime

```TypeScript
endTime: number
```

Call end time(timestamp, in seconds). When a call is not connected, the time when the call is hung up is the time when the call is disconnected.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CallLogInfo-endTime: number--><!--Device-CallLogInfo-endTime: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## isIncoming

```TypeScript
isIncoming: boolean
```

Call direction: **true** indicates an incoming call, and **false** indicates an outgoing call.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CallLogInfo-isIncoming: boolean--><!--Device-CallLogInfo-isIncoming: boolean-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## slotId

```TypeScript
slotId: number
```

SIM card slot ID. The value 0 indicates card slot 1, and the value 1 indicates card slot 2.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CallLogInfo-slotId: number--><!--Device-CallLogInfo-slotId: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## startTime

```TypeScript
startTime: number
```

Call connection time (timestamp, in seconds). The value is 0 when the call is not connected.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CallLogInfo-startTime: number--><!--Device-CallLogInfo-startTime: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## telephoneNumber

```TypeScript
telephoneNumber: string
```

Phone number of the other party.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CallLogInfo-telephoneNumber: string--><!--Device-CallLogInfo-telephoneNumber: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
