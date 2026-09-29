# Storage (System API)

```TypeScript
declare class Storage
```

A background API for persistent storage, which provides data persistence capabilities based on key-value pairs, including data reading, writing, clearing, and deletion. PersistentStorage uses this API to implement local persistence of AppStorage data, making it suitable for scenarios where flexible local persistent storage of application data is required.

**Since:** 7

<!--Device-unnamed-declare class Storage--><!--Device-unnamed-declare class Storage-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## clear

```TypeScript
clear(): void
```

Clears all stored data.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-Storage-clear(): void--><!--Device-Storage-clear(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## constructor

```TypeScript
constructor(needCrossThread?: boolean, file?: string)
```

A constructor for creating a **Storage** instance.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-Storage-constructor(needCrossThread?: boolean, file?: string)--><!--Device-Storage-constructor(needCrossThread?: boolean, file?: string)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| needCrossThread | boolean | No | Whether to access the storage across threads. This is a reserved API and does not provide specific functions. Default value: **false**. |
| file | string | No | Name of the storage file. This is a reserved API and does not provide specific functions. By default, **persistent_storage** in the application file directory is used as the storage file. |

## delete

```TypeScript
delete(key: string): void
```

Deletes the stored data corresponding to the specified key.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-Storage-delete(key: string): void--><!--Device-Storage-delete(key: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the storage to delete. |

## get

```TypeScript
get(key: string): string | undefined
```

Reads the stored data corresponding to the specified key from the disk.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-Storage-get(key: string): string | undefined--><!--Device-Storage-get(key: string): string | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the storage to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; undefined | Value corresponding to the key; **undefined** is returned if the key does not exist. |

## set

```TypeScript
set(key: string, val: any): void
```

Stores the data corresponding to the specified key persistently to the disk.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-Storage-set(key: string, val: any): void--><!--Device-Storage-set(key: string, val: any): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Name of the storage key to set. |
| val | any | Yes | Data to store. It supports basic types such as string, number, and boolean, as well as serializable objects and arrays. The data is serialized and then persisted to the storage file. |
