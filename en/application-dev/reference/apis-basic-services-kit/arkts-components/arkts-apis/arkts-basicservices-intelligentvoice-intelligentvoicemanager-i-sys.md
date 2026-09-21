# IntelligentVoiceManager (System API)

```TypeScript
interface IntelligentVoiceManager
```

Implements intelligent voice management. @typedef IntelligentVoiceManager

**Since:** 10

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { intelligentVoice } from '@kit.BasicServicesKit';
```

## getCapabilityInfo

```TypeScript
getCapabilityInfo(): Array<IntelligentVoiceEngineType>
```

Obtains capability information.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[IntelligentVoiceEngineType](arkts-basicservices-intelligentvoice-intelligentvoiceenginetype-e-sys.md)&gt; | array of supported IntelligentVoiceEngineType. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
if (intelligentVoiceManager != null) {
  let info = intelligentVoiceManager.getCapabilityInfo();
}
```

## off('serviceChange')

```TypeScript
off(type: 'serviceChange', callback?: Callback<ServiceChangeType>): void
```

Unsubscribes service change events.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serviceChange' | Yes | Type of the event to listen for. Only the serviceChange event is supported. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ServiceChangeType](arkts-basicservices-intelligentvoice-servicechangetype-e-sys.md)&gt; | No | Callback is invoked when the event is triggered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
if (intelligentVoiceManager != null) {
  intelligentVoiceManager.off('serviceChange');
}
```

## on('serviceChange')

```TypeScript
on(type: 'serviceChange', callback: Callback<ServiceChangeType>): void
```

Subscribes service change events. When the state of intelligent voice service changes, the callback is invoked.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serviceChange' | Yes | Type of the event to listen for. Only the serviceChange event is supported. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ServiceChangeType](arkts-basicservices-intelligentvoice-servicechangetype-e-sys.md)&gt; | Yes | Callback is invoked when the event is triggered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
if (intelligentVoiceManager != null) {
  intelligentVoiceManager.on('serviceChange', (serviceChangeType: intelligentVoice.ServiceChangeType) => {});
}
```
