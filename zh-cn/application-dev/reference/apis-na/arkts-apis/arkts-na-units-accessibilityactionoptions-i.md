# AccessibilityActionOptions

设置组件的无障碍操作的可选参数，用于限制或修改屏幕朗读等辅助应用发起的操作行为。仅Slider组件支持使用。在其他组件使用该接口时，编译环节可 正常通过，但接口功能不生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface AccessibilityActionOptions--><!--Device-unnamed-export declare interface AccessibilityActionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scrollStep

```TypeScript
scrollStep?: int
```

无障碍手势触发的无障碍滚动操作中的组件操作步数。默认值基于组件默认值。 不支持的组件配置不生效。 当前支持组件：slider，用于slider组件聚焦后通过手势上下扫动触发slider组件的滑动操作。滑动距离：scrollStep* [step](../../../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#slideroptions)。取值范围： [1, ([max](../../../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#slideroptions) - [min](../../../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#slideroptions))/[step](../../../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#slideroptions)]， 默认值为1。超出取值范围时取默认值1；在取值范围内，scrollStep为非整数时向下取整。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AccessibilityActionOptions-scrollStep?: int--><!--Device-AccessibilityActionOptions-scrollStep?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

