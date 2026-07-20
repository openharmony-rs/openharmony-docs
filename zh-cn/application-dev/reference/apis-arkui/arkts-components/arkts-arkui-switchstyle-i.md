# SwitchStyle

Switch类型的样式。

**起始版本：** 12

<!--Device-unnamed-declare interface SwitchStyle--><!--Device-unnamed-declare interface SwitchStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pointColor

```TypeScript
pointColor?: ResourceColor
```

设置Switch类型的圆形滑块颜色。

默认值：$r('sys.color.ohos_id_color_foreground_contrary')

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwitchStyle-pointColor?: ResourceColor--><!--Device-SwitchStyle-pointColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pointRadius

```TypeScript
pointRadius?: number | Resource
```

设置Switch类型的圆形滑块半径，单位为vp。

**说明：**

不支持百分比，设定值小于0时按照默认算法设置，设定值大于等于0时按照设定值设置。

未设定此属性时，圆形滑块半径根据默认算法设置。

默认算法：（组件高度（单位：vp） / 2） - （2vp * 组件高度（单位：vp） / 20vp）。

**类型：** number \| Resource

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwitchStyle-pointRadius?: number | Resource--><!--Device-SwitchStyle-pointRadius?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## trackBorderRadius

```TypeScript
trackBorderRadius?: number | Resource
```

设置Switch类型的滑轨的圆角，单位为vp。

**说明：**

不支持百分比，设定值小于0时按照默认算法设置，设定值大于组件高度一半时按照组件高度一半设置，其他场合按照设定值设置。

未设定此属性时，滑轨圆角根据默认算法设置。

默认算法：组件高度（单位：vp） / 2。

**类型：** number \| Resource

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwitchStyle-trackBorderRadius?: number | Resource--><!--Device-SwitchStyle-trackBorderRadius?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## unselectedColor

```TypeScript
unselectedColor?: ResourceColor
```

设置Switch类型关闭状态的背景颜色。

默认值：深色和浅色模式下均为0x337F7F7F。从API version 20开始，如果开启了[优化深浅色模式切换开销](docroot://ui/ui-dark-light-color-adaptation.md#优化深浅色模式切换开销)能力，浅色模式下默认值为0x19000000，表现效果为10%透明度的黑色；深色模式下默认值为0x19FFFFFF，表现效果为10%透明度的白色。

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SwitchStyle-unselectedColor?: ResourceColor--><!--Device-SwitchStyle-unselectedColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

