# lchown

## Modules to Import

```TypeScript
```

## lchown

```TypeScript
declare function lchown(path: string, uid: number, gid: number): Promise<void>
```

Changes the file owner (owner of the symbolic link, not the file referred to by the symbolic link) based on the file path. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |
| uid | number | Yes | New UID. |
| gid | number | Yes | New GID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |


## lchown

```TypeScript
declare function lchown(path: string, uid: number, gid: number, callback: AsyncCallback<void>): void
```

Changes the file owner (owner of the symbolic link, not the file referred to by the symbolic link) based on a file path. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |
| uid | number | Yes | New UID. |
| gid | number | Yes | New GID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked when the file owner is changed asynchronously. |
