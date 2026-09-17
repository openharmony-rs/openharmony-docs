# ResultSet (System API)

Defines APIs to access the result set obtained by querying the RDB store.

Before calling any of the following APIs, you must use [query](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md#query) to obtain a ResultSet instance.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## close

```TypeScript
close(): void
```

Closes this resultSet to release memory. If it is not closed, memory leaks may occur.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('close');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.close();
  } catch (err) {
    console.error(`close failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getRow

```TypeScript
getRow(): ValuesBucket
```

Obtains the values of all columns in the specified row.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [ValuesBucket](arkts-medialibrary-photoaccesshelper-valuesbucket-t-sys.md) | Values of all columns in the specified row. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getRow');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.goToFirstRow();
    const row = resultSet.getRow();
    resultSet.close();
  } catch (err) {
    console.error(`getRow failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getValue

```TypeScript
getValue(columnIndex: number): ValueType
```

Obtains the value of the specified column in the current row.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the specified column, starting from 0. The value ranges from 0 to the total number of columns in the result set minus 1. |

**Return value:**

| Type | Description |
| --- | --- |
| [ValueType](arkts-medialibrary-photoaccesshelper-valuetype-t-sys.md) | Allowed data field types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scene parameters validate failed, possible causes: columnIndex invalid. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getValue');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.goToFirstRow();
    const codes = resultSet.getValue(0);
    resultSet.close();
  } catch (err) {
    console.error(`getValue failed with error: ${err.code}, ${err.message}`);
  }
}
```

## goToFirstRow

```TypeScript
goToFirstRow(): boolean
```

Moves the cursor to the first row of the result set.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. **true** if the cursor is moved to the first row; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('goToFirstRow');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.goToFirstRow();
    resultSet.close();
  } catch (err) {
    console.error(`goToFirstRow failed with error: ${err.code}, ${err.message}`);
  }
}
```

## goToNextRow

```TypeScript
goToNextRow(): boolean
```

Moves the cursor to the next row in the result set.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. **true** if the cursor is moved to the next row; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('goToNextRow');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.goToNextRow();
    resultSet.close();
  } catch (err) {
    console.error(`goToNextRow failed with error: ${err.code}, ${err.message}`);
  }
}
```

## goToRow

```TypeScript
goToRow(position: number): boolean
```

Moves the cursor to the specified row in the result set.

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Index of the specified row, starting from 0. The value ranges from 0 to the total number of rows in the result set minus 1. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Operation result. **true** if the cursor is moved to the specified row; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scene parameters validate failed, possible causes: position invalid. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('goToRow');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.goToRow(0);
    resultSet.close();
  } catch (err) {
    console.error(`goToRow failed with error: ${err.code}, ${err.message}`);
  }
}
```

## columnCount

```TypeScript
columnCount: number
```

Number of columns in the result set.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## isAtLastRow

```TypeScript
isAtLastRow: boolean
```

Whether the cursor is in the last row of the result set. **true** if the cursor is in the last row; **false** otherwise.

**Type:** boolean

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## rowCount

```TypeScript
rowCount: number
```

Number of rows in the result set.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## rowIndex

```TypeScript
rowIndex: number
```

Index of the current row in the result set.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
