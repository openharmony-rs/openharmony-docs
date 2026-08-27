# createWatcher

## 导入模块

```TypeScript
```

## createWatcher

```TypeScript
declare function createWatcher(filename: string, events: number, callback: AsyncCallback<number>): Watcher
```

监听文件或者目录的变化，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [createWatcher](arkts-corefile-file-fs-createwatcher-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | 待监视文件的应用沙箱路径。 |
| events | number | 是 | 1:?监听文件或者目录是否发生重命名。   - 2：监听文件或者目录内容的是否修改。   - 3：两者都有。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 每发生变化一次，调用一次此函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Watcher](arkts-corefile-fileio-watcher-depr-i.md) | Promise对象。返回文件变化监听的实例。 |

**示例**

```TypeScript
let filePath = pathDir + "/test.txt";
fileio.createWatcher(filePath, 1, (err: BusinessError, event: number) => {
  console.info("event: " + event + "errmsg: " + JSON.stringify(err));
});
```
