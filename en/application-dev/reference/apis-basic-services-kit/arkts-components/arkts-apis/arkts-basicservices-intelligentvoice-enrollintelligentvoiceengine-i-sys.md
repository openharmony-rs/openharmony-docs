# EnrollIntelligentVoiceEngine (System API)

```TypeScript
interface EnrollIntelligentVoiceEngine
```

Implements enroll intelligent voice engine. @typedef EnrollIntelligentVoiceEngine

**Since:** 10

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { intelligentVoice } from '@kit.BasicServicesKit';
```

## commit

```TypeScript
commit(callback: AsyncCallback<void>): void
```

Commit enroll, This method uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | the callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [22700104](../errorcode-intelligentVoice.md#22700104-enrollment-commit-failure) | Failed to commit the enrollment. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).commit((err: BusinessError) => {
    if (err) {
      console.error(`Failed to commit enroll, Code:${err.code}, message:${err.message}`);
    } else {
      console.info(`Succeeded in committing enroll.`);
    }
  });
}
```

<a id="commit-1"></a>

## commit

```TypeScript
commit(): Promise<void>
```

Commit enroll, This method uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [22700104](../errorcode-intelligentVoice.md#22700104-enrollment-commit-failure) | Failed to commit the enrollment. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).commit().then(() => {
    console.info(`Succeeded in committing enroll.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to commit enroll, Code:${err.code}, message:${err.message}`);
  });
}
```

## enrollForResult

```TypeScript
enrollForResult(isLast: boolean, callback: AsyncCallback<EnrollCallbackInfo>): void
```

Enrolls for result, This method uses an asynchronous callback to return the result.

**Since:** 23

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE and ohos.permission.MICROPHONE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLast | boolean | Yes | isLast indicates if it is the last time to enroll. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[EnrollCallbackInfo](arkts-basicservices-intelligentvoice-enrollcallbackinfo-i-sys.md)&gt; | Yes | the callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700107](../errorcode-intelligentVoice.md#22700107-system-error) | System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let callbackInfo: intelligentVoice.EnrollCallbackInfo | null = null;
if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).enrollForResult(true, (err: BusinessError, data: intelligentVoice.EnrollCallbackInfo) => {
    if (err) {
      console.error(`Failed to enroll for result, Code:${err.code}, message:${err.message}`);
    } else {
      callbackInfo = data;
      console.info(`Succeeded in enrolling for result, info:${callbackInfo}.`);
    }
  });
}
```

<a id="enrollforresult-1"></a>

## enrollForResult

```TypeScript
enrollForResult(isLast: boolean): Promise<EnrollCallbackInfo>
```

Enrolls for result, This method uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE and ohos.permission.MICROPHONE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLast | boolean | Yes | isLast indicates if it is the last time to enroll. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[EnrollCallbackInfo](arkts-basicservices-intelligentvoice-enrollcallbackinfo-i-sys.md)&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700107](../errorcode-intelligentVoice.md#22700107-system-error) | System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let callbackInfo: intelligentVoice.EnrollCallbackInfo | null = null;
if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).enrollForResult(true).then((data: intelligentVoice.EnrollCallbackInfo) => {
    callbackInfo = data;
    console.info(`Succeeded in enrolling for result, info:${callbackInfo}.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to enroll for result, Code:${err.code}, message:${err.message}`);
  });
}
```

## evaluateForResult

```TypeScript
evaluateForResult(word: string): Promise<EvaluationResult>
```

Evaluates for result, This method uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| word | string | Yes | the word to evaluate. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[EvaluationResult](arkts-basicservices-intelligentvoice-evaluationresult-i-sys.md)&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700107](../errorcode-intelligentVoice.md#22700107-system-error) | System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).evaluateForResult('word').then(
    (data: intelligentVoice.EvaluationResult) => {
    let param: intelligentVoice.EvaluationResult = data;
    console.info(`Succeeded in evaluating, param:${param}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to evaluate, Code:${err.code}, message:${err.message}`);
  });
}
```

## getParameter

```TypeScript
getParameter(key: string, callback: AsyncCallback<string>): void
```

