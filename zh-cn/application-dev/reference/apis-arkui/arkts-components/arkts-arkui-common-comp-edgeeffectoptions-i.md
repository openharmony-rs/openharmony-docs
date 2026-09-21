# EdgeEffectOptions

```TypeScript
declare interface EdgeEffectOptions
```

edgeEffect属性参数对象。

@interface EdgeEffectOptions

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alwaysEnabled

```TypeScript
alwaysEnabled: boolean
```

组件内容大小小于组件自身时，设置是否开启滑动效果。设置为true开启滑动效果，设置为false关闭滑动效果。[List](arkts-arkui-list-comp.md#list)、[Grid](arkts-arkui-grid-comp.md#grid)和[WaterFlow](arkts-arkui-waterflow-comp.md#water_flow)组件默认值是false，[Scroll](arkts-arkui-scroll-comp.md#scroll)组件默认值是true。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## effectEdge

```TypeScript
effectEdge?: number
```

设置边缘效果生效的边缘。

如果设置[EffectEdge](arkts-arkui-common-comp-effectedge-e.md).START表示只有起始边生效。如果设置[EffectEdge](arkts-arkui-common-comp-effectedge-e.md).END表示只有末尾边生效。

默认值为[EffectEdge](arkts-arkui-common-comp-effectedge-e.md).START | [EffectEdge](arkts-arkui-common-comp-effectedge-e.md).END表示双边同时生效。当设置为其它异常值时，则默认双边同时生效。

如果需要双边都不生效，可将edgeEffect设置为EdgeEffect.None。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
