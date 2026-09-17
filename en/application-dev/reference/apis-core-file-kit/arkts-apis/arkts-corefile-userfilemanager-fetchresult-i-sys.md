# FetchResult (System API)

Provides APIs to manage the file retrieval result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [FetchResult](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## close

```TypeScript
close(): void
```

Releases and invalidates the **FetchFileResult** instance. After this instance is released, the APIs in this instance cannot be invoked.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [close](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#close)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## getAllObject

```TypeScript
getAllObject(callback: AsyncCallback<Array<T>>): void
```

Obtains all the file assets in the result set. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getAllObjects](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getallobjects)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;T&gt;&gt; | Yes | Callback used to return an array of all file assets in the result set. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## getAllObject

```TypeScript
getAllObject(): Promise<Array<T>>
```

Obtains all the file assets in the result set. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getAllObjects](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getallobjects)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;T&gt;&gt; | Promise that returns an array of all file assets in the result set. |

**Examples**

See [getAllObject](#getallobject)

## getCount

```TypeScript
getCount(): number
```

Obtains the total number of files in the result set.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getCount](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getcount)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the total number of files obtained. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## getFirstObject

```TypeScript
getFirstObject(callback: AsyncCallback<T>): void
```

Obtains the first file asset in the result set. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getFirstObject](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getfirstobject)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | Yes | Callback used to return the first file asset obtained. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## getFirstObject

```TypeScript
getFirstObject(): Promise<T>
```

Obtains the first file asset in the result set. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getFirstObject](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getfirstobject)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise that returns the first object in the result set. |

**Examples**

See [getFirstObject](#getfirstobject)

## getLastObject

```TypeScript
getLastObject(callback: AsyncCallback<T>): void
```

Obtains the last file asset in the result set. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getLastObject](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getlastobject)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | Yes | Callback used to return the last file asset obtained. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## getLastObject

```TypeScript
getLastObject(): Promise<T>
```

Obtains the last file asset in the result set. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getLastObject](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getlastobject)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise that returns the last object in the result set. |

**Examples**

See [getLastObject](#getlastobject)

## getNextObject

```TypeScript
getNextObject(callback: AsyncCallback<T>): void
```

Obtains the next file asset in the result set. This API uses an asynchronous callback to return the result.

Before using this API, you must use [isAfterLast()](#isafterlast) to check whether the current position is the end of the result set.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getNextObject](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getnextobject)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | Yes | Callback used to return the next file asset. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## getNextObject

```TypeScript
getNextObject(): Promise<T>
```

Obtains the next file asset in the result set. This API uses a promise to return the result.

Before using this API, you must use [isAfterLast()](#isafterlast) to check whether the current position is the end of the result set.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getNextObject](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getnextobject)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise that returns the next object in the result set. |

**Examples**

See [getNextObject](#getnextobject)

## getPositionObject

```TypeScript
getPositionObject(index: number, callback: AsyncCallback<T>): void
```

Obtains a file asset with the specified index in the result set. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getObjectByPosition](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getobjectbyposition)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the file asset to obtain. The value starts from **0**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | Yes | Callback used to return the file asset obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type index is not number |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## getPositionObject

```TypeScript
getPositionObject(index: number): Promise<T>
```

Obtains a file asset with the specified index in the result set. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getObjectByPosition](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#getobjectbyposition)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the file asset to obtain. The value starts from **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise that returns the file asset obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type index is not number |

**Examples**

See [getPositionObject](#getpositionobject)

## isAfterLast

```TypeScript
isAfterLast(): boolean
```

Checks whether the cursor is in the last row of the result set.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [isAfterLast](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-fetchresult-i.md#isafterlast)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the cursor is in the last row of the result set; returns **false** otherwise. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```
