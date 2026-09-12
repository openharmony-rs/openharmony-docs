# @ohos.data.preferences (User Preferences)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @cuile44-->
<!--Designer: @cuile44-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=baacd5e603827a8080bb1e15309bc06852b1fd80 translatedAt=2026-09-04T03:41:58.490Z pushedAt=2026-09-09T09:11:03.726Z -->

The **Preferences** module provides APIs for processing data in the form of key-value (KV) pairs, including querying, modifying, and persisting KV pairs.

Data is stored in the form of key-value (KV) pairs, where the key is a string and the value can be a number, string, boolean, array, Uint8Array, object, or bigint.

The user preference persistent files are stored in the [preferencesDir](../../application-models/application-context-stage.md#obtaining-application-file-paths) directory. Before creating a preferences object, ensure that the **preferencesDir** directory is readable and writeable. The [encryption level](../apis-ability-kit/js-apis-app-ability-contextConstant.md#areamode) of the persistent file directory determines the access to the files. For details, see [Application File Directory and Application File Path](../../file-management/app-sandbox-directory.md#application-file-directory-and-application-file-path).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Preferences are not thread-safe and may cause file damage and data loss when used in multi-process scenarios. Do not use preferences in multi-process scenarios.

## Modules to Import

```ts
import { preferences } from '@kit.ArkData';
```

## Constants

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

| Name            | Type     | Read-Only| Description                                   |
| ---------------- | -------- | ---- | --------------------------------------- |
| MAX_KEY_LENGTH   | number   | Yes  | Maximum key length, which is 1,024 bytes.    |
| MAX_VALUE_LENGTH | number   | Yes  | Maximum value length, which is 16 MB.|


## preferences.getPreferences

getPreferences(context: Context, name: string, callback: AsyncCallback&lt;Preferences&gt;): void

Obtains a **Preferences** instance with the parameters set by **name**. This API uses an asynchronous callback to return the result.

After the first application launch calls this API to obtain a **Preferences** instance, the instance is cached. Subsequent calls do not read from the persistent file again but directly obtain the **Preferences** instance from the cache.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                                            | Mandatory| Description                                                        |
| -------- | ------------------------------------------------ | ---- | ------------------------------------------------------------ |
| context  | Context            | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).                                                |
| name     | string                                           | Yes   | Name of the **Preferences** instance. The name length must be greater than 0 and less than or equal to 255 bytes. The name cannot contain '/' and cannot end with '/'. |
| callback | AsyncCallback&lt;[Preferences](#preferences)&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and the **Preferences** instance obtained is returned. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();
let dataPreferences: preferences.Preferences | null = null;

preferences.getPreferences(context, 'myStore', (err: BusinessError, val: preferences.Preferences) => {
  if (err) {
    console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
    return;
  }
  dataPreferences = val;
  console.info("Succeeded in getting preferences.");
})
```

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let dataPreferences: preferences.Preferences | null = null;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    preferences.getPreferences(this.context, 'myStore', (err: BusinessError, val: preferences.Preferences) => {
      if (err) {
        console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
        return;
      }
      dataPreferences = val;
      console.info("Succeeded in getting preferences.");
    })
  }
}
```

## preferences.getPreferences

getPreferences(context: Context, name: string): Promise&lt;Preferences&gt;

Obtains a **Preferences** instance with the parameters set by **name**. This API uses a promise to return the result.

After the first application launch calls this API to obtain a **Preferences** instance, the instance is cached. Subsequent calls do not read from the persistent file again but directly obtain the **Preferences** instance from the cache.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type                                 | Mandatory| Description                   |
| ------- | ------------------------------------- | ---- | ----------------------- |
| context | Context | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).           |
| name    | string                                | Yes   | Name of the **Preferences** instance. The name length must be greater than 0 and less than or equal to 255 bytes. The name cannot contain '/' and cannot end with '/'. |

**Return value**