Obtains the value of an intelligent voice parameter. This method uses an asynchronous callback to return the query result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | the key of the intelligent voice parameter whose value is to be obtained. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | the callback used to return the value of the intelligent voice parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).getParameter('key', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get parameter, Code:${err.code}, message:${err.message}`);
    } else {
      let param: string = data;
      console.info(`Succeeded in getting parameter, param:${param}`);
    }
  });
}
```

<a id="getparameter-1"></a>

## getParameter

```TypeScript
getParameter(key: string): Promise<string>
```

Obtains the value of an intelligent voice parameter. This method uses a promise to return the query result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | the key of the intelligent voice parameter whose value is to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | the promise used to return the value of the intelligent voice parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).getParameter('key').then((data: string) => {
    let param: string = data;
    console.info(`Succeeded in getting parameter, param:${param}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get parameter, Code:${err.code}, message:${err.message}`);
  });
}
```

## getSupportedRegions

```TypeScript
getSupportedRegions(callback: AsyncCallback<Array<string>>): void
```

Obtains the supported regions, This method uses an asynchronous callback to return the query result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | the callback used to return the supported regions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let regions: Array<string> | null = null;

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).getSupportedRegions((err: BusinessError, data: Array<string>) => {
    if (err) {
      console.error(`Failed to get supported regions, Code:${err.code}, message:${err.message}`);
    } else {
      regions = data;
      console.info(`Succeeded in getting supported regions, regions:${regions}.`);
    }
  });
}
```

<a id="getsupportedregions-1"></a>

## getSupportedRegions

```TypeScript
getSupportedRegions(): Promise<Array<string>>
```

Obtains the supported regions, This method uses a promise to return the query result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | the promise used to return the supported regions. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let regions: Array<string> | null = null;
if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).getSupportedRegions().then((data: Array<string>) => {
    regions = data;
    console.info(`Succeeded in getting supported regions, regions:${regions}.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get supported regions, Code:${err.code}, message:${err.message}`);
  });
}
```

## init

```TypeScript
init(config: EnrollEngineConfig, callback: AsyncCallback<void>): void
```

Initials the engine, This method uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [EnrollEngineConfig](arkts-basicservices-intelligentvoice-enrollengineconfig-i-sys.md) | Yes | config indicates enroll engine configuration. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | the callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |
| [22700103](../errorcode-intelligentVoice.md#22700103-initialization-failed) | Init failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let config: intelligentVoice.EnrollEngineConfig = {
  language: 'zh',
  region: 'CN',
}
if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).init(config, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to initialize enrollIntelligentVoice engine. Code:${err.code}, message:${err.message}`);
    } else {
      console.info(`Succeeded in initializing enrollIntelligentVoice engine.`);
    }
  });
}
```

<a id="init-1"></a>

## init

```TypeScript
init(config: EnrollEngineConfig): Promise<void>
```

Initials the engine, This method uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [EnrollEngineConfig](arkts-basicservices-intelligentvoice-enrollengineconfig-i-sys.md) | Yes | config indicates enroll engine configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |
| [22700103](../errorcode-intelligentVoice.md#22700103-initialization-failed) | Init failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let config: intelligentVoice.EnrollEngineConfig = {
  language: 'zh',
  region: 'CN',
}
if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).init(config).then(() => {
    console.info(`Succeeded in initializing enrollIntelligentVoice engine.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to initialize enrollIntelligentVoice engine. Code:${err.code}, message:${err.message}`);
  });
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases the engine, This method uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | the callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release enrollIntelligentVoice engine, Code:${err.code}, message:${err.message}`);
    } else {
      console.info(`Succeeded in releasing enrollIntelligentVoice engine.`);
    }
  });
}
```

<a id="release-1"></a>

## release

```TypeScript
release(): Promise<void>
```

Releases the engine, This method uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).release().then(() => {
    console.info(`Succeeded in releasing enrollIntelligentVoice engine.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to release enrollIntelligentVoice engine, Code:${err.code}, message:${err.message}`);
  });
}
```

## setParameter

```TypeScript
setParameter(key: string, value: string, callback: AsyncCallback<void>): void
```

