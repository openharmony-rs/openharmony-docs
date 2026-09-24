# Storage

```TypeScript
interface Storage
```

Provides APIs for obtaining and modifying storage data.

Before calling the following APIs, use [data_storage.getStorage](arkts-arkdata-storage-getstoragesync-f.md) or [data_storage.getStorageSync](arkts-arkdata-storage-getstoragesync-f.md) to obtain the **Storage** instance.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** preferences

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

## Modules to Import

```TypeScript
```

## clear

```TypeScript
clear(callback: AsyncCallback<void>): void
```

Clears this **Storage** object. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** clear

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
storage.clear(function (err) {
    if (err) {
        console.info("Failed to clear the storage with err: " + err);
        return;
    }
    console.info("Succeeded in clearing the storage.");
})
```

<a id="clear-1"></a>

## clear

```TypeScript
clear(): Promise<void>
```

Clears this **Storage** object. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** clear

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A promise object. |

**Examples**

```TypeScript
let promiseclear = storage.clear();
promiseclear.then(() => {
    console.info("Succeeded in clearing the storage.");
}).catch((err) => {
    console.info("Failed to clear the storage with err: " + err);
})
```

## clearSync

```TypeScript
clearSync(): void
```

Clears this **Storage** object.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** clear

**Examples**

```TypeScript
storage.clearSync();
```

## delete

```TypeScript
delete(key: string, callback: AsyncCallback<void>): void
```

Deletes data with the specified key from this storage object. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** delete

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
storage.delete('startup', function (err) {
    if (err) {
        console.info("Failed to delete startup key failed err: " + err);
        return;
    }
    console.info("Succeeded in deleting startup key.");
})
```

<a id="delete-1"></a>

## delete

```TypeScript
delete(key: string): Promise<void>
```

Deletes data with the specified key from this storage object. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** delete

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
let promisedel = storage.delete('startup')
promisedel.then(() => {
    console.info("Succeeded in deleting startup key.");
}).catch((err) => {
    console.info("Failed to delete startup key failed err: " + err);
})
```

## deleteSync

```TypeScript
deleteSync(key: string): void
```

Deletes data with the specified key from this storage object.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** delete

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |

**Examples**

```TypeScript
storage.deleteSync('startup');
```

## flush

```TypeScript
flush(callback: AsyncCallback<void>): void
```

Saves the modification of this object to the **Storage** instance and synchronizes the modification to the file. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** flush

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
storage.flush(function (err) {
    if (err) {
        console.info("Failed to flush to file with err: " + err);
        return;
    }
    console.info("Succeeded in flushing to file.");
})
```

<a id="flush-1"></a>

## flush

```TypeScript
flush(): Promise<void>
```

Saves the modification of this object to the **Storage** instance and synchronizes the modification to the file. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** flush

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
let promiseflush = storage.flush();
promiseflush.then(() => {
    console.info("Succeeded in flushing to file.");
}).catch((err) => {
    console.info("Failed to flush to file with err: " + err);
})
```

## flushSync

```TypeScript
flushSync(): void
```

Saves the modification of this object to the **Storage** instance and synchronizes the modification to the file.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** flush

**Examples**

```TypeScript
storage.flushSync();
```

## get

```TypeScript
get(key: string, defValue: ValueType, callback: AsyncCallback<ValueType>): void
```

Obtains the value corresponding to a key. If the value is null or not of the default value type, **defValue** is returned. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** get

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |
| defValue | [ValueType](arkts-arkdata-storage-valuetype-t.md) | Yes | Default value to be returned. It can be a number, string, or Boolean value. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ValueType](arkts-arkdata-storage-valuetype-t.md)&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
storage.get('startup', 'default', function(err, value) {
    if (err) {
        console.info("Failed to get the value of startup with err: " + err);
        return;
      }
    console.info("The value of startup is " + value);
})
```

<a id="get-1"></a>

## get

```TypeScript
get(key: string, defValue: ValueType): Promise<ValueType>
```

Obtains the value corresponding to a key. If the value is null or not of the default value type, **defValue** is returned. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** get

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |
| defValue | [ValueType](arkts-arkdata-storage-valuetype-t.md) | Yes | Default value to be returned. It can be a number, string, or Boolean value. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ValueType](arkts-arkdata-storage-valuetype-t.md)&gt; | Promise used to return the result. |

**Examples**

```TypeScript
let promiseget = storage.get('startup', 'default');
promiseget.then((value) => {
    console.info("The value of startup is " + value)
}).catch((err) => {
    console.info("Failed to get the value of startup with err: " + err);
})
```

## getSync