| Type                                      | Description                              |
| ------------------------------------------ | ---------------------------------- |
| Promise&lt;[Preferences](#preferences)&gt; | Promise used to return the **Preferences** instance obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

let dataPreferences: preferences.Preferences | null = null;
let sp = preferences.getPreferences(context, 'myStore');
sp.then((object: preferences.Preferences) => {
  dataPreferences = object;
  console.info("Succeeded in getting preferences.");
}).catch((err: BusinessError) => {
  console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
})
```

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let dataPreferences: preferences.Preferences | null = null;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let sp = preferences.getPreferences(this.context, 'myStore');
    sp.then((object: preferences.Preferences) => {
      dataPreferences = object;
      console.info("Succeeded in getting preferences.");
    }).catch((err: BusinessError) => {
      console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
    })
  }
}
```

## preferences.getPreferences<sup>10+</sup>

getPreferences(context: Context, options: Options, callback: AsyncCallback&lt;Preferences&gt;): void

Obtains a **Preferences** instance with the parameters set by **Options**. This API uses an asynchronous callback to return the result.

After the first application launch calls this API to obtain a **Preferences** instance, the instance is cached. Subsequent calls do not read from the persistent file again but directly obtain the **Preferences** instance from the cache.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                                         | Mandatory| Description                                                                                                                                                                          |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| context  | Context                                       | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| options  | [Options](#options10)                              | Yes   | Configuration options related to the **Preferences** instance. The **name** field is mandatory. The name length must be greater than 0 and less than or equal to 255 bytes. The name cannot contain '/' or end with '/'. **dataGroupId** and **storageType** are optional fields.                                                                                                                                              |
| callback | AsyncCallback&lt;[Preferences](#preferences)&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and the **Preferences** instance obtained is returned. Otherwise, **err** is an error object.                                                                                   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error. <br>Applicable versions: 11+                  |
| 15501001 | The operations is supported in stage mode only. |
| 15501002 | Invalid dataGroupId.     |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();
let dataPreferences: preferences.Preferences | null = null;

let options: preferences.Options = { name: 'myStore' };
preferences.getPreferences(context, options, (err: BusinessError, val: preferences.Preferences) => {
  if (err) {
    console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
    return;
  }
  dataPreferences = val;
  console.info("Succeeded in getting preferences.");
})
```


Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let dataPreferences: preferences.Preferences | null = null;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    preferences.getPreferences(this.context, options, (err: BusinessError, val: preferences.Preferences) => {
      if (err) {
        console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
        return;
      }
      dataPreferences = val;
      console.info("Succeeded in getting preferences.");
    })
  }
}
```

## preferences.getPreferences<sup>10+</sup>

getPreferences(context: Context, options: Options): Promise&lt;Preferences&gt;

Obtains a **Preferences** instance with the parameters set by **Options**. This API uses a promise to return the result.

After the first application launch calls this API to obtain a **Preferences** instance, the instance is cached. Subsequent calls do not read from the persistent file again but directly obtain the **Preferences** instance from the cache.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type            | Mandatory| Description                                                                                                                                                                          |
| ------- | ---------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| context | Context          | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| options | [Options](#options10) | Yes  | Configuration options of the **Preferences** instance.                                                                                                                                             |

**Return value**

| Type                                   | Description                              |
| --------------------------------------- | ---------------------------------- |
| Promise&lt;[Preferences](#preferences)&gt; | Promise used to return the **Preferences** instance obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |
| 15501001 | The operations is supported in stage mode only. |
| 15501002 | Invalid dataGroupId.     |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

let dataPreferences: preferences.Preferences | null = null;
let options: preferences.Options = { name: 'myStore' };
let sp = preferences.getPreferences(context, options);
sp.then((object: preferences.Preferences) => {
  dataPreferences = object;
  console.info("Succeeded in getting preferences.");
}).catch((err: BusinessError) => {
  console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
})
```

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let dataPreferences: preferences.Preferences | null = null;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    let sp = preferences.getPreferences(this.context, options);
    sp.then((object: preferences.Preferences) => {
      dataPreferences = object;
      console.info("Succeeded in getting preferences.");
    }).catch((err: BusinessError) => {
      console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
    })
  }
}
```

## preferences.getPreferencesSync<sup>10+</sup>

getPreferencesSync(context: Context, options: Options): Preferences

Obtains a **Preferences** instance. This API returns the result synchronously.

After the first application launch calls this API to obtain a **Preferences** instance, the instance is cached. Subsequent calls do not read from the persistent file again but directly obtain the **Preferences** instance from the cache.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type                 | Mandatory| Description                                                        |
| ------- | --------------------- | ---- | ------------------------------------------------------------ |
| context | Context               | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| options | [Options](#options10) | Yes  | Configuration options of the **Preferences** instance.                           |

**Return value**

| Type                       | Description                 |
| --------------------------- | --------------------- |
| [Preferences](#preferences) | **Preferences** instance obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |
| 15501001 | The operations is supported in stage mode only.   |
| 15501002 | Invalid dataGroupId. |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';

let context = featureAbility.getContext();
let dataPreferences: preferences.Preferences | null = null;

let options: preferences.Options = { name: 'myStore' };
dataPreferences = preferences.getPreferencesSync(context, options);
```

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

let dataPreferences: preferences.Preferences | null = null;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    dataPreferences = preferences.getPreferencesSync(this.context, options);
  }
}
```

## preferences.deletePreferences

deletePreferences(context: Context, name: string, callback: AsyncCallback&lt;void&gt;): void

Deletes the specified **Preferences** instance from the cache. If the **Preferences** instance has a corresponding persistent file, the persistent file is also deleted. This API uses **name** as the parameter and an asynchronous callback to return the result.

Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner.

This API cannot be called concurrently with other **preferences** APIs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                                 | Mandatory| Description                                                |
| -------- | ------------------------------------- | ---- | ---------------------------------------------------- |
| context  | Context | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).                                        |
| name     | string                                | Yes   | Name of the **Preferences** instance. The name length must be greater than 0 and less than or equal to 255 bytes. The name cannot contain '/' and cannot end with '/'. |
| callback | AsyncCallback&lt;void&gt;             | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |
| 15500010 | Failed to delete the user preferences persistence file. |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
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

```ts
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

## preferences.deletePreferences

deletePreferences(context: Context, name: string): Promise&lt;void&gt;

Deletes the specified **Preferences** instance from the cache. If the **Preferences** instance has a corresponding persistent file, the persistent file is also deleted. This API uses **name** as the parameter and a promise to return the result.

Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner.

This API cannot be called concurrently with other **preferences** APIs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type                                 | Mandatory| Description                   |
| ------- | ------------------------------------- | ---- | ----------------------- |
| context | Context | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).           |
| name    | string                                | Yes   | Name of the **Preferences** instance. The name length must be greater than 0 and less than or equal to 255 bytes. The name cannot contain '/' and cannot end with '/'. |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |
| 15500010 | Failed to delete the user preferences persistence file. |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
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

```ts
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

## preferences.deletePreferences<sup>10+</sup>

deletePreferences(context: Context, options: Options, callback: AsyncCallback&lt;void&gt;): void

Deletes the specified **Preferences** instance from the cache. If the **Preferences** instance has a corresponding persistent file, the persistent file is also deleted. This API uses **Options** as the parameter and an asynchronous callback to return the result.

Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner.

This API cannot be called concurrently with other **preferences** APIs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                                                                                                                                                          |
| -------- | ------------------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| context  | Context                   | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| options  | [Options](#options10)          | Yes  | Configuration options of the **Preferences** instance.                                                                                                                                             |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.                                                                                                                          |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |
| 15500010 | Failed to delete the user preferences persistence file. |
| 15501001 | The operations is supported in stage mode only. |
| 15501002 | Invalid dataGroupId. |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
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

```ts
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


## preferences.deletePreferences<sup>10+</sup>

deletePreferences(context: Context, options: Options): Promise&lt;void&gt;

Deletes the specified **Preferences** instance from the cache. If the **Preferences** instance has a corresponding persistent file, the persistent file is also deleted. This API uses **Options** as the parameter and a promise to return the result.

Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner.

This API cannot be called concurrently with other **preferences** APIs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type            | Mandatory| Description                                                                                                                                                                          |
| ------- | ---------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| context | Context          | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| options | [Options](#options10) | Yes  | Configuration options of the **Preferences** instance.                                                                                                                                             |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |
| 15500010 | Failed to delete the user preferences persistence file. |
| 15501001 | The operations is supported in stage mode only. |
| 15501002 | Invalid dataGroupId. |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
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

```ts
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


## preferences.removePreferencesFromCache

removePreferencesFromCache(context: Context, name: string, callback: AsyncCallback&lt;void&gt;): void

Removes the specified **Preferences** instance from the cache. This API uses **name** as the parameter and an asynchronous callback to return the result.

After an application calls [getPreferences](#preferencesgetpreferences) for the first time to obtain a **Preferences** instance, the obtained **Preferences** instance is cached. When the application calls [getPreferences](#preferencesgetpreferences) again, the **Preferences** instance will be read from the cache instead of from the persistent file. After this API is called to remove the instance from the cache, calling **getPreferences** again will read data from the persistent file and create a **Preferences** instance.

Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner.

If [GSKV](../../database/data-persistence-by-preferences.md#gskv) is used, you are advised to manually call this API once when the process exits. This operation writes the data cache page to the disk, which can reduce the time required for calling the **getPreferences** API next time. Otherwise, data restoration is required at the bottom layer when the **getPreferences** API is called. The time required for data restoration depends on the number of data cache pages that are not written to the disk.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                                 | Mandatory| Description                                                |
| -------- | ------------------------------------- | ---- | ---------------------------------------------------- |
| context  | Context | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).                                        |
| name     | string                                | Yes   | Name of the **Preferences** instance. The name length must be greater than 0 and less than or equal to 255 bytes. The name cannot contain '/' and cannot end with '/'. |
| callback | AsyncCallback&lt;void&gt;             | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();
preferences.removePreferencesFromCache(context, 'myStore', (err: BusinessError) => {
  if (err) {
    console.error("Failed to remove preferences. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in removing preferences.");
})
```

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    preferences.removePreferencesFromCache(this.context, 'myStore', (err: BusinessError) => {
      if (err) {
        console.error("Failed to remove preferences. code =" + err.code + ", message = " + err.message);
        return;
      }
      console.info("Succeeded in removing preferences.");
    })
  }
}
```

## preferences.removePreferencesFromCache

removePreferencesFromCache(context: Context, name: string): Promise&lt;void&gt;

Removes the specified **Preferences** instance from the cache. This API uses **name** as the parameter and a promise to return the result.

After an application calls [getPreferences](#preferencesgetpreferences) for the first time to obtain a **Preferences** instance, the obtained **Preferences** instance is cached. When the application calls [getPreferences](#preferencesgetpreferences) again, the **Preferences** instance will be read from the cache instead of from the persistent file. After this API is called to remove the instance from the cache, calling **getPreferences** again will read data from the persistent file and create a **Preferences** instance.

Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner.

If [GSKV](../../database/data-persistence-by-preferences.md#gskv) is used, you are advised to manually call this API once when the process exits. This operation writes the data cache page to the disk, which can reduce the time required for calling the **getPreferences** API next time. Otherwise, data restoration is required at the bottom layer when the **getPreferences** API is called. The time required for data restoration depends on the number of data cache pages that are not written to the disk.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type                                 | Mandatory| Description                   |
| ------- | ------------------------------------- | ---- | ----------------------- |
| context | Context | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).           |
| name    | string                                | Yes   | Name of the **Preferences** instance. The name length must be greater than 0 and less than or equal to 255 bytes. The name cannot contain '/' and cannot end with '/'. |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();
let sp = preferences.removePreferencesFromCache(context, 'myStore');
sp.then(() => {
  console.info("Succeeded in removing preferences.");
}).catch((err: BusinessError) => {
  console.error("Failed to remove preferences. code =" + err.code + ", message = " + err.message);
})
```

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let sp = preferences.removePreferencesFromCache(this.context, 'myStore');
    sp.then(() => {
      console.info("Succeeded in removing preferences.");
    }).catch((err: BusinessError) => {
      console.error("Failed to remove preferences. code =" + err.code + ", message = " + err.message);
    })
  }
}
```

## preferences.removePreferencesFromCacheSync<sup>10+</sup>

removePreferencesFromCacheSync(context: Context, name: string): void

Removes the specified **Preferences** instance from the cache. This API uses **name** as the parameter and is a synchronous API.

After an application calls [getPreferences](#preferencesgetpreferences) for the first time to obtain a **Preferences** instance, the obtained **Preferences** instance is cached. When the application calls [getPreferences](#preferencesgetpreferences) again, the **Preferences** instance will be read from the cache instead of from the persistent file. After this API is called to remove the instance from the cache, calling **getPreferences** again will read data from the persistent file and create a **Preferences** instance.

Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim it in a unified manner.

If [GSKV](../../database/data-persistence-by-preferences.md#gskv) is used, you are advised to manually call this API once when the process exits. This operation writes the data cache page to the disk, which can reduce the time required for calling the **getPreferences** API next time. Otherwise, data restoration is required at the bottom layer when the **getPreferences** API is called. The time required for data restoration depends on the number of data cache pages that are not written to the disk.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type                                 | Mandatory| Description                   |
| ------- | ------------------------------------- | ---- | ----------------------- |
| context | Context | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).           |
| name    | string                                | Yes   | Name of the **Preferences** instance. The name length must be greater than 0 and less than or equal to 255 bytes. The name cannot contain '/' and cannot end with '/'. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';

let context = featureAbility.getContext();
preferences.removePreferencesFromCacheSync(context, 'myStore');
```

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    preferences.removePreferencesFromCacheSync(this.context, 'myStore');
  }
}
```

## preferences.removePreferencesFromCache<sup>10+</sup>

removePreferencesFromCache(context: Context, options: Options, callback: AsyncCallback&lt;void&gt;): void

Removes the specified **Preferences** instance from the cache. This API uses **Options** as the parameter and an asynchronous callback to return the result.

After an application calls [getPreferences](#preferencesgetpreferences) for the first time to obtain a **Preferences** instance, the obtained **Preferences** instance is cached. When the application calls [getPreferences](#preferencesgetpreferences) again, the **Preferences** instance will be read from the cache instead of from the persistent file. After this API is called to remove the instance from the cache, calling **getPreferences** again will read data from the persistent file and create a **Preferences** instance.

Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner.

If [GSKV](../../database/data-persistence-by-preferences.md#gskv) is used, you are advised to manually call this API once when the process exits. This operation writes the data cache pages to the disk, which can reduce the time required for calling the **getPreferences** API next time. Otherwise, data restoration is required at the bottom layer when the **getPreferences** API is called. The time required for data restoration depends on the number of data cache pages that are not written to the disk.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                                                                                                                                                          |
| -------- | ------------------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| context  | Context                   | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| options  | [Options](#options10)          | Yes  | Configuration options of the **Preferences** instance.                                                                                                                                             |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.                                                                                                                          |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |
| 15501001 | The operations is supported in stage mode only. |
| 15501002 | Invalid dataGroupId.     |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();
let options: preferences.Options = { name: 'myStore' };
preferences.removePreferencesFromCache(context, options, (err: BusinessError) => {
  if (err) {
    console.error("Failed to remove preferences. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in removing preferences.");
})
```

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    preferences.removePreferencesFromCache(this.context, options, (err: BusinessError) => {
      if (err) {
        console.error("Failed to remove preferences. code =" + err.code + ", message = " + err.message);
        return;
      }
      console.info("Succeeded in removing preferences.");
    })
  }
}
```

## preferences.removePreferencesFromCache<sup>10+</sup>

removePreferencesFromCache(context: Context, options: Options): Promise&lt;void&gt;

Removes the specified **Preferences** instance from the cache. This API uses **Options** as the parameter and a promise to return the result.

After an application calls [getPreferences](#preferencesgetpreferences) for the first time to obtain a **Preferences** instance, the obtained **Preferences** instance is cached. When the application calls [getPreferences](#preferencesgetpreferences) again, the **Preferences** instance will be read from the cache instead of from the persistent file. After this API is called to remove the instance from the cache, calling **getPreferences** again will read data from the persistent file and create a **Preferences** instance.

Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim it in a unified manner.

If [GSKV](../../database/data-persistence-by-preferences.md#gskv) is used, you are advised to manually call this API once when the process exits. This operation writes the data cache page to the disk, which can reduce the time required for calling the **getPreferences** API next time. Otherwise, data restoration is required at the bottom layer when the **getPreferences** API is called. The time required for data restoration depends on the number of data cache pages that are not written to the disk.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type            | Mandatory| Description                                                                                                                                                                          |
| ------- | ---------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| context | Context          | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| options | [Options](#options10) | Yes  | Configuration options of the **Preferences** instance.                                                                                                                                             |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |
| 15501001 | The operations is supported in stage mode only. |
| 15501002 | Invalid dataGroupId.     |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();
let options: preferences.Options = { name: 'myStore' };
let sp = preferences.removePreferencesFromCache(context, options);
sp.then(() => {
  console.info("Succeeded in removing preferences.");
}).catch((err: BusinessError) => {
  console.error("Failed to remove preferences. code =" + err.code + ", message = " + err.message);
})
```

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    let sp = preferences.removePreferencesFromCache(this.context, options);
    sp.then(() => {
      console.info("Succeeded in removing preferences.");
    }).catch((err: BusinessError) => {
      console.error("Failed to remove preferences. code =" + err.code + ", message = " + err.message);
    })
  }
}
```

## preferences.removePreferencesFromCacheSync<sup>10+</sup>

removePreferencesFromCacheSync(context: Context, options: Options): void

Removes the specified **Preferences** instance from the cache. This API uses **Options** to set parameters and is a synchronous API.

After an application calls [getPreferences](#preferencesgetpreferences) for the first time to obtain a **Preferences** instance, the obtained **Preferences** instance is cached. When the application calls [getPreferences](#preferencesgetpreferences) again, the **Preferences** instance will be read from the cache instead of from the persistent file. After this API is called to remove the instance from the cache, calling **getPreferences** again will read data from the persistent file and create a **Preferences** instance.

Avoid using a removed **Preferences** instance to perform data operations, which may cause data inconsistency. Instead, set the removed **Preferences** instance to null. The system will reclaim them in a unified manner.

If [GSKV](../../database/data-persistence-by-preferences.md#gskv) is used, you are advised to manually call this API once when the process exits. This operation writes the data cache page to the disk, which can reduce the time required for calling the **getPreferences** API next time. Otherwise, data restoration is required at the bottom layer when the **getPreferences** API is called. The time required for data restoration depends on the number of data cache pages that are not written to the disk.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type                 | Mandatory| Description                                                        |
| ------- | --------------------- | ---- | ------------------------------------------------------------ |
| context | Context               | Yes  | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| options | [Options](#options10) | Yes  | Configuration options of the **Preferences** instance.                           |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |
| 15501001 | The operations is supported in stage mode only.   |
| 15501002 | Invalid dataGroupId. |

**Example**

FA model:

<!--code_no_check_fa-->
```ts
// Obtain the context.
import { featureAbility } from '@kit.AbilityKit';

let context = featureAbility.getContext();
let options: preferences.Options = { name: 'myStore' };
preferences.removePreferencesFromCacheSync(context, options);
```

Stage model:

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    preferences.removePreferencesFromCacheSync(this.context, options);
  }
}
```

## StorageType<sup>18+</sup>
Enumerates the storage types of preferences.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

| Name| Value  | Description|
| ---- | ---- | ---- |
| XML |  0    | [XML storage mode](../../database/data-persistence-by-preferences.md#xml), which is the default storage mode of **Preferences**.<br>**Features:** Data is stored in XML format. Operations on data are performed in memory, and the [flush](#flush) API must be called to persist the data to disk.     |
| GSKV |  1    |Indicates the [GSKV storage mode](../../database/data-persistence-by-preferences.md#gskv).<br>**Features:** Data is stored in GSKV database mode. Operations on data are persisted to disk in real time, and there is no need to call the [flush](#flush) API to persist the data to disk.      |


> **NOTE**
>   - Before selecting a storage mode, you are advised to call [isStorageTypeSupported](#preferencesisstoragetypesupported18) to check whether the current platform supports the corresponding storage mode.
>   - After an instance is obtained through [preferences.getPreferences](#preferencesgetpreferences) in a certain mode, switching the mode midway is not allowed.
>   - Preferences does not support data migration between different modes. To switch data from one mode to another, migrate the data by reading from and writing to the preferences.
>   - To change the storage path of preferences, do not move or overwrite files. Instead, migrate the data by reading from and writing to the preferences.

## preferences.isStorageTypeSupported<sup>18+</sup>
isStorageTypeSupported(type: StorageType): boolean

Checks whether the specified storage type is supported. This API returns the result synchronously. If the storage type is supported, **true** is returned. Otherwise, **false** is returned.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type                 | Mandatory| Description                                                        |
| ------- | --------------------- | ---- | ------------------------------------------------------------ |
| type | [StorageType](#storagetype18)               | Yes  | Storage type to check.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| boolean | Returns **true** if the storage type is supported; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes: Incorrect parameter types. |


**Example**

```ts
let xmlType = preferences.StorageType.XML;
let gskvType = preferences.StorageType.GSKV;
let isXmlSupported = preferences.isStorageTypeSupported(xmlType);
let isGskvSupported = preferences.isStorageTypeSupported(gskvType);
console.info("Is xml supported in current platform: " + isXmlSupported);
console.info("Is gskv supported in current platform: " + isGskvSupported);
```

## Options<sup>10+</sup>

Represents the configuration of a **Preferences** instance.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

| Name       | Type  | Read-Only| Optional| Description                                                        |
| ----------- | ------ | ---- | ----| ------------------------------------------------------------ |
| name        | string | No  | No | Name of the **Preferences** instance. The name length must be greater than 0 and less than or equal to 255 bytes. The name cannot contain '/' and cannot end with '/'. <br>**Atomic service API:** Since API version 11, this parameter is supported in atomic services.                                    |
| dataGroupId | string \| null \| undefined | No  | Yes | Application group ID. <!--RP1-->Currently, specifying **dataGroupId** to create a Preferences instance in the corresponding shared sandbox path is not supported.<!--RP1End--><br>This is an optional parameter. It specifies to create a **Preferences** instance in the sandbox path corresponding to this **dataGroupId**. If this parameter is not specified, a **Preferences** instance is created in the application sandbox directory by default.<br> **Model constraint:** This attribute is available only in the stage model.<br>**Atomic service API:** Since API version 11, this parameter is supported in atomic services. |
| storageType<sup>18+</sup> | [StorageType](#storagetype18) \| null \| undefined | No | Yes | Storage mode. This is an optional parameter. It indicates the storage mode to be used by the current **Preferences** instance. If this parameter is not specified, the XML storage mode is used by default. After a **Preferences** instance is created with a storage mode, switching the storage mode midway is not supported. <br>**Atomic service API:** Since API version 18, this parameter is supported in atomic services. |


## Preferences

Provides APIs for obtaining and modifying the stored data.

Before calling any API of **Preferences**, you must obtain a **Preferences** instance by using [preferences.getPreferences](#preferencesgetpreferences).


### get

get(key: string, defValue: ValueType, callback: AsyncCallback&lt;ValueType&gt;): void

Obtains the value of a key from this **Preferences** instance. This API uses an asynchronous callback to return the result. If the value is null or is not of the default value type, **defValue** is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                                        | Mandatory| Description              |
| -------- | -------------------------------------------- | ---- |---------------------------|
| key      | string                                       | Yes  | Key to be obtained. The value cannot be empty. For details about its maximum length, see [MAX_KEY_LENGTH](#constants).  |
| defValue | [ValueType](#valuetype)                      | Yes  | Default value to be returned.|
| callback | AsyncCallback&lt;[ValueType](#valuetype)&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the value obtained. Otherwise, **err** is an error object.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

dataPreferences.get('startup', 'default', (err: BusinessError, val: preferences.ValueType) => {
  if (err) {
    console.error("Failed to get value of 'startup'. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in getting value of 'startup'. val: " + val);
})
```

### get

get(key: string, defValue: ValueType): Promise&lt;ValueType&gt;

Obtains the value of a key from this **Preferences** instance. This API uses a promise to return the result. If the value is null or is not of the default value type, **defValue** is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

 **Parameters**

| Name  | Type                   | Mandatory| Description |
| -------- | ----------------------- | ---- |--------|
| key      | string                  | Yes  | Key to be obtained. The value cannot be empty. For details about its maximum length, see [MAX_KEY_LENGTH](#constants). |
| defValue | [ValueType](#valuetype) | Yes  | Default value to be returned.|

**Return value**

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| Promise<[ValueType](#valuetype)&gt; | Promise used to return the value obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let data = dataPreferences.get('startup', 'default');
data.then((data: preferences.ValueType) => {
  console.info("Succeeded in getting value of 'startup'. Data: " + data);
}).catch((err: BusinessError) => {
  console.error("Failed to get value of 'startup'. code =" + err.code + ", message = " + err.message);
})
```

### getSync<sup>10+</sup>

getSync(key: string, defValue: ValueType): ValueType

Obtains the value of a key from this **Preferences** instance. This API returns the result synchronously. If the value is null or is not of the default value type, **defValue** is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                   | Mandatory| Description           |
| -------- | ----------------------- | ---- |---------------------|
| key      | string                  | Yes  | Key to be obtained. The value cannot be empty. For details about its maximum length, see [MAX_KEY_LENGTH](#constants). |
| defValue | [ValueType](#valuetype) | Yes  | Default value to be returned.|

**Return value**

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| [ValueType](#valuetype) | Returns the value obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
let value: preferences.ValueType = dataPreferences.getSync('startup', 'default');
```

### getAll

getAll(callback: AsyncCallback&lt;Object&gt;): void

Obtains all KV pairs from a **Preferences** instance. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Object&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **value** provides all KV pairs obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Mandatory parameters are left unspecified.|
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// There is no Object.keys in ArkTS, and the for..in... syntax cannot be used.
// If an error is reported, extract this API to a .ts file and expose it. Then import the API to the .ets file when required.
function getObjKeys(obj: Object): string[] {
  let keys = Object.keys(obj);
  return keys;
}

dataPreferences.getAll((err: BusinessError, value: Object) => {
  if (err) {
    console.error("Failed to get all key-values. code =" + err.code + ", message = " + err.message);
    return;
  }
  let allKeys = getObjKeys(value);
  console.info("getAll keys = " + allKeys);
  console.info("getAll object = " + JSON.stringify(value));
})
```


### getAll

getAll(): Promise&lt;Object&gt;

Obtains all key-value data in the cached **Preferences** instance. This API uses a promise to return the result asynchronously.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Return value**

| Type                 | Description                                       |
| --------------------- | ------------------------------------------- |
| Promise&lt;Object&gt; | Promise used to return the KV pairs obtained.|

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// There is no Object.keys in ArkTS, and the for..in... syntax cannot be used.
// If an error is reported, extract this API to a .ts file and expose it. Then import the API to the .ets file when required.
function getObjKeys(obj: Object): string[] {
  let keys = Object.keys(obj);
  return keys;
}

let allData = dataPreferences.getAll();
allData.then((value: Object) => {
  let allKeys = getObjKeys(value);
  console.info('getAll keys = ' + allKeys);
  console.info("getAll object = " + JSON.stringify(value));
}).catch((err: BusinessError) => {
  console.error("Failed to get all key-values. code =" + err.code + ", message = " + err.message);
})
```

### getAllSync<sup>10+</sup>

getAllSync(): Object

Obtains all KV pairs from this **Preferences** instance. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Return value**

| Type                 | Description                                       |
| --------------------- | ------------------------------------------- |
| Object | Returns all KV pairs obtained.|

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
// There is no Object.keys in ArkTS, and the for..in... syntax cannot be used.
// If an error is reported, extract this API to a .ts file and expose it. Then import the API to the .ets file when required.
function getObjKeys(obj: Object): string[] {
  let keys = Object.keys(obj);
  return keys;
}

let value = dataPreferences.getAllSync();
let allKeys = getObjKeys(value);
console.info('getAll keys = ' + allKeys);
console.info("getAll object = " + JSON.stringify(value));
```

### put

put(key: string, value: ValueType, callback: AsyncCallback&lt;void&gt;): void

Writes data to this **Preferences** instance. This API uses an asynchronous callback to return the result. You can use [flush](#flush) to persist the **Preferences** instance.

  > **NOTE**
  >
  > If the value contains a string that is not in UTF-8 format, store it in a Uint8Array. Otherwise, the persistent file may be damaged due to format errors.
  >
  > If the key already exists, **put()** overwrites the value. You can use **hasSync()** to check whether the KV pair exists.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                      |
| -------- | ------------------------- | ---- |-------------------------|
| key      | string                    | Yes  | Key to be modified. The value cannot be empty. For details about its maximum length, see [MAX_KEY_LENGTH](#constants).|
| value    | [ValueType](#valuetype)   | Yes  | Value to write.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

dataPreferences.put('startup', 'auto', (err: BusinessError) => {
  if (err) {
    console.error("Failed to put value of 'startup'. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in putting value of 'startup'.");
})
```


### put

put(key: string, value: ValueType): Promise&lt;void&gt;

Writes data to this **Preferences** instance. This API uses a promise to return the result. You can use [flush](#flush) to persist the **Preferences** instance.

  > **NOTE**
  >
  > If the value contains a string that is not in UTF-8 format, store it in a Uint8Array. Otherwise, the persistent file may be damaged due to format errors.
  >
  > If the key already exists, **put()** overwrites the value. You can use **hasSync()** to check whether the KV pair exists.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type                   | Mandatory| Description                        |
| ------ | ----------------------- | ---- |--------------------------|
| key    | string                  | Yes  | Key to be modified. The value cannot be empty. For details about its maximum length, see [MAX_KEY_LENGTH](#constants). |
| value  | [ValueType](#valuetype) | Yes  | Value to write.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let putStartupPref = dataPreferences.put('startup', 'auto');
putStartupPref.then(() => {
  console.info("Succeeded in putting value of 'startup'.");
}).catch((err: BusinessError) => {
  console.error("Failed to put value of 'startup'. code =" + err.code + ", message = " + err.message);
})
```


### putSync<sup>10+</sup>

putSync(key: string, value: ValueType): void

Writes data to this **Preferences** instance. This API returns the result synchronously. You can use [flush](#flush) to persist the **Preferences** instance.

  > **NOTE**
  >
  > If the value contains a string that is not in UTF-8 format, store it in a Uint8Array. Otherwise, the persistent file may be damaged due to format errors.
  >
  > If the key already exists, **putSync()** overwrites the value. You can use **hasSync()** to check whether the KV pair exists.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type                   | Mandatory| Description                                                        |
| ------ | ----------------------- | ---- | ------------------------ |
| key    | string                  | Yes  | Key to be modified. The value cannot be empty. For details about its maximum length, see [MAX_KEY_LENGTH](#constants).|
| value  | [ValueType](#valuetype) | Yes  | Value to write.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
dataPreferences.putSync('startup', 'auto');
```


### has

has(key: string, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether this **Preferences** instance contains the KV pair of the given key. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                        | Mandatory| Description                                                        |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| key      | string                       | Yes  | Name of the storage key to check. It cannot be empty, and its maximum length is limited by [MAX_KEY_LENGTH](#constants).                              |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback function. Returns whether the **Preferences** instance contains the key-value pair of the given key. The value **true** indicates that the key exists, and **false** indicates that it does not. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

dataPreferences.has('startup', (err: BusinessError, val: boolean) => {
  if (err) {
    console.error("Failed to check the key 'startup'. code =" + err.code + ", message = " + err.message);
    return;
  }
  if (val) {
    console.info("The key 'startup' is contained.");
  } else {
    console.info("The key 'startup' is not contained.");
  }
})
```


### has

has(key: string): Promise&lt;boolean&gt;

Checks whether this **Preferences** instance contains the KV pair of the given key. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | Yes   | Storage key name to check. It cannot be empty. The maximum length is limited by [MAX_KEY_LENGTH](#constants). |

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise object used to return whether the **Preferences** instance contains the key-value pair of the given key. The value **true** indicates that it exists, and **false** indicates that it does not exist. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let isStartupSet = dataPreferences.has('startup');
isStartupSet.then((val: boolean) => {
  if (val) {
    console.info("The key 'startup' is contained.");
  } else {
    console.info("The key 'startup' does not contain.");
  }
}).catch((err: BusinessError) => {
  console.error("Failed to check the key 'startup'. code =" + err.code + ", message = " + err.message);
})
```


### hasSync<sup>10+</sup>

hasSync(key: string): boolean

Checks whether this **Preferences** instance contains the KV pair of the given key. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | Yes   | Name of the storage key to check. It cannot be empty and its maximum length is limited by [MAX_KEY_LENGTH](#constants). |

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| boolean | Whether the **Preferences** instance contains the key-value pair with the given key. **true** indicates that it exists, and **false** indicates that it does not. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
let isExist: boolean = dataPreferences.hasSync('startup');
if (isExist) {
  console.info("The key 'startup' is contained.");
} else {
  console.info("The key 'startup' does not contain.");
}
```


### delete

delete(key: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a KV pair from this **Preferences** instance. This API uses an asynchronous callback to return the result. You can use [flush](#flush) to persist the **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                                |
| -------- | ------------------------- | ---- | ---------------------------------------------------- |
| key      | string                    | Yes  | Key to be deleted. The value cannot be empty. For details about its maximum length, see [MAX_KEY_LENGTH](#constants).                     |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

dataPreferences.delete('startup', (err: BusinessError) => {
  if (err) {
    console.error("Failed to delete the key 'startup'. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in deleting the key 'startup'.");
})
```


### delete

delete(key: string): Promise&lt;void&gt;

Deletes a KV pair from this **Preferences** instance. This API uses a promise to return the result. You can use [flush](#flush) to persist the **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | Yes   | Key name to delete. It cannot be empty, and its maximum length is limited by [MAX_KEY_LENGTH](#constants). |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let deleteStartupPromise = dataPreferences.delete('startup');
deleteStartupPromise.then(() => {
  console.info("Succeeded in deleting the key 'startup'.");
}).catch((err: BusinessError) => {
  console.error("Failed to delete the key 'startup'. code =" + err.code +", message = " + err.message);
})
```


### deleteSync<sup>10+</sup>

deleteSync(key: string): void

Deletes a KV pair from this **Preferences** instance. This API returns the result synchronously. You can use [flush](#flush) to persist the **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | Yes   | Key of the stored data to delete. It cannot be empty and its length cannot exceed [MAX_KEY_LENGTH](#constants). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
dataPreferences.deleteSync('startup');
```


### flush

flush(callback: AsyncCallback&lt;void&gt;): void

Flushes the data in this **Preferences** instance to the persistent file. This API uses an asynchronous callback to return the result.

  > **NOTE**
  >
  > If no data is modified or the modified data is the same as the cached data, the persistent file will not be updated.
  >
  > This API is exclusively applicable to the XML storage and does not require invocation in the GSKV storage. When GSKV mode is selected, data operations via preferences are flushed to disk in real-time. For details about the preferences storage types, see [Storage Types](../../database/data-persistence-by-preferences.md#storage-types).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                                |
| -------- | ------------------------- | ---- | ---------------------------------------------------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Mandatory parameters are left unspecified.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

dataPreferences.flush((err: BusinessError) => {
  if (err) {
    console.error("Failed to flush. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in flushing.");
})
```


### flush

flush(): Promise&lt;void&gt;

Flushes the data in this **Preferences** instance to the persistent file. This API uses a promise to return the result.

  > **NOTE**
  >
  > If no data is modified or the modified data is the same as the cached data, the persistent file will not be updated.
  >
  > This API is exclusively applicable to the XML storage and does not require invocation in the GSKV storage. When GSKV mode is selected, data operations via preferences are flushed to disk in real-time. For details about the preferences storage types, see [Storage Types](../../database/data-persistence-by-preferences.md#storage-types).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let flushResult = dataPreferences.flush();
flushResult.then(() => {
  console.info("Succeeded in flushing.");
}).catch((err: BusinessError) => {
  console.error("Failed to flush. code =" + err.code + ", message = " + err.message);
})
```

### flushSync<sup>14+</sup>

flushSync(): void

Flushes the data in the cached **Preferences** instance to the persistent file.

  > **NOTE**
  >
  > If no data is modified or the modified data is the same as the cached data, the persistent file will not be updated.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error.                   |

**Example**

```ts
dataPreferences.flushSync();
```

### clear

clear(callback: AsyncCallback&lt;void&gt;): void

Clears this **Preferences** instance. This API uses an asynchronous callback to return the result. You can use [flush](#flush) to persist the **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                                |
| -------- | ------------------------- | ---- | ---------------------------------------------------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Mandatory parameters are left unspecified.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

dataPreferences.clear((err: BusinessError) =>{
  if (err) {
    console.error("Failed to clear. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in clearing.");
})
```


### clear

clear(): Promise&lt;void&gt;

Clears this **Preferences** instance. This API uses a promise to return the result. You can use [flush](#flush) to persist the **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let promise = dataPreferences.clear();
promise.then(() => {
  console.info("Succeeded in clearing.");
}).catch((err: BusinessError) => {
  console.error("Failed to clear. code =" + err.code + ", message = " + err.message);
})
```


### clearSync<sup>10+</sup>

clearSync(): void

Clears this **Preferences** instance. This API returns the result synchronously. You can use [flush](#flush) to persist the **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Example**

```ts
dataPreferences.clearSync();
```


### on('change')

on(type: 'change', callback: Callback&lt;string&gt;): void

Subscribes to data changes. When the value of a subscribed key changes and the [flush](#flush) method is executed, the callback is invoked.

> **NOTE**
> **Comparison of subscription methods:**
> - **on('change')**: Subscribes to changes of all keys. It is suitable for scenarios where global data change awareness is required.
> - **on('dataChange')**: Precisely subscribes to changes of specified keys. It is suitable for scenarios that focus on specific data and can return the specific value through the callback.
> - **on('multiProcessChange')**: Subscribes to multi-process data changes. It is suitable for scenarios where multiple processes share the same preferences file.
> 
> **Selection suggestions:** For single-process applications, **on('change')** or **on('dataChange')** is recommended. For multi-process data synchronization, use **on('multiProcessChange')**. When you need to precisely know the change of a specific key and obtain the new value, use **on('dataChange')**.

  > **NOTE**
  >
  > After [removePreferencesFromCache](#preferencesremovepreferencesfromcache) or [deletePreferences](#preferencesdeletepreferences) is called, the data change subscription will be automatically canceled. After [getPreferences](#preferencesgetpreferences) is called again, you need to subscribe to data changes again.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type    | Mandatory| Description                                    |
| -------- | -------- | ---- | ---------------------------------------- |
| type     | string   | Yes  | Event type. The value is **'change'**, which indicates data changes.|
| callback | Callback&lt;string&gt; | Yes | Callback function used to receive data change notifications. The callback parameter is a key string, indicating the name of the changed key. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
}
dataPreferences.on('change', observer);
dataPreferences.putSync('startup', 'manual');
dataPreferences.flush((err: BusinessError) => {
  if (err) {
    console.error("Failed to flush. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in flushing.");
})
```

### on('multiProcessChange')<sup>10+</sup>

on(type: 'multiProcessChange', callback: Callback&lt;string&gt;): void

Subscribes to data changes between processes. When multiple processes hold the same preference file, calling [flush](#flush) in any process (including the current process) will trigger the callback in this API.

This API is provided for applications that have applied for [dataGroupId](#options10). It is not recommended for applications that have not applied for it (data changes cannot be listened to). Multi-process operations may damage the persistent file and cause data loss.

  > **NOTE**
  >
  > The maximum number of multi-process data change subscriptions for the same persistent file in the current process is 50. Subscriptions beyond this limit will fail. You are advised to cancel the subscription in a timely manner after the callback is triggered.
  >
  > After [removePreferencesFromCache](#preferencesremovepreferencesfromcache) or [deletePreferences](#preferencesdeletepreferences) is called, the subscribed data change is automatically unsubscribed. After [getPreferences](#preferencesgetpreferences) is called again, you need to subscribe to the data change again.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type. The value is **'multiProcessChange'**, which indicates inter-process data changes.|
| callback | Callback&lt;string&gt; | Yes | Callback invoked when data changes between multiple processes. The callback parameter is the key string that has changed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                               |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                           |
| 15500019 | Failed to obtain the subscription service. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
}
dataPreferences.on('multiProcessChange', observer);
dataPreferences.putSync('startup', 'manual');
dataPreferences.flush((err: BusinessError) => {
  if (err) {
    console.error("Failed to flush. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in flushing.");
})
```

### on('dataChange')<sup>12+</sup>

on(type: 'dataChange', keys: Array&lt;string&gt;,  callback: Callback&lt;Record&lt;string, ValueType&gt;&gt;): void

Precisely subscribes to data changes. Only when the value of a subscribed key changes and the [flush](#flush) method is executed, the callback is invoked.

  > **NOTE**
  >
  > After [removePreferencesFromCache](#preferencesremovepreferencesfromcache) or [deletePreferences](#preferencesdeletepreferences) is called, the data change subscription will be automatically canceled. After [getPreferences](#preferencesgetpreferences) is called again, you need to subscribe to data changes again.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The value is **'dataChange'**, which indicates data changes.          |
| keys     | Array&lt;string&gt;                                          | Yes   | Set of keys to subscribe to.                                          |
| callback | Callback&lt;Record&lt;string, [ValueType](#valuetype)&gt;&gt; | Yes   | Callback invoked to return multiple key-value pairs, where the key is the subscribed key that has changed, of the string type, and the value is the changed data, of the [ValueType](#valuetype) type. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (data: Record<string, preferences.ValueType>) => {
  for (const keyValue of Object.entries(data)) {
    console.info(`observer : ${keyValue}`);
  }
  console.info("The observer called.");
}
let keys = ['name', 'age'];
dataPreferences.on('dataChange', keys, observer);
dataPreferences.putSync('name', 'xiaohong');
dataPreferences.putSync('weight', 125);
dataPreferences.flush((err: BusinessError) => {
  if (err) {
    console.error("Failed to flush. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in flushing.");
})
```

### off('change')

off(type: 'change', callback?: Callback&lt;string&gt;): void

Unsubscribes from data changes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type. The value is **'change'**, which indicates data changes.                    |
| callback | Callback&lt;string&gt; | No | Callback to unregister. If this parameter is not specified, all registered callbacks are unregistered; if specified, only the specified callback is unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
}
dataPreferences.on('change', observer);
dataPreferences.putSync('startup', 'auto');
dataPreferences.flush((err: BusinessError) => {
  if (err) {
    console.error("Failed to flush. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in flushing.");
})
dataPreferences.off('change', observer);
```

### off('multiProcessChange')<sup>10+</sup>

off(type: 'multiProcessChange', callback?: Callback&lt;string&gt;): void

Unsubscribes from inter-process data changes.

This API is provided for applications that have applied for [dataGroupId](#options10). It is not recommended for applications that have not applied for it (data changes cannot be listened to). Multi-process operations may damage the persistent file and cause data loss.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type. The value is **'multiProcessChange'**, which indicates inter-process data changes.|
| callback | Callback&lt;string&gt; | No | Callback for the event to cancel. If this parameter is not specified, all registered callbacks are canceled; if it is specified, only the specified callback is canceled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error. <br>Applicable versions: 11+                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
}
dataPreferences.on('multiProcessChange', observer);
dataPreferences.putSync('startup', 'auto');
dataPreferences.flush((err: BusinessError) => {
  if (err) {
    console.error("Failed to flush. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in flushing.");
})
dataPreferences.off('multiProcessChange', observer);
```
### off('dataChange')<sup>12+</sup>

off(type: 'dataChange', keys: Array&lt;string&gt;,  callback?: Callback&lt;Record&lt;string, ValueType&gt;&gt;): void

Unsubscribes from changes of specific data.

**Paired call**
- Used together with [on('dataChange')](#ondatachange12) to cancel the precise data change subscription.
- If you do not need to listen to data changes of a specific key, call off in a timely manner to unsubscribe.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The value is **'dataChange'**, which indicates data changes.          |
| keys     | Array&lt;string&gt;                                          | Yes   | Set of keys to unsubscribe from. When the **keys** array is empty, all keys are unsubscribed from. When the **keys** array is not empty, only the keys in the set are unsubscribed from. |
| callback | Callback&lt;Record&lt;string, [ValueType](#valuetype)&gt;&gt; | No   | Callback to unsubscribe. If this parameter is not specified, all registered callbacks are unsubscribed from. If this parameter is specified, only the specified callback is unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (data: Record<string, preferences.ValueType>) => {
  for (const keyValue of Object.entries(data)) {
    console.info(`observer : ${keyValue}`);
  }
  console.info("The observer called.");
}
let keys = ['name', 'age'];
dataPreferences.on('dataChange', keys, observer);
dataPreferences.putSync('name', 'xiaohong');
dataPreferences.putSync('weight', 125);
dataPreferences.flush((err: BusinessError) => {
  if (err) {
    console.error("Failed to flush. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in flushing.");
})
dataPreferences.off('dataChange', keys, observer);
```

## ValueType

type ValueType = number | string | boolean | Array\<number> | Array\<string> | Array\<boolean> | Uint8Array | object | bigint

Enumerates the value types.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

| Type                      | Description               |
|--------------------------|-------------------|
| number                   | The value is a number.        |
| string                   | The value is a string.       |
| boolean                  | The value is true or false.       |
| Array\<number>           | The value is an array of numbers.   |
| Array\<boolean>          | The value is a boolean array.   |
| Array\<string>           | The value is an array of strings.  |
| Uint8Array<sup>11+</sup> | The value is an array of 8-bit unsigned integers.|
| object<sup>12+</sup>     | The value is an object.|
| bigint<sup>12+</sup>     | The value is an integer in any format. |
