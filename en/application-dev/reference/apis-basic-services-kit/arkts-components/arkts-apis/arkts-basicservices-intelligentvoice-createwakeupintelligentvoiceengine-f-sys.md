# createWakeupIntelligentVoiceEngine (System API)

## Modules to Import

```TypeScript
import { intelligentVoice } from '@kit.BasicServicesKit';
```

## createWakeupIntelligentVoiceEngine

```TypeScript
function createWakeupIntelligentVoiceEngine(descriptor: WakeupIntelligentVoiceEngineDescriptor, callback: AsyncCallback<WakeupIntelligentVoiceEngine>): void
```

Obtains an [WakeupIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceengine-i-sys.md) instance. This method uses an asynchronous callback to return the WakeupIntelligentVoiceEngine instance.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [WakeupIntelligentVoiceEngineDescriptor](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceenginedescriptor-i-sys.md) | Yes | descriptor indicates wakeup intelligent voice engine descriptor. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[WakeupIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceengine-i-sys.md)&gt; | Yes | the callback used to return the WakeupIntelligentVoiceEngine instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700101](../errorcode-intelligentVoice.md#22700101-insufficient-memory) | No memory. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let wakeupEngineDescriptor: intelligentVoice.WakeupIntelligentVoiceEngineDescriptor = {
  needReconfirm: true,
  wakeupPhrase: 'Xiaohua Xiaohua',
}
let wakeupIntelligentVoiceEngine: intelligentVoice.WakeupIntelligentVoiceEngine | null = null;
intelligentVoice.createWakeupIntelligentVoiceEngine(wakeupEngineDescriptor, (err: BusinessError, data: intelligentVoice.WakeupIntelligentVoiceEngine) => {
  if (err) {
    console.error(`Failed to create wakeupIntelligentVoice engine, Code:${err.code}, message:${err.message}`);
  } else {
    console.info(`Succeeded in creating wakeupIntelligentVoice engine.`);
    wakeupIntelligentVoiceEngine = data;
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let wakeupEngineDescriptor: intelligentVoice.WakeupIntelligentVoiceEngineDescriptor = {
  needReconfirm: true,
  wakeupPhrase: 'Xiaohua Xiaohua',
}
let wakeupIntelligentVoiceEngine: intelligentVoice.WakeupIntelligentVoiceEngine | null = null;
intelligentVoice.createWakeupIntelligentVoiceEngine(wakeupEngineDescriptor).then((data: intelligentVoice.WakeupIntelligentVoiceEngine) => {
  wakeupIntelligentVoiceEngine = data;
  console.info(`Succeeded in creating wakeupIntelligentVoice engine.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create wakeupIntelligentVoice engine, Code:${err.code}, message:${err.message}`);
});
```


## createWakeupIntelligentVoiceEngine

```TypeScript
function createWakeupIntelligentVoiceEngine(descriptor: WakeupIntelligentVoiceEngineDescriptor): Promise<WakeupIntelligentVoiceEngine>
```

Obtains an [WakeupIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceengine-i-sys.md) instance. This method uses a promise to return the WakeupIntelligentVoiceEngine instance.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [WakeupIntelligentVoiceEngineDescriptor](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceenginedescriptor-i-sys.md) | Yes | descriptor indicates wakeup intelligent voice engine descriptor. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WakeupIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceengine-i-sys.md)&gt; | the promise used to return the WakeupIntelligentVoiceEngine instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700101](../errorcode-intelligentVoice.md#22700101-insufficient-memory) | No memory. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

See [createWakeupIntelligentVoiceEngine](#createwakeupintelligentvoiceengine)
