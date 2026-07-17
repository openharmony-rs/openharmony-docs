# CustomComponent

自定义组件

**继承/实现关系：** CustomComponent extends [BaseCustomComponent](arkts-arkui-common-basecustomcomponent-c.md)

**起始版本：** 18

<!--Device-unnamed-declare class CustomComponent extends BaseCustomComponent--><!--Device-unnamed-declare class CustomComponent extends BaseCustomComponent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToReuse

```TypeScript
aboutToReuse?(params: Record<string, Object | undefined | null>): void
```

Invoked when a reusable custom component is re-added to the node tree from the reuse cache to receive construction parameters of the component.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CustomComponent-aboutToReuse?(params: Record<string, Object | undefined | null>): void--><!--Device-CustomComponent-aboutToReuse?(params: Record<string, Object | undefined | null>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Record<string, Object \| undefined \| null> | 是 | Custom component init params. |

## onLayout

```TypeScript
onLayout?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void
```

**起始版本：** 9

**废弃版本：** 10

**替代接口：** onPlaceChildren

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CustomComponent-onLayout?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void--><!--Device-CustomComponent-onLayout?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| children | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<LayoutChild> | 是 | Child component layout information. |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-units-constraintsizeoptions-i.md) | 是 | Size constraint of the parent component. |

## onMeasure

```TypeScript
onMeasure?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void
```

**起始版本：** 9

**废弃版本：** 10

**替代接口：** onMeasureSize

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CustomComponent-onMeasure?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void--><!--Device-CustomComponent-onMeasure?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| children | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<LayoutChild> | 是 | Child component layout information. |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-units-constraintsizeoptions-i.md) | 是 | Size constraint of the parent component. |

