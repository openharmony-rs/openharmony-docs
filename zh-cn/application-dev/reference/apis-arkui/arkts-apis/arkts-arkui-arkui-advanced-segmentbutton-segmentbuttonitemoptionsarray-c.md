# SegmentButtonItemOptionsArray

用于保存按钮信息的数组。

> **说明：**
> 
> SegmentButtonItemOptionsArray仅支持保存2到5个按钮信息元素。

**继承/实现关系：** SegmentButtonItemOptionsArray extends Array<SegmentButtonItemOptions>

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(elements: SegmentButtonItemTuple)
```

构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elements | [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | 是 | 用于初始化数组的按钮信息元组，包含2到5个按钮选项元素，每个元素定义一个按钮的图标、文本等属性。 |

## create

```TypeScript
static create(elements: SegmentButtonItemTuple): SegmentButtonItemOptionsArray
```

创建一个SegmentButtonItemOptionsArray对象。与构造函数接受相同的参数，功能一致，可根据编码习惯选择使用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elements | [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | 是 | 用于初始化数组的按钮信息元组，包含2到5个按钮选项元素，每个元素定义一个按钮的图标、文本等属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md) | 返回创建的SegmentButtonItemOptionsArray对象，用于保存按钮信息的数组。 |

## pop

```TypeScript
pop(): SegmentButtonItemOptions | undefined
```

移除数组末尾最后一个元素，返回被移除的元素。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md) \| undefined | 被移除的元素。 |

## push

```TypeScript
push(...items: SegmentButtonItemArray): number
```

在数组末尾添加新的元素，返回添加元素后数组的长度。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | 是 | 被添加的按钮信息数组。 默认值：不传入任何按钮信息元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加元素后数组的长度。 |

## shift

```TypeScript
shift(): SegmentButtonItemOptions | undefined
```

移除数组开头第一个元素，返回被移除的元素。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md) \| undefined | 被移除的元素。 |

## splice

```TypeScript
splice(start: number, deleteCount: number, ...items: SegmentButtonItemOptions[]): SegmentButtonItemOptions[]
```

在数组中，删除从start位置开始的deleteCount数量的元素，并插入items中的元素，返回一个包含了被删除的元素的数组。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 删除元素的起始位置，从0开始计数。 |
| deleteCount | number | 是 | 删除元素的数量，取值范围大于等于0。若deleteCount超过数组剩余长度，则删除从start位置开始的所有剩余元素。 |
| items | [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md)[] | 是 | 从start开始要加入到数组中的元素。 默认值：不指定任何元素，将从数组中删除元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md)[] | 返回包含了被删除的元素的数组。 |

## unshift

```TypeScript
unshift(...items: SegmentButtonItemArray): number
```

在数组开头添加新的元素，返回添加元素后数组的长度。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | 是 | 添加的按钮信息数组。 默认值：不传入任何按钮信息元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加元素后数组的长度。 |
