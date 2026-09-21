# ItemFillPolicy

```TypeScript
declare interface ItemFillPolicy
```

定义一个适用于WaterFlow、Grid、List、Swiper和LazyVWaterFlowLayout组件的响应式布局策略。LazyVWaterFlowLayout组件从API版本26.0.0开始支持。

**起始版本：** 22

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fillType

```TypeScript
fillType?: ResponsiveFillType
```

为不同的响应式断点指定列数。默认值为BREAKPOINT_DEFAULT。

**类型：** [ResponsiveFillType](arkts-arkui-responsivefilltype-t.md)

**默认值：** ResponsiveFillType.BREAKPOINT_DEFAULT

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
