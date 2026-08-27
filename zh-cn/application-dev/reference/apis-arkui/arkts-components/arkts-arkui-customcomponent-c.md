# CustomComponent

自定义组件@extends CommonAttribute [since 7 - 17] @extends BaseCustomComponent [since 18]

**继承/实现关系：** CustomComponent extends [BaseCustomComponent](arkts-arkui-basecustomcomponent-c.md)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## aboutToReuse

```TypeScript
aboutToReuse?(params: Record<string, Object | undefined | null>): void
```

当一个可复用的自定义组件从复用缓存中重新加入到节点树时，触发aboutToReuse生命周期回调，并将组件的构造参数传递给该回调。

> **说明：**
> 
> * [避免对@Link/@ObjectLink/@Prop等自动更新的状态变量，在aboutToReuse()中重复赋值](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/arkts-component_reuse#避免对linkobjectlinkprop等自动更新的状态变量在abouttoreuse中重复赋值)。
> 
> * 在滑动场景中，使用组件复用通常需要用该回调函数去更新组件的状态变量，因此在该回调函数中应避免耗时操作，否则会导致丢帧卡顿。最佳实践请参考
> [主线程耗时操作优化指导-组件复用回调](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-time-optimization-of-the-main-thread#section20815336174316)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Record & lt;string, Object \ | undefined \| null & gt; | 是 | 自定义组件的构造参数。其中key为复用时外部传入的组件成员变量名，value为复用时外部传入的对应参数 值。<br>**起始版本：** 20 |

## onLayout

```TypeScript
onLayout?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void
```

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [onPlaceChildren](arkts-arkui-basecustomcomponent-c.md#onplacechildren)

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| children | Array&lt;[LayoutChild](arkts-arkui-layoutchild-i.md)&gt; | 是 | Child component layout information. |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | 是 | Size constraint of the parent component. |

## onMeasure

```TypeScript
onMeasure?(children: Array<LayoutChild>, constraint: ConstraintSizeOptions): void
```

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [onMeasureSize](arkts-arkui-basecustomcomponent-c.md#onmeasuresize)

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| children | Array&lt;[LayoutChild](arkts-arkui-layoutchild-i.md)&gt; | 是 | Child component layout information. |
| constraint | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | 是 | Size constraint of the parent component. |
