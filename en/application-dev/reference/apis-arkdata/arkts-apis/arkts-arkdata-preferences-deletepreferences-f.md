# deletePreferences

## Modules to Import

```TypeScript
import { preferences } from '@kit.ArkData';
```

## deletePreferences

```TypeScript
function deletePreferences(context: Context, name: string, callback: AsyncCallback<void>): void
```

Deletes a specified **Preferences** instance from the cache. If the **Preferences** instance has a corresponding persistent file, the persistent file is also deleted. This API uses an asynchronous callback to return the result. Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner. This API cannot be called concurrently with other **preferences** APIs.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context.<br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |
| name | string | Yes | Name of the **Preferences** instance. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [15500010](../errorcode-preferences.md#15500010-failed-to-delete-the-user-preference-persistence-file) | Failed to delete the user preferences persistence file. |
| [15500000](../errorcode-preferences.md#15500000-internal-error) | Inner error.<br>**Applicable version:** 11 and later |

**Examples**

FA model:

```TypeScript
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

preferences.deletePreferences(context, 'myStore', (err: BusinessError) => {
  if (err) {
    console.error("Failed to delete preferences. Code = " + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in deleting preferences.");
})
```

Stage model:

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    preferences.deletePreferences(this.context, 'myStore', (err: BusinessError) => {
      if (err) {
        console.error("Failed to delete preferences. Code = " + err.code + ", message = " + err.message);
        return;
      }
      console.info("Succeeded in deleting preferences.");
    })
  }
}
```


<a id="deletepreferences-1"></a>

## deletePreferences

```TypeScript
function deletePreferences(context: Context, options: Options, callback: AsyncCallback<void>): void
```

Deletes a specified **Preferences** instance from the cache. If the **Preferences** instance has a corresponding persistent file, the persistent file is also deleted. This API uses an asynchronous callback to return the result. Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner. This API cannot be called concurrently with other **preferences** APIs.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context.<br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |
| options | [Options](arkts-arkdata-preferences-options-i.md) | Yes | Configuration options of the **Preferences** instance. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [15500010](../errorcode-preferences.md#15500010-failed-to-delete-the-user-preference-persistence-file) | Failed to delete the user preferences persistence file. |
| [15501001](../errorcode-preferences.md#15501001-stage-model-required) | The operations is supported in stage mode only. |
| [15501002](../errorcode-preferences.md#15501002-invalid-datagroupid-parameter-in-options) | Invalid dataGroupId. |
| [15500000](../errorcode-preferences.md#15500000-internal-error) | Inner error.<br>**Applicable version:** 11 and later |

**Examples**

FA model:

```TypeScript
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

let options: preferences.Options = { name: 'myStore' };
preferences.deletePreferences(context, options, (err: BusinessError) => {
  if (err) {
    console.error("Failed to delete preferences. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in deleting preferences.");
})
```

Stage model:

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    preferences.deletePreferences(this.context, options, (err: BusinessError) => {
      if (err) {
        console.error("Failed to delete preferences. code =" + err.code + ", message = " + err.message);
        return;
      }
      console.info("Succeeded in deleting preferences.");
    })
  }
}
```


<a id="deletepreferences-2"></a>

## deletePreferences

```TypeScript
function deletePreferences(context: Context, name: string): Promise<void>
```

Deletes a specified **Preferences** instance from the cache. If the **Preferences** instance has a corresponding persistent file, the persistent file is also deleted. This API uses a promise to return the result. Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner. This API cannot be called concurrently with other **preferences** APIs.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context.<br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |
| name | string | Yes | Name of the **Preferences** instance. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [15500010](../errorcode-preferences.md#15500010-failed-to-delete-the-user-preference-persistence-file) | Failed to delete the user preferences persistence file. |
| [15500000](../errorcode-preferences.md#15500000-internal-error) | Inner error.<br>**Applicable version:** 11 and later |

**Examples**

FA model:

```TypeScript
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

let sp = preferences.deletePreferences(context, 'myStore');
sp.then(() => {
  console.info("Succeeded in deleting preferences.");
}).catch((err: BusinessError) => {
  console.error("Failed to delete preferences. Code = " + err.code + ", message = " + err.message);
})
```

Stage model:

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let sp = preferences.deletePreferences(this.context, 'myStore');
    sp.then(() => {
      console.info("Succeeded in deleting preferences.");
    }).catch((err: BusinessError) => {
      console.error("Failed to delete preferences. code =" + err.code + ", message = " + err.message);
    })
  }
}
```


<a id="deletepreferences-3"></a>

## deletePreferences

```TypeScript
function deletePreferences(context: Context, options: Options): Promise<void>
```

Deletes a specified **Preferences** instance from the cache. If the **Preferences** instance has a corresponding persistent file, the persistent file is also deleted. This API uses a promise to return the result. Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner. This API cannot be called concurrently with other **preferences** APIs.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context.<br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |
| options | [Options](arkts-arkdata-preferences-options-i.md) | Yes | Configuration options of the **Preferences** instance. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [15500010](../errorcode-preferences.md#15500010-failed-to-delete-the-user-preference-persistence-file) | Failed to delete the user preferences persistence file. |
| [15501001](../errorcode-preferences.md#15501001-stage-model-required) | The operations is supported in stage mode only. |
| [15501002](../errorcode-preferences.md#15501002-invalid-datagroupid-parameter-in-options) | Invalid dataGroupId. |
| [15500000](../errorcode-preferences.md#15500000-internal-error) | Inner error.<br>**Applicable version:** 11 and later |

**Examples**

FA model:

```TypeScript
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

let options: preferences.Options = { name: 'myStore' };
let sp = preferences.deletePreferences(context, options);
sp.then(() => {
  console.info("Succeeded in deleting preferences.");
}).catch((err: BusinessError) => {
  console.error("Failed to delete preferences. code =" + err.code + ", message = " + err.message);
})
```

Stage model:

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    let sp = preferences.deletePreferences(this.context, options);
    sp.then(() => {
      console.info("Succeeded in deleting preferences.");
    }).catch((err: BusinessError) => {
      console.error("Failed to delete preferences. code =" + err.code + ", message = " + err.message);
    })
  }
}
```
