# ConcatArray

该接口定义了支持数组连接操作的对象，并继承了`ISendable`接口，使其兼具高效数组拼接和跨线程传递能力。

> **说明**  
>  
> - 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。  
> 文档中存在泛型的使用，涉及以下泛型标记符：

- T：Type，支持[Sendable支持的数据类型](../../../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)。

**继承/实现关系：** ConcatArray extends [ISendable](arkts-arkts-collections-isendable-t.md)

**起始版本：** 12

<!--Device-collections-interface ConcatArray<T> extends ISendable--><!--Device-collections-interface ConcatArray<T> extends ISendable-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { collections } from '@kit.ArkTS';
```

## join

```TypeScript
join(separator?: string): string
```

将ConcatArray的所有元素连接成一个字符串，元素之间可以用指定的分隔符分隔。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ConcatArray-join(separator?: string): string--><!--Device-ConcatArray-join(separator?: string): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| separator | string | 否 | 用于分隔ConcatArray元素的字符串。如果省略，则使用逗号分隔。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 包含所有ConcatArray元素连接成的字符串。如果ConcatArray为空，则返回空字符串。 |

## slice

```TypeScript
slice(start?: number, end?: number): ConcatArray<T>
```

返回一个新的ConcatArray，该ConcatArray是原始ConcatArray的切片。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ConcatArray-slice(start?: number, end?: number): ConcatArray<T>--><!--Device-ConcatArray-slice(start?: number, end?: number): ConcatArray<T>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 否 | 开始索引。如果`start &lt; 0`，则会从`start + array.length`位置开始。默认值为0。 |
| end | number | 否 | 结束索引（不包括该元素）。如果`end &lt; 0`，则会到`end + array.length`位置结束。默认为ArkTS Array的长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ConcatArray](arkts-arkts-collections-concatarray-i.md)<T> | 包含原始ConcatArray切片的新ConcatArray。 |

## index

```TypeScript
readonly [index: number]: T
```

返回ConcatArray指定索引位置的元素。

**类型：** T

**起始版本：** 12

<!--Device-ConcatArray-readonly [index: number]: T--><!--Device-ConcatArray-readonly [index: number]: T-End-->

**系统能力：** SystemCapability.Utils.Lang

## length

```TypeScript
readonly length: number
```

ConcatArray的元素个数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ConcatArray-readonly length: number--><!--Device-ConcatArray-readonly length: number-End-->

**系统能力：** SystemCapability.Utils.Lang

