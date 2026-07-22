# Watcher

Watcher是文件变化监听的实例，调用Watcher.stop()方法（同步或异步）来停止文件监听。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [fs:Watcher](arkts-corefile-fileio-watcher-depr-i.md)

<!--Device-unnamed-declare interface Watcher--><!--Device-unnamed-declare interface Watcher-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## stop

```TypeScript
stop(): Promise<void>
```

关闭watcher监听，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [stop](arkts-corefile-fileio-watcher-depr-i.md#stop)

<!--Device-Watcher-stop(): Promise<void>--><!--Device-Watcher-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | return Promise |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let watcher = fileio.createWatcher(filePath, 1, (err: BusinessError, event: number) => {
  console.info("event: " + event + "errmsg: " + JSON.stringify(err));
});
watcher.stop().then(() => {
  console.info("close watcher succeed");
});

```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

关闭watcher监听，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [stop](arkts-corefile-fileio-watcher-depr-i.md#stop)

<!--Device-Watcher-stop(callback: AsyncCallback<void>): void--><!--Device-Watcher-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 以异步方法关闭watcher监听之后的回调。 |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let watcher = fileio.createWatcher(filePath, 1, (err: BusinessError, event: number) => {
  console.info("event: " + event + "errmsg: " + JSON.stringify(err));
});
watcher.stop(() => {
  console.info("close watcher succeed");
})

```

