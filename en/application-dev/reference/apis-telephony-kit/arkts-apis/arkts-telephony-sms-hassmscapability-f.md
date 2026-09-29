# hasSmsCapability

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## hasSmsCapability

```TypeScript
function hasSmsCapability(): boolean
```

Checks whether the current device can send and receive SMS messages. This API works in synchronous mode.

**Since:** 7

<!--Device-sms-function hasSmsCapability(): boolean--><!--Device-sms-function hasSmsCapability(): boolean-End-->

**System capability:** SystemCapability.Telephony.SmsMms

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true**: The device can send and receive SMS messages.<br>- **false**: The device cannot send or receive SMS messages. |
