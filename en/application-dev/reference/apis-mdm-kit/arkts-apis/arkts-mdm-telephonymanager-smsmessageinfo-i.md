# SmsMessageInfo

```TypeScript
interface SmsMessageInfo
```

SMS message information. Provides detailed information about an SMS message, including the message content, sender/receiver information, timestamp, and SIM card slot used.

**Since:** 26.1.0

<!--Device-telephonyManager-interface SmsMessageInfo--><!--Device-telephonyManager-interface SmsMessageInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## content

```TypeScript
content: string
```

SMS content.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SmsMessageInfo-content: string--><!--Device-SmsMessageInfo-content: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## isSender

```TypeScript
isSender: boolean
```

SMS direction: **true** indicates send, **false** indicates receive.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SmsMessageInfo-isSender: boolean--><!--Device-SmsMessageInfo-isSender: boolean-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## telephoneNumber

```TypeScript
telephoneNumber: string
```

Telephone number of the other party.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SmsMessageInfo-telephoneNumber: string--><!--Device-SmsMessageInfo-telephoneNumber: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## time

```TypeScript
time: number
```

SMS receive/send time (millisecond timestamp).

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SmsMessageInfo-time: number--><!--Device-SmsMessageInfo-time: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
