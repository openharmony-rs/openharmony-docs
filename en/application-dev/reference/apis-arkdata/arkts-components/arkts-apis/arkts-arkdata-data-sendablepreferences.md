# @ohos.data.sendablePreferences

The **sendablePreferences** module provides APIs for processing data in the form of key-value (KV) pairs, including querying, modifying, and persisting KV pairs. In the KV pairs, the key must be a string, and the value can be a number, a string, a Boolean value, a bigint, or a serializable object. The persistent files of the shared user preferences are stored in the [preferencesDir](../../../application-models/application-context-stage.md#obtaining-application-file-paths) directory. Before creating a preferences object, ensure that the **preferencesDir** path can be read and written. The [encryption level](../../apis-ability-kit/arkts-apis/arkts-ability-contextconstant-areamode-e.md) of the persistent file directory determines the access to the files. For details, see [Application File Directory and Application File Path](../../../file-management/app-sandbox-directory.md#application-file-directory-and-application-file-path). Sendable preferences can be passed between concurrent ArkTS instances (including the main thread and TaskPool or Worker threads) by reference. It allows for higher performance than [user preferences](arkts-arkdata-data-preferences.md). For more information, see [Using Sendable Objects](../../../arkts-utils/sendable-guide.md).

> **NOTE:** 
> 
> The shared user preferences are not thread-safe and may cause file damage and data loss when used in multi-process
> scenarios. Do not use it in multi-process scenarios.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core @name sendablePreferences

## Modules to Import

```TypeScript
import { sendablePreferences } from '@kit.ArkData';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [deletePreferences](arkts-arkdata-sendablepreferences-deletepreferences-f.md) | Deletes a specified **Preferences** instance from the cache. If the **Preferences** instance has a corresponding persistent file, the persistent file is also deleted. This API uses a promise to return the result. Avoid using a deleted **Preferences** instance to perform data operations, which may cause data inconsistency. |
| [getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md) | Obtains a **Preferences** instance. This API uses a promise to return the result. |
| [getPreferencesSync](arkts-arkdata-sendablepreferences-getpreferencessync-f.md) | Obtains a **Preferences** instance. This API returns the result synchronously. |
| [removePreferencesFromCache](arkts-arkdata-sendablepreferences-removepreferencesfromcache-f.md) | Removes a **Preferences** instance from the cache. This API uses a promise to return the result. After an application calls [getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md) for the first time to obtain a **Preferences** instance, the obtained **Preferences** instance is cached. When the application calls [getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md) again, the **Preferences** instance will be read from the cache instead of from the persistent file. After this API is called to remove the instance from the cache, calling **getPreferences** again will read data from the persistent file and create a **Preferences** instance. |
| [removePreferencesFromCacheSync](arkts-arkdata-sendablepreferences-removepreferencesfromcachesync-f.md) | Removes a **Preferences** instance from the cache. This API returns the result synchronously. After an application calls [getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md) for the first time to obtain a **Preferences** instance, the obtained **Preferences** instance is cached. When the application calls [getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md) again, the **Preferences** instance will be read from the cache instead of from the persistent file. After this API is called to remove the instance from the cache, calling **getPreferences** again will read data from the persistent file and create a **Preferences** instance. |

### Interfaces

| Name | Description |
| --- | --- |
| [Options](arkts-arkdata-sendablepreferences-options-i.md) | Represents the configuration options of a **Preferences** instance. |
| [Preferences](arkts-arkdata-sendablepreferences-preferences-i.md) | Provides APIs for obtaining and modifying **Preferences** instances. **Preferences** inherits from [ISendable](../../../arkts-utils/arkts-sendable.md#isendable) and can be passed between concurrent ArkTS instances (including the main thread and the TaskPool or Worker threads) by reference. Before calling any API of **Preferences**, obtain a **Preferences** instance by using [sendablePreferences.getPreferences](arkts-arkdata-sendablepreferences-getpreferences-f.md). |

### Constants

| Name | Description |
| --- | --- |
| [MAX_KEY_LENGTH](arkts-arkdata-sendablepreferences-con.md#max_key_length) | Maximum length of a key, which is 1024 bytes. |
| [MAX_VALUE_LENGTH](arkts-arkdata-sendablepreferences-con.md#max_value_length) | Maximum length of a value, which is 16 MB. |
