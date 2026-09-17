# createEnrollIntelligentVoiceEngine (System API)

## Modules to Import

```TypeScript
import { intelligentVoice } from '@kit.BasicServicesKit';
```

## createEnrollIntelligentVoiceEngine

```TypeScript
function createEnrollIntelligentVoiceEngine(descriptor: EnrollIntelligentVoiceEngineDescriptor, callback: AsyncCallback<EnrollIntelligentVoiceEngine>): void
```

Obtains an [EnrollIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-enrollintelligentvoiceengine-i-sys.md) instance. This method uses an asynchronous callback to return the EnrollIntelligentVoiceEngine instance.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [EnrollIntelligentVoiceEngineDescriptor](arkts-basicservices-intelligentvoice-enrollintelligentvoiceenginedescriptor-i-sys.md) | Yes | descriptor indicates enroll intelligent voice engine descriptor. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[EnrollIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-enrollintelligentvoiceengine-i-sys.md)&gt; | Yes | the callback used to return the EnrollIntelligentVoiceEngine instance. |

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

let engineDescriptor: intelligentVoice.EnrollIntelligentVoiceEngineDescriptor = {
  wakeupPhrase: 'Xiaohua Xiaohua',
}
let enrollIntelligentVoiceEngine: intelligentVoice.EnrollIntelligentVoiceEngine | null = null;
intelligentVoice.createEnrollIntelligentVoiceEngine(engineDescriptor, (err: BusinessError, data: intelligentVoice.EnrollIntelligentVoiceEngine) => {
  if (err) {
    console.error(`Failed to create enrollIntelligentVoice engine, Code:${err.code}, message:${err.message}`);
  } else {
    console.info(`Succeeded in creating enrollIntelligentVoice engine.`);
    enrollIntelligentVoiceEngine = data;
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let engineDescriptor: intelligentVoice.EnrollIntelligentVoiceEngineDescriptor = {
  wakeupPhrase: 'Xiaohua Xiaohua',
}
let enrollIntelligentVoiceEngine: intelligentVoice.EnrollIntelligentVoiceEngine | null = null;
intelligentVoice.createEnrollIntelligentVoiceEngine(engineDescriptor).then((data: intelligentVoice.EnrollIntelligentVoiceEngine) => {
  enrollIntelligentVoiceEngine = data;
  console.info(`Succeeded in creating enrollIntelligentVoice engine.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to create enrollIntelligentVoice engine, Code:${err.code}, message:${err.message}`);
});
```


## createEnrollIntelligentVoiceEngine

```TypeScript
function createEnrollIntelligentVoiceEngine(descriptor: EnrollIntelligentVoiceEngineDescriptor): Promise<EnrollIntelligentVoiceEngine>
```

Obtains an [EnrollIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-enrollintelligentvoiceengine-i-sys.md) instance. This method uses a promise to return the EnrollIntelligentVoiceEngine instance.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [EnrollIntelligentVoiceEngineDescriptor](arkts-basicservices-intelligentvoice-enrollintelligentvoiceenginedescriptor-i-sys.md) | Yes | descriptor indicates enroll intelligent voice engine descriptor. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[EnrollIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-enrollintelligentvoiceengine-i-sys.md)&gt; | the promise used to return the EnrollIntelligentVoiceEngine instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700101](../errorcode-intelligentVoice.md#22700101-insufficient-memory) | No memory. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

See [createEnrollIntelligentVoiceEngine](#createenrollintelligentvoiceengine)
