# createWatcher

## Modules to Import

```TypeScript
```

## createWatcher

```TypeScript
declare function createWatcher(filename: string, events: number, callback: AsyncCallback<number>): Watcher
```

Listens for file or directory changes. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [createWatcher](arkts-corefile-file-fs-createwatcher-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filename | string | Yes | Application sandbox path of the file. |
| events | number | Yes | **1**: The file or directory is renamed.<br>- **2**: The file or directory is modified.<br>- **3**: The file or directory is modified and renamed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Called each time a change is detected. |

**Return value:**

| Type | Description |
| --- | --- |
| [Watcher](arkts-corefile-fileio-watcher-depr-i.md) | Promise that returns the file change. |
