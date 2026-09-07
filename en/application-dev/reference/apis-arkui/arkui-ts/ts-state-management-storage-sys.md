# Storage (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhushilin0206-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=b4c16a3481f0a0bf24de133bf760018019cda10c translatedAt=2026-09-02T11:24:24.194Z pushedAt=2026-09-03T02:28:47.255Z -->

>**NOTE**
>
>The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Storage

A background API for persistent storage, which provides data persistence capabilities based on key-value pairs, including data reading, writing, clearing, and deletion. PersistentStorage uses this API to implement local persistence of AppStorage data, making it suitable for scenarios where flexible local persistent storage of application data is required.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(needCrossThread?: boolean, file?: string)

A constructor for creating a **Storage** instance.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| --------------- | ------- | ---- | -------------------------------------- |
| needCrossThread | boolean | No | Whether to access the storage across threads. This is a reserved API and does not provide specific functions. Default value: **false**. |
| file | string | No | Name of the storage file. This is a reserved API and does not provide specific functions. By default, **persistent_storage** in the application file directory is used as the storage file. |

### get

get(key: string): string \| undefined

Reads the stored data corresponding to the specified key from the disk.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                    | Mandatory | Description                              |
| -------- | ----------------------- | ---- | -------------------------------- |
| key      | string                  | Yes   | Key of the storage to obtain.              |

**Return value**

| Type      | Description                                                      |
| --------- | -------------------------------------------------------- |
| string \| undefined | Value corresponding to the key; **undefined** is returned if the key does not exist.          |

### set

set(key: string, val: any): void

Stores the data corresponding to the specified key persistently to the disk.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ----------------------- | ---- | ------------------------------- |
| key | string | Yes | Name of the storage key to set. |
| val | any | Yes | Data to store. It supports basic types such as string, number, and boolean, as well as serializable objects and arrays. The data is serialized and then persisted to the storage file. |

### clear

clear(): void

Clears all stored data.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### delete

delete(key: string): void

Deletes the stored data corresponding to the specified key.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ----------------------- | ---- | ------------------------------- |
| key | string | Yes | Key of the storage to delete. |
