# @ohos.data.sendablePreferences (Shared User Preferences)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @cuile44-->
<!--Designer: @cuile44-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=baacd5e603827a8080bb1e15309bc06852b1fd80 translatedAt=2026-09-04T03:45:42.185Z pushedAt=2026-09-09T09:11:03.728Z -->


The **sendablePreferences** module provides APIs for processing data in the form of key-value (KV) pairs, including querying, modifying, and persisting KV pairs.

In the KV pairs, the key must be a string, and the value can be a number, a string, a Boolean value, a bigint, or a serializable object.

The persistent files of the shared user preferences are stored in the [preferencesDir](../../application-models/application-context-stage.md#obtaining-application-file-paths) directory. Before creating a preferences object, ensure that the **preferencesDir** path can be read and written. The [encryption level](../apis-ability-kit/js-apis-app-ability-contextConstant.md#areamode) of the persistent file directory determines the access to the files. For details, see [Application File Directory and Application File Path](../../file-management/app-sandbox-directory.md#application-file-directory-and-application-file-path).

Sendable preferences can be passed between concurrent ArkTS instances (including the main thread and TaskPool or Worker threads) by reference. It allows for higher performance than [user preferences](js-apis-data-preferences.md). For more information, see [Using Sendable Objects](../../arkts-utils/sendable-guide.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The shared user preferences are not thread-safe and may cause file damage and data loss when used in multi-process scenarios. Do not use it in multi-process scenarios.

## Modules to Import

```ts
import { sendablePreferences } from '@kit.ArkData';
```

## Constants

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

| Name            | Type     | Read-Only| Description                                   |
| ---------------- | -------- | ---- | --------------------------------------- |
| MAX_KEY_LENGTH   | number   | Yes  | Maximum length of a key, which is 1024 bytes.    |
| MAX_VALUE_LENGTH | number   | Yes  | Maximum length of a value, which is 16 MB.|

## sendablePreferences.getPreferences

getPreferences(context: Context, options: Options): Promise&lt;Preferences&gt;

Obtains a **Preferences** instance. This API uses a promise to return the result.

After the first application calls this interface to obtain a **Preferences** instance, this instance will be cached. Subsequent calls will not read from the persistent file again, but directly retrieve the **Preferences** instance from cache.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type            | Mandatory| Description                                                                                                                                                                          |
| ------- | ---------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)          | Yes  | Application context.|
| options | [Options](#options) | Yes | Configuration options related to the **Preferences** instance. The **name** field is mandatory. The name length must be greater than zero and less than or equal to 255 bytes. The name must not contain '/' and must not end with '/'. The **dataGroupId** field is optional. |

**Return value**

| Type                                   | Description                              |
| --------------------------------------- | ---------------------------------- |
| Promise&lt;[Preferences](#preferences)&gt; | Promise object that returns a **Preferences** instance. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error.                   |
| 15501001 | The operations is supported in stage mode only. |
| 15501002 | Invalid dataGroupId.     |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let preferences: sendablePreferences.Preferences;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: sendablePreferences.Options = { name: 'myStore' };
    let promise = sendablePreferences.getPreferences(this.context, options);
    promise.then((object: sendablePreferences.Preferences) => {
      preferences = object;
      console.info("Succeeded in getting preferences.");
    }).catch((err: BusinessError) => {
      console.error(`Failed to get preferences. code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## sendablePreferences.getPreferencesSync

getPreferencesSync(context: Context, options: Options): Preferences

Obtains a **Preferences** instance. This API returns the result synchronously.

After the first application calls this interface to obtain a **Preferences** instance, this instance will be cached. Subsequent calls will not read from the persistent file again, but directly retrieve the **Preferences** instance from cache.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type                 | Mandatory| Description                                                        |
| ------- | --------------------- | ---- | ------------------------------------------------------------ |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)               | Yes  | Application context.|
| options | [Options](#options) | Yes  | Configuration options of the **Preferences** instance.                           |

**Return value**

| Type                       | Description                 |
| --------------------------- | --------------------- |
| [Preferences](#preferences) | Returns a **Preferences** instance. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error.                   |
| 15501001 | The operations is supported in stage mode only.   |
| 15501002 | Invalid dataGroupId. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

let preferences: sendablePreferences.Preferences;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: sendablePreferences.Options = { name: 'myStore' };
    preferences = sendablePreferences.getPreferencesSync(this.context, options);
  }
}
```

## sendablePreferences.deletePreferences

deletePreferences(context: Context, options: Options): Promise&lt;void&gt;

Deletes a specified **Preferences** instance from the cache. If the **Preferences** instance has a corresponding persistent file, the persistent file is also deleted. This API uses a promise to return the result.

Avoid using a deleted **Preferences** instance to perform data operations, which may cause data inconsistency.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type            | Mandatory| Description                                                                        |
| ------- | ---------------- | ---- | ----------------------------------------------------------------------------|
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)          | Yes  | Application context.|
| options | [Options](#options) | Yes  | Instance-related configuration options for the **Preferences** instance. The name field is mandatory. The name length must be greater than zero and less than or equal to 255 bytes. The name must not contain '/' and must not end with '/'. dataGroupId is an optional field.                            |

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
| 15500000 | Inner error.                   |
| 15500010 | Failed to delete the user preferences persistence file. |
| 15501001 | The operations is supported in stage mode only. |
| 15501002 | Invalid dataGroupId. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: sendablePreferences.Options = { name: 'myStore' };
    let promise = sendablePreferences.deletePreferences(this.context, options);
    promise.then(() => {
      console.info("Succeeded in deleting preferences.");
    }).catch((err: BusinessError) => {
      console.error(`Failed to delete preferences. code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## sendablePreferences.removePreferencesFromCache

removePreferencesFromCache(context: Context, options: Options): Promise&lt;void&gt;

Removes a **Preferences** instance from the cache. This API uses a promise to return the result.

After an application calls [getPreferences](#sendablepreferencesgetpreferences) for the first time to obtain a **Preferences** instance, the obtained **Preferences** instance is cached. When the application calls [getPreferences](#sendablepreferencesgetpreferences) again, the **Preferences** instance will be read from the cache instead of from the persistent file. After this API is called to remove the instance from the cache, calling **getPreferences** again will read data from the persistent file and create a **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type            | Mandatory| Description                                                                                                                     |
| ------- | ---------------- | ---- | ----------------------------------------------------------------------------------------------------------------------- |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)          | Yes  | Application context.|
| options | [Options](#options) | Yes  | Configuration options of the **Preferences** instance.                                                                                   |

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
| 15500000 | Inner error.                   |
| 15501001 | The operations is supported in stage mode only. |
| 15501002 | Invalid dataGroupId.     |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: sendablePreferences.Options = { name: 'myStore' };
    let promise = sendablePreferences.removePreferencesFromCache(this.context, options);
    promise.then(() => {
      console.info("Succeeded in removing preferences.");
    }).catch((err: BusinessError) => {
      console.error(`Failed to remove preferences. code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## sendablePreferences.removePreferencesFromCacheSync

removePreferencesFromCacheSync(context: Context, options: Options):void

Removes a **Preferences** instance from the cache. This API returns the result synchronously.

After an application calls [getPreferences](#sendablepreferencesgetpreferences) for the first time to obtain a **Preferences** instance, the obtained **Preferences** instance is cached. When the application calls [getPreferences](#sendablepreferencesgetpreferences) again, the **Preferences** instance will be read from the cache instead of from the persistent file. After this API is called to remove the instance from the cache, calling **getPreferences** again will read data from the persistent file and create a **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name | Type                 | Mandatory| Description                                                        |
| ------- | --------------------- | ---- | ------------------------------------------------------------ |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)               | Yes  | Application context.|
| options | [Options](#options) | Yes  | Configuration options of the **Preferences** instance.                           |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 801      | Capability not supported.     |
| 15500000 | Inner error.                   |
| 15501001 | The operations is supported in stage mode only.   |
| 15501002 | Invalid dataGroupId. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: sendablePreferences.Options = { name: 'myStore' };
    sendablePreferences.removePreferencesFromCacheSync(this.context, options);
  }
}
```

## Options

Represents the configuration options of a **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

| Name       | Type  | Read-Only| Optional| Description                                                        |
| ----------- | ------ | ---- | ----| ------------------------------------------------------------ |
| name        | string | No  | No  | Name of the **Preferences** instance. The name length must be greater than zero and less than or equal to 255 bytes. The name must not contain '/' and must not end with '/'.                                   |
| dataGroupId | string \| null | No  | Yes  | Application group ID. <!--RP1-->Currently, specifying **dataGroupId** to create a Preferences instance in the corresponding shared sandbox path is not supported. <!--RP1End--><br/>This is an optional parameter. It specifies to create a **Preferences** instance in the sandbox path corresponding to this **dataGroupId**. If this parameter is not specified, the Preferences instance is created in the application sandbox directory by default.<br/> **Model constraint:** This attribute is available only in the stage model.|


## Preferences

Provides APIs for obtaining and modifying **Preferences** instances. **Preferences** inherits from [ISendable](../../arkts-utils/arkts-sendable.md#isendable) and can be passed between concurrent ArkTS instances (including the main thread and the TaskPool or Worker threads) by reference.

Before calling any API of **Preferences**, obtain a **Preferences** instance by using [sendablePreferences.getPreferences](#sendablepreferencesgetpreferences).

### get

get(key: string, defValue: lang.ISendable): Promise&lt;lang.ISendable&gt;

Obtains the value of a key from this **Preferences** instance. This API uses a promise to return the result. If the value is null or is not of the default value type, **defValue** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

 **Parameters**

| Name  | Type                   | Mandatory| Description |
| -------- | ----------------------- | ---- |--------|
| key      | string                  | Yes  | Key to be obtained. The value cannot be empty, and the maximum length is 1024 bytes. For details, see [MAX_KEY_LENGTH](#constants). |
| defValue | [lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable) | Yes  | Default value to be returned.|

**Return value**

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| Promise&lt;[lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable)&gt; | Promise object used to return the value corresponding to the key.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { lang } from '@kit.ArkTS';

let promise = preferences.get('startup', 'default');
promise.then((data: lang.ISendable) => {
  let dataStr = data as string;
  console.info(`Succeeded in getting value of 'startup'. Data: ${dataStr}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get value of 'startup'. code: ${err.code}, message: ${err.message}`);
});
```

### getSync

getSync(key: string, defValue: lang.ISendable): lang.ISendable

Obtains the value of a key from this **Preferences** instance. This API returns the result synchronously. If the value is null or is not of the default value type, **defValue** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                   | Mandatory| Description           |
| -------- | ----------------------- | ---- |---------------------|
| key      | string                  | Yes  | Key to be obtained. The value cannot be empty, and the maximum length is 1024 bytes. For details, see [MAX_KEY_LENGTH](#constants). |
| defValue | [lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable) | Yes  | Default value to be returned.|

**Return value**

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| [lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable) | Value corresponding to the key. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { lang } from '@kit.ArkTS';

let value: lang.ISendable = preferences.getSync('startup', 'default');
```

### getAll

getAll(): Promise&lt;lang.ISendable&gt;

Obtains all data in the cached **Preferences** instance. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Return value**

| Type                 | Description                                       |
| --------------------- | ------------------------------------------- |
| Promise&lt;[lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable)&gt; | Promise object that returns all the key-value data contained. |

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { lang } from '@kit.ArkTS';

let promise = preferences.getAll();
promise.then((keyValues: lang.ISendable) => {
  for (let value of Object.keys(keyValues)) {
    console.info("getAll " + JSON.stringify(value));
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get all key-values. code: ${err.code}, message: ${err.message}`);
});
```

### getAllSync

getAllSync(): lang.ISendable

Obtains all KV pairs from this **Preferences** instance. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Return value**

| Type                 | Description                                       |
| --------------------- | ------------------------------------------- |
| [lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable) | All the key-value data contained. |

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error.                   |

**Example**

```ts
import { lang } from '@kit.ArkTS';

let keyValues: lang.ISendable = preferences.getAllSync();
for (let value of Object.keys(keyValues)) {
  console.info("getAll " + JSON.stringify(value));
}
```

### put

put(key: string, value: lang.ISendable): Promise&lt;void&gt;

Writes data to this **Preferences** instance. This API uses a promise to return the result. You can use [flush](#flush) to persist the **Preferences** instance.

  > **NOTE**
  >
  > If the value contains a string that is not in UTF-8 format, store it in a Uint8Array. Otherwise, the persistent file may be damaged due to format errors.
  >
  > If the key already exists, **put()** overwrites the value. You can use **hasSync()** to check whether the KV pair exists.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type                   | Mandatory| Description                        |
| ------ | ----------------------- | ---- |--------------------------|
| key    | string                  | Yes  | Key to be modified. The value cannot be empty, and the maximum length is 1024 bytes. For details, see [MAX_KEY_LENGTH](#constants). |
| value  | [lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable) | Yes  | Value to write.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let promise = preferences.put('startup', 'auto');
promise.then(() => {
  console.info("Succeeded in putting value of 'startup'.");
}).catch((err: BusinessError) => {
  console.error(`Failed to put value of 'startup'. code: ${err.code}, message: ${err.message}`);
});
```

### putSync

putSync(key: string, value: lang.ISendable): void

Writes data to this **Preferences** instance. This API returns the result synchronously. You can use [flush](#flush) to persist the **Preferences** instance.

  > **NOTE**
  >
  > If the value contains a string that is not in UTF-8 format, store it in a Uint8Array. Otherwise, the persistent file may be damaged due to format errors.
  >
  > If the key already exists, **putSync()** overwrites the value. You can use **hasSync()** to check whether the KV pair exists.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type                   | Mandatory| Description                                                        |
| ------ | ----------------------- | ---- | ------------------------ |
| key    | string                  | Yes  | Key to be modified. The value cannot be empty, and the maximum length is 1024 bytes. For details, see [MAX_KEY_LENGTH](#constants).|
| value  | [lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable) | Yes  | Value to write.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
preferences.putSync('startup', 'auto');
```

### has

has(key: string): Promise&lt;boolean&gt;

Checks whether this **Preferences** instance contains the KV pair of the given key. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | Yes   | Name of the storage key to check. It cannot be empty and has a maximum length of [MAX_KEY_LENGTH](#constants). |

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return whether the **Preferences** instance contains the key-value pair of the given key. The value **true** indicates that it exists, and **false** indicates that it does not. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let promise = preferences.has('startup');
promise.then((val: boolean) => {
  if (val) {
    console.info("The key 'startup' is contained.");
  } else {
    console.info("The key 'startup' does not contain.");
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to check the key 'startup'. code: ${err.code}, message: ${err.message}`);
});
```

### hasSync

hasSync(key: string): boolean

Checks whether this **Preferences** instance contains the KV pair of the given key. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | Yes   | Name of the storage key to check. It cannot be empty, and its maximum length is limited to [MAX_KEY_LENGTH](#constants). |

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| boolean | Whether the **Preferences** instance contains the stored key-value pair for the given key. **true** indicates that it exists, and **false** indicates that it does not. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
let isExist: boolean = preferences.hasSync('startup');
if (isExist) {
  console.info("The key 'startup' is contained.");
} else {
  console.info("The key 'startup' does not contain.");
}
```

### delete

delete(key: string): Promise&lt;void&gt;

Deletes a KV pair from this **Preferences** instance. This API uses a promise to return the result. You can use [flush](#flush) to persist the **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | Yes   | Name of the storage key to delete. It cannot be empty, and its maximum length is [MAX_KEY_LENGTH](#constants). |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let promise = preferences.delete('startup');
promise.then(() => {
  console.info("Succeeded in deleting the key 'startup'.");
}).catch((err: BusinessError) => {
  console.error(`Failed to delete the key 'startup'. code: ${err.code}, message: ${err.message}`);
});
```

### deleteSync

deleteSync(key: string): void

Deletes a KV pair from this **Preferences** instance. This API returns the result synchronously. You can use [flush](#flush) to persist the **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | Yes   | Name of the storage key to delete. It cannot be empty, and its maximum length is [MAX_KEY_LENGTH](#constants). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
preferences.deleteSync('startup');
```

### flush

flush(): Promise&lt;void&gt;

Flushes the data in this **Preferences** instance to the persistent file. This API uses a promise to return the result.

  > **NOTE**
  >
  > If no data is modified or the modified data is the same as the cached data, the persistence file will not be updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let promise = preferences.flush();
promise.then(() => {
  console.info("Succeeded in flushing.");
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});
```

### flushSync<sup>14+</sup>

flushSync(): void

Flushes the data in the cached **Preferences** instance to the persistent file.

  > **NOTE**
  >
  > If no data is modified or the modified data is the same as the cached data, the persistence file will not be updated.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error.                   |

**Example**

```ts
preferences.flushSync();
```

### clear

clear(): Promise&lt;void&gt;

Clears this **Preferences** instance. This API uses a promise to return the result. You can use [flush](#flush) to persist the **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let promise = preferences.clear();
promise.then(() => {
  console.info("Succeeded in clearing.");
}).catch((err: BusinessError) => {
  console.error(`Failed to clear. code: ${err.code}, message: ${err.message}`);
});
```

### clearSync

clearSync(): void

Clears this **Preferences** instance. This API returns the result synchronously. You can use [flush](#flush) to persist the **Preferences** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Error codes**

For details about the error codes, see [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 15500000 | Inner error.                   |

**Example**

```ts
preferences.clearSync();
```

### on('change')

on(type: 'change', callback: Callback&lt;string&gt;): void

Subscribes to data changes. When the value of a subscribed key changes, the callback is triggered after the flush method is executed.

> **Comparison of different subscription methods:**
> - **on('change')**: Subscribes to changes of all keys. It is suitable for scenarios where global data change awareness is required.
> - **on('dataChange')**: Precisely subscribes to changes of specified keys. It is suitable for scenarios that focus on specific data, and the callback can return the specific value.
> 
> **Selection suggestion:** Use **on('change')** when you need to listen for all data changes; use **on('dataChange')** when you need to precisely know the change of a specific key and obtain the new value.

  > **NOTE**
  >
  > After [removePreferencesFromCache](#sendablepreferencesremovepreferencesfromcache) or [deletePreferences](#sendablepreferencesdeletepreferences) is called, the data change subscription will be automatically canceled. After [getPreferences](#sendablepreferencesgetpreferences) is called again, you need to subscribe to data changes again.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type    | Mandatory| Description                                    |
| -------- | -------- | ---- | ---------------------------------------- |
| type     | string   | Yes  | Event type. The value is **'change'**, which indicates data changes.|
| callback | Callback&lt;string&gt; | Yes  | Callback used to return the key whose value is changed.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
};
preferences.on('change', observer);
preferences.putSync('startup', 'manual');
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});
```

### on('multiProcessChange')

on(type: 'multiProcessChange', callback: Callback&lt;string&gt;): void

Subscribes to data changes between processes. When multiple processes hold the same preference file, calling [flush](#flush) in any process (including the current process) will trigger the callback in this API.

This API is provided for applications that have applied for [dataGroupId](#options). Avoid using this API for the applications that have not applied for **dataGroupId** because calling it in multiple processes may damage the persistent files and cause data loss.

  > **NOTE**
  >
  > The maximum number of subscriptions for inter-process data change of the same persistent file in the current process is 50. Once the limit is reached, the subscription will fail. You are advised to cancel the subscription in a timely manner after the callback is triggered.
  >
  > After [removePreferencesFromCache](#sendablepreferencesremovepreferencesfromcache) or [deletePreferences](#sendablepreferencesdeletepreferences) is called, the data change subscription will be automatically canceled. After [getPreferences](#sendablepreferencesgetpreferences) is called again, you need to subscribe to data changes again.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type. The value is **'multiProcessChange'**, which indicates inter-process data changes.|
| callback | Callback&lt;string&gt; | Yes  | Callback used to return the key whose value is changed.                  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                               |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                           |
| 15500019 | Failed to obtain the subscription service. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
};
preferences.on('multiProcessChange', observer);
preferences.putSync('startup', 'manual');
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});
```

### on('dataChange')

on(type: 'dataChange', keys: Array&lt;string&gt;, callback: Callback&lt;lang.ISendable&gt;): void

Precisely subscribes to data changes. Only when the value of a subscribed key changes is the callback triggered after the [flush](#flush) method is executed.

  > **NOTE**
  >
  > After [removePreferencesFromCache](#sendablepreferencesremovepreferencesfromcache) or [deletePreferences](#sendablepreferencesdeletepreferences) is called, the data change subscription will be automatically canceled. After [getPreferences](#sendablepreferencesgetpreferences) is called again, you need to subscribe to data changes again.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The value is **'dataChange'**, which indicates data changes.          |
| keys     | Array&lt;string&gt;                                          | Yes   | Set of keys to subscribe to.                                          |
| callback | Callback&lt;[lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable)&gt; | Yes   | Callback invoked to return multiple key-value pairs, where the key is the subscribed key that has changed and the value is the changed data, which can be number, string, boolean, bigint, or a serializable object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { lang } from '@kit.ArkTS';

let observer = (data: lang.ISendable) => {
  console.info(`observer : ${data}`);
};
let keys = ['name', 'age'];
preferences.on('dataChange', keys, observer);
preferences.putSync('name', 'xiaohong');
preferences.putSync('weight', 125);
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});
```

### off('change')

off(type: 'change', callback?: Callback&lt;string&gt;): void

Unsubscribes from data changes.

**Paired call**
- Used together with **on('change')** to unsubscribe from data changes.
- If you do not need to listen for data changes, call **off** to unsubscribe in a timely manner.

**Related methods:**
- **on('change')**: Subscribes to data changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type. The value is **'change'**, which indicates data changes.                    |
| callback | Callback&lt;string&gt; | No   | Callback function to cancel. If not specified, all registered callback functions are canceled; if specified, only the specified callback function is canceled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
};
preferences.on('change', observer);
preferences.putSync('startup', 'auto');
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
  preferences.off('change', observer);
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});
```

### off('multiProcessChange')

off(type: 'multiProcessChange', callback?: Callback&lt;string&gt;): void

Unsubscribes from inter-process data changes.

This API is provided for applications that have applied for [dataGroupId](#options). Avoid using this API for the applications that have not applied for **dataGroupId** because calling it in multiple processes may damage the persistent files and cause data loss.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type. The value is **'multiProcessChange'**, which indicates inter-process data changes.|
| callback | Callback&lt;string&gt; | No | Callback function to be unsubscribed. If this parameter is not specified, all registered callback functions are unsubscribed; if it is specified, only the specified callback function is unsubscribed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
};
preferences.on('multiProcessChange', observer);
preferences.putSync('startup', 'auto');
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
  preferences.off('multiProcessChange', observer);
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});
```
### off('dataChange')

off(type: 'dataChange', keys: Array&lt;string&gt;, callback?: Callback&lt;lang.ISendable&gt;): void

Unsubscribes from changes of specific data.

**Paired call**
- Used in pair with **on('dataChange')** to cancel the precise data change subscription.
- If you do not need to listen for data changes of specific keys, call **off** to unsubscribe in a timely manner.

**Related Methods**
- **on('dataChange')**: subscribes to precise data changes

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.DistributedDataManager.Preferences.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The value is **'dataChange'**, which indicates data changes.          |
| keys     | Array&lt;string&gt;                                          | Yes   | Set of keys to unsubscribe from. When keys is an empty array, all keys are unsubscribed from; when keys is a non-empty array, only the keys in the set are unsubscribed from. |
| callback | Callback&lt;[lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable)&gt; | No   | Callback to unsubscribe. If this parameter is not specified, all registered callbacks are unsubscribed from; if it is specified, only the specified callback is unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Preference Error Codes](errorcode-preferences.md).

| ID| Error Message                       |
| -------- | ------------------------------ |
| 401      | Parameter error. Possible causes:1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed.                       |
| 15500000 | Inner error.                   |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { lang } from '@kit.ArkTS';

let observer = (data: lang.ISendable) => {
  console.info(`observer : ${data}`);
};
let keys = ['name', 'age'];
preferences.on('dataChange', keys, observer);
preferences.putSync('name', 'xiaohong');
preferences.putSync('weight', 125);
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
  preferences.off('dataChange', keys, observer);
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});
```
