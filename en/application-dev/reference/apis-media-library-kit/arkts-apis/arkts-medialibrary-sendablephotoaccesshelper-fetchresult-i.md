# FetchResult

Provides APIs to manage the file retrieval result.

**Inheritance/Implementation:** FetchResult extends lang.ISendable

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## close

```TypeScript
close(): void
```

Closes this FetchResult instance to invalidate it. After this instance is closed, the APIs in this instance cannot be invoked.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14000011 | Internal system error |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in sendablePhotoAccessHelper.getPhotoAccessHelper.
```

## getAllObjects

```TypeScript
getAllObjects(): Promise<Array<T>>
```

Obtains all the file assets in the result set. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;T&gt;&gt; | Promise used to return all the assets in the result set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14000011 | Internal system error |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in sendablePhotoAccessHelper.getPhotoAccessHelper.
```

## getCount

```TypeScript
getCount(): number
```

Obtains the total number of files in the result set.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Total number of files obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14000011 | Internal system error |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in sendablePhotoAccessHelper.getPhotoAccessHelper.
```

## getFirstObject

```TypeScript
getFirstObject(): Promise<T>
```

Obtains the first asset in the result set. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise used to return the first object in the result set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14000011 | Internal system error |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in sendablePhotoAccessHelper.getPhotoAccessHelper.
```

## getLastObject

```TypeScript
getLastObject(): Promise<T>
```

Obtains the last asset in the result set. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise used to return the last object in the result set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14000011 | Internal system error |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in sendablePhotoAccessHelper.getPhotoAccessHelper.
```

## getNextObject

```TypeScript
getNextObject(): Promise<T>
```

Obtains the next asset in the result set. This API uses a promise to return the result.

Before using this API, you must use [isAfterLast()](#isafterlast) to check whether the current position is the end of the result set.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise used to return the next object in the result set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14000011 | Internal system error |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in sendablePhotoAccessHelper.getPhotoAccessHelper.
```

## getObjectByPosition

```TypeScript
getObjectByPosition(index: number): Promise<T>
```

Obtains the asset with the given index in the result set. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the asset to obtain. The value starts from **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise used to return the asset obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in sendablePhotoAccessHelper.getPhotoAccessHelper.
```

## isAfterLast

```TypeScript
isAfterLast(): boolean
```

Checks whether the cursor is in the last row of the result set.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the cursor is in the last row of the result set; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14000011 | Internal system error |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in sendablePhotoAccessHelper.getPhotoAccessHelper.
```
