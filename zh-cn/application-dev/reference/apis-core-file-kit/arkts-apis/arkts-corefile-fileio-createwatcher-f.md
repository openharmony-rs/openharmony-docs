# createWatcher

## createWatcher

```TypeScript
declare function createWatcher(filename: string, events: number, callback: AsyncCallback<number>): Watcher
```

监听文件或者目录的变化，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [@ohos.file.fs:createWatcher](arkts-corefile-fileio-createwatcher-f.md#createwatcher)

<!--Device-unnamed-declare function createWatcher(filename: string, events: number, callback: AsyncCallback<number>): Watcher--><!--Device-unnamed-declare function createWatcher(filename: string, events: number, callback: AsyncCallback<number>): Watcher-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filename | string | 是 | 待监视文件的应用沙箱路径。 |
| events | number | 是 | -?1:?监听文件或者目录是否发生重命名。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-?2：监听文件或者目录内容的是否修改。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_-?3：两者都有。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt; | 是 | 每发生变化一次，调用一次此函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Promise对象。返回文件变化监听的实例。 |

