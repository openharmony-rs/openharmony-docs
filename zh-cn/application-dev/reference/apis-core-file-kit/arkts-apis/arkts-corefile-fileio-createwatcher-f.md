# createWatcher

## createWatcher

```TypeScript
declare function createWatcher(filename: string, events: number, callback: AsyncCallback<number>): Watcher
```

监听文件或者目录的变化，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [fs:createWatcher](arkts-corefile-file-fs-createwatcher-f.md#createwatcher-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | 待监视文件的应用沙箱路径。 |
| events | number | 是 | -?1:?监听文件或者目录是否发生重命名。<br/>-?2：监听文件或者目录内容的是否修改。<br/>-?3：两者都有。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 每发生变化一次，调用一次此函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Watcher | Promise对象。返回文件变化监听的实例。 |

