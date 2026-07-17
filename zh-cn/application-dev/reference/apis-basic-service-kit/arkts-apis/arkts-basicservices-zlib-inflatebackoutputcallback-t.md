# InflateBackOutputCallback

```TypeScript
type InflateBackOutputCallback = (outDesc: object, buf: ArrayBuffer, length: number) => number
```

用户提供的输出数据会被写入回调函数中。每当解压后的数据准备好进行输出时，zlib 就会调用此函数将缓冲区中的数据写入目标位置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-zlib-type InflateBackOutputCallback = (outDesc: object, buf: ArrayBuffer, length: int) => int--><!--Device-zlib-type InflateBackOutputCallback = (outDesc: object, buf: ArrayBuffer, length: int) => int-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outDesc | object | 是 | 用户定义数据对象。 |
| buf | ArrayBuffer | 是 | 用于存储要写入的数据。 |
| length | int | 是 | 写入输出缓冲区的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 输出缓冲区的字节数。 |

