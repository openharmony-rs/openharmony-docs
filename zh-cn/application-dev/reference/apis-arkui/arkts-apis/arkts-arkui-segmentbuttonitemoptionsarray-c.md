# SegmentButtonItemOptionsArray

用于保存按钮信息的数组。

> **说明：**
>
> SegmentButtonItemOptionsArray仅支持保存2到5个按钮信息元素。

**继承/实现关系：** SegmentButtonItemOptionsArray extends [Array<SegmentButtonItemOptions>](Array<SegmentButtonItemOptions>)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(elements: SegmentButtonItemTuple)
```

构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elements | SegmentButtonItemTuple | 是 | 按钮信息。 |

## create

```TypeScript
static create(elements: SegmentButtonItemTuple): SegmentButtonItemOptionsArray
```

创建一个SegmentButtonItemOptionsArray对象。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elements | SegmentButtonItemTuple | 是 | 按钮信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SegmentButtonItemOptionsArray | 返回创建的SegmentButtonItemOptionsArray对象。 |

## pop

```TypeScript
pop(): SegmentButtonItemOptions | undefined
```

移除数组末尾最后一个元素，返回被移除的元素。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SegmentButtonItemOptions | Element removed from the array. |

## push

```TypeScript
push(...items: SegmentButtonItemArray): number
```

在数组末尾添加新的元素，返回添加元素后数组的长度。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | SegmentButtonItemArray | 是 | 被添加的按钮信息数组。<br>默认值：0个被添加的按钮信息数组。 |

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

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SegmentButtonItemOptions | Element removed from the array. |

## splice

```TypeScript
splice(start: number, deleteCount: number, ...items: SegmentButtonItemOptions[]): SegmentButtonItemOptions[]
```

在数组中，删除从start位置开始的deleteCount数量的元素，并插入items中的元素，返回一个包含了被删除的元素的数组。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 删除元素的起始位置。 |
| deleteCount | number | 是 | 删除元素的数量。 |
| items | SegmentButtonItemOptions[] | 是 | 从start开始要加入到数组中的元素。<br>默认值：不指定任何元素，将从数组中删除元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SegmentButtonItemOptions[] | An array containing the removed elements. |

## unshift

```TypeScript
unshift(...items: SegmentButtonItemArray): number
```

在数组开头添加一个新的元素，返回添加元素后数组的长度。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | SegmentButtonItemArray | 是 | 添加的按钮信息数组。<br>默认值：0个被添加的按钮信息数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加元素后数组的长度。 |

