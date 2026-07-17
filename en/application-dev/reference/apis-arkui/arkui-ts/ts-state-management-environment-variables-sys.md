# Built-in Environment Variable Description (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhushilin0206-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=79e4597a11fe0470e85a7a6ec526decbb0cbcff4 translatedAt=2026-07-15T07:36:36.871Z pushedAt=2026-07-15T08:56:08.970Z -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Storage

A background API for persistent storage, which provides data persistence capabilities based on key-value pairs, including data reading, writing, clearing, and deletion. It supports custom storage file paths and cross-thread safe access. PersistentStorage uses this API to implement local persistence of AppStorage data, making it suitable for scenarios where flexible local persistent storage of application data is required.

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(needCrossThread?: boolean, file?: string)

A constructor for creating a **Storage** instance.

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name            | Type    | Mandatory | Description                                                                                                                                                                                                                                                                                                                                 |
| --------------- | ------- | ---- | -------------------------------------- |
| needCrossThread | boolean | No        | Whether to access the storage across threads. The value **true** means the instance supports cross-thread read and write, and the framework processes storage access in a thread-safe manner. The value **false** means the storage is accessed only within the thread where the instance is created (usually the main thread).<br>Default value: **false**. |
| file            | string  | No        | Storage file name. By default, the **persistent_storage** file in the application file directory is used as a storage file.                                                                                                                                                                                                                      |

### get

get(key: string): string \| undefined

Reads the stored data corresponding to the specified key from the disk.

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ----------------------- | ---- | -------------------------------- |
| key | string | Yes | Key of the data to obtain. |

**Returns**

| Type | Description |
| --------- | -------------------------------------------------------- |
| string \| undefined | Value corresponding to the key. **undefined** is returned if the key does not exist. |

### set

set(key: string, val: any): void

Persistently stores the data corresponding to the specified key to the disk. If **needCrossThread** is set to **false** when the **Storage** instance is created, this API can only be called within the thread where the instance is created (usually the main thread).

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                    | Mandatory | Description                             |
| -------- | ----------------------- | ---- | ------------------------------- |
| key      | string                  | Yes   | Key of the data to set.             |
| val      | any                     | Yes   | Data to store. The value can be of a basic type such as string, number, or boolean, or a serializable object or array. The data will be serialized and persisted to the storage file.                    |

### clear

clear(): void

Clears all stored data.

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

### delete

delete(key: string): void

Deletes the stored data corresponding to the specified key.

**System API:** This is a system API.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type   | Mandatory | Description                        |
| ---- | ------ | --------- | ---------------------------------- |
| key  | string | Yes       | Key of the data to delete. |