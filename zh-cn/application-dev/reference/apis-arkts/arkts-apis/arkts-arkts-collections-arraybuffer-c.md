# ArrayBuffer

ArkTS TypedArray（[Int8Array](arkts-collections.md#collections)、
[Uint8Array](arkts-collections.md#collections)、
[Int16Array](arkts-collections.md#collections)、
[Uint16Array](arkts-collections.md#collections)、
[Int32Array](arkts-collections.md#collections)、
[Uint32Array](arkts-collections.md#collections)、
[Uint8ClampedArray](arkts-collections.md#collections)、
[Float32Array](arkts-collections.md#collections)）的底层数据结构。

> **说明**
>
> - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。
> **装饰器类型**：\@Sendable

**起始版本：** 12

**装饰器类型：** @Sendable

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(byteLength: number)
```

构造函数，用于创建一个指定长度的ArkTS ArrayBuffer对象。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| byteLength | number | 是 | buffer所占的字节数，取值范围是[0, 2147483647]，否则会抛出异常。0代表构造的ArrayBuffer的长度为0，2147483647表示构造的ArrayBuffer的长度为2147483647。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200012](../../errorcode-universal.md#10200012-The) | The ArrayBuffer's constructor cannot be directly invoked. |

## slice

```TypeScript
slice(begin: number, end?: number): ArrayBuffer
```

返回一个新的ArkTS ArrayBuffer对象，其包含原ArkTS ArrayBuffer指定范围的内容。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | number | 是 | 开始索引，如果`begin &lt; 0`，则会从`begin +<br/>arrayBuffer.byteLength`位置开始。 |
| end | number | 否 | 结束索引（不包括该元素），如果`end &lt; 0`，则会到`end +<br/>arrayBuffer.byteLength`位置结束。默认为原ArkTS ArrayBuffer的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 新生成的ArkTS ArrayBuffer对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200011](../../errorcode-universal.md#10200011-The) | The slice method cannot be bound. |
| [10200201](../../errorcode-universal.md#10200201-Concurrent) | Concurrent modification error. |

## byteLength

```TypeScript
readonly byteLength: number
```

buffer所占的字节数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

