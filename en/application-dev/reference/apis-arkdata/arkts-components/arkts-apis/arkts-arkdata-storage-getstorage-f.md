# getStorage

## Modules to Import

```TypeScript
```

## getStorage

```TypeScript
function getStorage(path: string, callback: AsyncCallback<Storage>): void
```

Reads the specified file and loads its data to the **Storage** instance for data operations. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** getPreferences

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the target file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Storage](arkts-arkdata-storage-storage-i.md)&gt; | Yes | Callback used to return the result. |


## getStorage

```TypeScript
function getStorage(path: string): Promise<Storage>
```

Reads the specified file and loads its data to the **Storage** instance for data operations. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** getPreferences

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the target file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Storage](arkts-arkdata-storage-storage-i.md)&gt; | Promise used to return the result. |
