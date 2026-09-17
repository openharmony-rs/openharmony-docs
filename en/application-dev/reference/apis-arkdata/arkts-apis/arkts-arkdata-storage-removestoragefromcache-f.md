# removeStorageFromCache

## Modules to Import

```TypeScript
```

## removeStorageFromCache

```TypeScript
function removeStorageFromCache(path: string, callback: AsyncCallback<void>): void
```

Removes the singleton **Storage** instance of a file from the cache. The removed instance cannot be used for data operations. Otherwise, data inconsistency will occur. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** removePreferencesFromCache

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the target file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |


## removeStorageFromCache

```TypeScript
function removeStorageFromCache(path: string): Promise<void>
```

Removes the singleton **Storage** instance of a file from the cache. The removed instance cannot be used for data operations. Otherwise, data inconsistency will occur. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** removePreferencesFromCache

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the target file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |
