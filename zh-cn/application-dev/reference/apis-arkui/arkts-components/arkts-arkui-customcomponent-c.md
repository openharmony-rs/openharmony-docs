# CustomComponent

自定义组件

**继承/实现关系：** CustomComponent extends [BaseCustomComponent](arkts-arkui-basecustomcomponent-c.md)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToReuse

```TypeScript
aboutToReuse?(params: Record<string, Object | undefined | null>): void
```

Invoked when a reusable custom component is re-added to the node tree
from the reuse cache to receive construction parameters of the component.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Record&lt;string, Object \| undefined \| null&gt; | 是 | Custom component init params. |

## onLayout

```TypeScript
onLayout?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void
```

**起始版本：** 9

**废弃版本：** 10

**替代接口：** onPlaceChildren

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| children | Array&lt;LayoutChild&gt; | 是 | Child component layout information. |
| constraint | ConstraintSizeOptions | 是 | Size constraint of the parent component. |

## onMeasure

```TypeScript
onMeasure?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void
```

**起始版本：** 9

**废弃版本：** 10

**替代接口：** onMeasureSize

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| children | Array&lt;LayoutChild&gt; | 是 | Child component layout information. |
| constraint | ConstraintSizeOptions | 是 | Size constraint of the parent component. |

