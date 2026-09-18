# choose

## Modules to Import

```TypeScript
```

## choose

```TypeScript
declare function choose(types?: string[]): Promise<string>
```

Chooses files of the specified types. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | string[] | No | Types of the files to choose. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. An error code is returned. |


## choose

```TypeScript
declare function choose(callback: AsyncCallback<string>): void
```

Chooses a file. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. An error code is returned. |


## choose

```TypeScript
declare function choose(types: string[], callback: AsyncCallback<string>): void
```

Chooses files of the specified types. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| types | string[] | Yes | Types of the files to choose. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. An error code is returned. |
