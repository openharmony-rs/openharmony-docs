# Watcher

Listens for file change. You can call the **Watcher.stop()** method synchronously or asynchronously to stop the listening.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [Watcher](arkts-corefile-file-fs-watcher-i.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
```

## stop

```TypeScript
stop(): Promise<void>
```

Stops the **watcher** instance. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [stop](arkts-corefile-file-fs-watcher-i.md#stop)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | return Promise |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let watcher = fileio.createWatcher(filePath, 1, (err: BusinessError, event: number) => {
  console.info("event: " + event + "errmsg: " + JSON.stringify(err));
});
watcher.stop().then(() => {
  console.info("close watcher succeed");
});
```

```TypeScript
let filePath = pathDir + "/test.txt";
let watcher = fileio.createWatcher(filePath, 1, (err: BusinessError, event: number) => {
  console.info("event: " + event + "errmsg: " + JSON.stringify(err));
});
watcher.stop(() => {
  console.info("close watcher succeed");
})
```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops the **watcher** instance. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [stop](arkts-corefile-file-fs-watcher-i.md#stop)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked when **watcher** is stopped asynchronously. |

**Examples**

See [stop](#stop)
