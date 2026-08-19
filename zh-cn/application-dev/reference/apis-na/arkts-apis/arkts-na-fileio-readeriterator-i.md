# ReaderIterator

文件读取迭代器。在调用ReaderIterator的方法前，需要先通过readLines方法（同步或异步）来构建一个ReaderIterator实例。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-interface ReaderIterator--><!--Device-fileIo-interface ReaderIterator-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
```

## next

```TypeScript
next(): ReaderIteratorResult
```

获取迭代器下一项内容。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ReaderIterator-next(): ReaderIteratorResult--><!--Device-ReaderIterator-next(): ReaderIteratorResult-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ReaderIteratorResult](arkts-na-file-fs-readeriteratorresult-i.md) | 文件读取迭代器返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900037 | No data available |
| 13900042 | Unknown error |

