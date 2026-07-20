# HeifsMetadata

HeifsMetadata implements Metadata

HEIF序列图像元数据类，用于存储图像的元数据。

**继承/实现关系：** HeifsMetadata implements [Metadata](arkts-image-image-metadata-i.md)

**起始版本：** 23

<!--Device-image-class HeifsMetadata implements Metadata--><!--Device-image-class HeifsMetadata implements Metadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

<a id="clone"></a>
## clone

```TypeScript
clone(): Promise<HeifsMetadata>
```

对Heifs元数据进行克隆。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-clone(): Promise<HeifsMetadata>--><!--Device-HeifsMetadata-clone(): Promise<HeifsMetadata>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HeifsMetadata&gt; | Promise对象，成功返回Heifs元数据实例。 |

<a id="createinstance"></a>
## createInstance

```TypeScript
static createInstance(): HeifsMetadata
```

创建一个空的[HeifsMetadata](arkts-image-image-heifsmetadata-c.md)实例。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-static createInstance(): HeifsMetadata--><!--Device-HeifsMetadata-static createInstance(): HeifsMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HeifsMetadata](arkts-image-image-heifsmetadata-c.md) | 返回HeifsMetadata的空实例。 |

<a id="getallproperties"></a>
## getAllProperties

```TypeScript
getAllProperties(): Promise<Record<string, string | null>>
```

获取图片中所有元数据的属性的值。使用Promise异步回调。

要查询的属性的具体信息请参考[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-getAllProperties(): Promise<Record<string, string | null>>--><!--Device-HeifsMetadata-getAllProperties(): Promise<Record<string, string | null>>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, string \| null&gt;&gt; | Promise对象，返回元数据拥有的所有属性的值。 |

<a id="getblob"></a>
## getBlob

```TypeScript
getBlob(): Promise<ArrayBuffer>
```

以二进制数据的形式获取元数据。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-getBlob(): Promise<ArrayBuffer>--><!--Device-HeifsMetadata-getBlob(): Promise<ArrayBuffer>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise对象，返回元数据的二进制数据。 |

<a id="getproperties"></a>
## getProperties

```TypeScript
getProperties(key: Array<string>): Promise<Record<string, string | null>>
```

获取图像元数据的属性值。使用Promise异步回调。

要查询的属性的具体信息请参考[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-getProperties(key: Array<string>): Promise<Record<string, string | null>>--><!--Device-HeifsMetadata-getProperties(key: Array<string>): Promise<Record<string, string | null>>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | Array&lt;string&gt; | 是 | 要获取的值的属性名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, string \| null&gt;&gt; | Promise对象，返回元数据要获取的属性的值，如果获取失败则返回错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: unsupported metadata type |

<a id="setblob"></a>
## setBlob

```TypeScript
setBlob(blob: ArrayBuffer): Promise<void>
```

使用二进制数据替换当前元数据。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-setBlob(blob: ArrayBuffer): Promise<void>--><!--Device-HeifsMetadata-setBlob(blob: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blob | ArrayBuffer | 是 | 要替换的二进制数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible causes: The blob is empty or has a length of 0. |

<a id="setproperties"></a>
## setProperties

```TypeScript
setProperties(records: Record<string, string | null>): Promise<void>
```

批量设置图片元数据中的指定属性的值。使用Promise异步回调。

要查询的属性的具体信息请参考[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-setProperties(records: Record<string, string | null>): Promise<void>--><!--Device-HeifsMetadata-setProperties(records: Record<string, string | null>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| records | Record&lt;string, string \| null&gt; | 是 | 用户要修改HeifsMetadata对象的属性和值的键值对集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: unsupported metadata type. |

## heifsCanvasHeight

```TypeScript
readonly heifsCanvasHeight?: number
```

HEIF序列图片的画布高度。

单位为像素（px）。

该值为正整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-readonly heifsCanvasHeight?: int--><!--Device-HeifsMetadata-readonly heifsCanvasHeight?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## heifsCanvasWidth

```TypeScript
readonly heifsCanvasWidth?: number
```

HEIF序列图片的画布宽度。

单位为像素（px）。

该值为正整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-readonly heifsCanvasWidth?: int--><!--Device-HeifsMetadata-readonly heifsCanvasWidth?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## heifsDelayTime

```TypeScript
readonly heifsDelayTime?: number
```

HEIF序列图片的每帧播放时长。单位为毫秒（ms）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-readonly heifsDelayTime?: int--><!--Device-HeifsMetadata-readonly heifsDelayTime?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## heifsUnclampedDelayTime

```TypeScript
readonly heifsUnclampedDelayTime?: number
```

HEIF序列图片每帧未钳制的延迟时长。

单位为毫秒（ms）。

该值为正整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeifsMetadata-readonly heifsUnclampedDelayTime?: int--><!--Device-HeifsMetadata-readonly heifsUnclampedDelayTime?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