```TypeScript
getSync(key: string, defValue: ValueType): ValueType
```

Obtains the value corresponding to a key. If the value is null or not of the default value type, **defValue** is returned.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** get

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |
| defValue | [ValueType](arkts-arkdata-storage-valuetype-t.md) | Yes | Default value to be returned if the value of the specified key does not exist. It can be a number, string, or Boolean value. |

**Return value:**

| Type | Description |
| --- | --- |
| [ValueType](arkts-arkdata-storage-valuetype-t.md) | Value corresponding to the specified key. If the value is null or not in the default value format, the default value is returned. |

**Examples**

```TypeScript
let value = storage.getSync('startup', 'default');
console.info("The value of startup is " + value);
```

## has

```TypeScript
has(key: string, callback: AsyncCallback<boolean>): boolean
```

Checks whether the storage object contains data with a given key. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** has

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the storage object contains data with the specified key; returns **false** otherwise. |

**Examples**

```TypeScript
storage.has('startup', function (err, isExist) {
    if (err) {
        console.info("Failed to check the key of startup with err: " + err);
        return;
    }
    if (isExist) {
        console.info("The key of startup is contained.");
    }
})
```

<a id="has-1"></a>

## has

```TypeScript
has(key: string): Promise<boolean>
```

Checks whether the storage object contains data with a given key. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** has

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. |

**Examples**

```TypeScript
let promisehas = storage.has('startup')
promisehas.then((isExist) => {
    if (isExist) {
        console.info("The key of startup is contained.");
    }
}).catch((err) => {
    console.info("Failed to check the key of startup with err: " + err);
})
```

## hasSync

```TypeScript
hasSync(key: string): boolean
```

Checks whether the storage object contains data with a given key.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** has

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the storage object contains data with the specified key; returns **false** otherwise. |

**Examples**

```TypeScript
let isExist = storage.hasSync('startup');
if (isExist) {
    console.info("The key of startup is contained.");
}
```

## off('change')

```TypeScript
off(type: 'change', callback: Callback<StorageObserver>): void
```

Unsubscribes from data changes.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** off

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type. The value **change** indicates data change events. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StorageObserver](arkts-arkdata-storage-storageobserver-i.md)&gt; | Yes | Callback for the data change. |

**Examples**

```TypeScript
let observer = function (key) {
    console.info("The key of " + key + " changed.");
}
storage.off('change', observer);
```

## on('change')

```TypeScript
on(type: 'change', callback: Callback<StorageObserver>): void
```

Subscribes to data changes. The **StorageObserver** needs to be implemented. When the value of the key subscribed to is changed, a callback will be invoked after **flush()** or **flushSync()** is executed.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** on

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type. The value **change** indicates data change events. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[StorageObserver](arkts-arkdata-storage-storageobserver-i.md)&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let observer = function (key) {
    console.info("The key of " + key + " changed.");
}
storage.on('change', observer);
storage.putSync('startup', 'auto');
storage.flushSync();  // observer will be called.
```

## put

```TypeScript
put(key: string, value: ValueType, callback: AsyncCallback<void>): void
```

Obtains the **Storage** instance corresponding to the specified file, writes data to the **Storage** instance using a **Storage** API, and saves the modification using **flush()** or **flushSync()**. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** put

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | Yes | New value to store. It can be a number, string, or Boolean value. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
storage.put('startup', 'auto', function (err) {
    if (err) {
        console.info("Failed to put the value of startup with err: " + err);
        return;
    }
    console.info("Succeeded in putting the value of startup.");
})
```

<a id="put-1"></a>

## put

```TypeScript
put(key: string, value: ValueType): Promise<void>
```

Obtains the **Storage** instance corresponding to the specified file, writes data to the **Storage** instance using a **Storage** API, and saves the modification using **flush()** or **flushSync()**. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** put

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | Yes | New value to store. It can be a number, string, or Boolean value. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
let promiseput = storage.put('startup', 'auto');
promiseput.then(() => {
    console.info("Succeeded in putting the value of startup.");
}).catch((err) => {
    console.info("Failed to put the value of startup with err: " + err);
})
```

## putSync

```TypeScript
putSync(key: string, value: ValueType): void
```

Obtains the **Storage** instance corresponding to the specified file, writes data to the **Storage** instance using a **Storage** API, and saves the modification using **flush()** or **flushSync()**.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** put

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data. It cannot be empty. |
| value | [ValueType](arkts-arkdata-storage-valuetype-t.md) | Yes | New value to store. It can be a number, string, or Boolean value. |

**Examples**

```TypeScript
storage.putSync('startup', 'auto');
```
