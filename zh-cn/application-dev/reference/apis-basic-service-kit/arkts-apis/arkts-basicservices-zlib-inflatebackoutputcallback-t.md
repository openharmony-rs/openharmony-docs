# InflateBackOutputCallback

```TypeScript
type InflateBackOutputCallback = (outDesc: RecordData, buf: ArrayBuffer, length: int) => int
```

用户提供的输出数据会被写入回调函数中。每当解压后的数据准备好进行输出时，zlib 就会调用此函数将缓冲区中的数据写入目标位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-type InflateBackOutputCallback = (outDesc: RecordData, buf: ArrayBuffer, length: int) => int--><!--Device-zlib-type InflateBackOutputCallback = (outDesc: RecordData, buf: ArrayBuffer, length: int) => int-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outDesc | [RecordData](arkts-basicservices-recorddata-t.md) | 是 | 用户定义数据对象。 |
| buf | ArrayBuffer | 是 | 用于存储要写入的数据。 |
| length | int | 是 | 写入输出缓冲区的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 输出缓冲区的字节数。 |