Sets an intelligent voice parameter. This method uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | the key of the intelligent voice parameter to set. |
| value | string | Yes | the value of the intelligent voice parameter to set. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | the callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).setParameter('scene', '0', (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set parameter, Code:${err.code}, message:${err.message}`);
    } else {
      console.info(`Succeeded in setting parameter`);
    }
  });
}
```

<a id="setparameter-1"></a>

## setParameter

```TypeScript
setParameter(key: string, value: string): Promise<void>
```

Sets an intelligent voice parameter. This method uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | the key of the intelligent voice parameter to set. |
| value | string | Yes | the value of the intelligent voice parameter to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).setParameter('scene', '0').then(() => {
    console.info(`Succeeded in setting parameter`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to set parameter, Code:${err.code}, message:${err.message}`);
  });
}
```

## setSensibility

```TypeScript
setSensibility(sensibility: SensibilityType, callback: AsyncCallback<void>): void
```

Sets sensibility, This method uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensibility | [SensibilityType](arkts-basicservices-intelligentvoice-sensibilitytype-e-sys.md) | Yes | sensibility to set. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | the callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).setSensibility(intelligentVoice.SensibilityType.LOW_SENSIBILITY, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set sensibility, Code:${err.code}, message:${err.message}`);
    } else {
      console.info(`Succeeded in setting sensibility.`);
    }
  });
}
```

<a id="setsensibility-1"></a>

## setSensibility

```TypeScript
setSensibility(sensibility: SensibilityType): Promise<void>
```

Sets sensibility, This method uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensibility | [SensibilityType](arkts-basicservices-intelligentvoice-sensibilitytype-e-sys.md) | Yes | sensibility to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).setSensibility(intelligentVoice.SensibilityType.LOW_SENSIBILITY).then(() => {
    console.info(`Succeeded in setting sensibility.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to set sensibility, Code:${err.code}, message:${err.message}`);
  });
}
```

## setWakeupHapInfo

```TypeScript
setWakeupHapInfo(info: WakeupHapInfo, callback: AsyncCallback<void>): void
```

Sets wakeup hap information, This method uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [WakeupHapInfo](arkts-basicservices-intelligentvoice-wakeuphapinfo-i-sys.md) | Yes | info indicates wakeup hap information. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | the callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let info: intelligentVoice.WakeupHapInfo = {
  bundleName: 'com.wakeup',
  abilityName: 'WakeUpExtAbility',
}
if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).setWakeupHapInfo(info, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set wakeup hap info, Code:${err.code}, message:${err.message}`);
    } else {
      console.info(`Succeeded in setting wakeup hap info.`);
    }
  });
}
```

<a id="setwakeuphapinfo-1"></a>

## setWakeupHapInfo

```TypeScript
setWakeupHapInfo(info: WakeupHapInfo): Promise<void>
```

Sets wakeup hap information, This method uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [WakeupHapInfo](arkts-basicservices-intelligentvoice-wakeuphapinfo-i-sys.md) | Yes | info indicates wakeup hap information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let info: intelligentVoice.WakeupHapInfo = {
  bundleName: 'com.wakeup',
  abilityName: 'WakeUpExtAbility',
}
if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).setWakeupHapInfo(info).then(() => {
    console.info(`Succeeded in setting wakeup hap info.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to set wakeup hap info, Code:${err.code}, message:${err.message}`);
  });
}
```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops the engine, This method uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | the callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).stop((err: BusinessError) => {
    if (err) {
      console.error(`Failed to stop enrollIntelligentVoice engine, Code:${err.code}, message:${err.message}`);
    } else {
      console.info(`Succeeded in stopping enrollIntelligentVoice engine.`);
    }
  });
}
```

<a id="stop-1"></a>

## stop

```TypeScript
stop(): Promise<void>
```

Stops the engine, This method uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (enrollIntelligentVoiceEngine != null) {
  (enrollIntelligentVoiceEngine as intelligentVoice.EnrollIntelligentVoiceEngine).stop().then(() => {
    console.info(`Succeeded in stopping enrollIntelligentVoice engine.`);
  }).catch((err:BusinessError) => {
    console.error(`Failed to stop enrollIntelligentVoice engine, Code:${err.code}, message:${err.message}`);
  });
}
```
