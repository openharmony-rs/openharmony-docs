# PresetFillType

```TypeScript
declare enum PresetFillType
```

为不同响应式[栅格容器断点](../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)指定列数。

**起始版本：** 22

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BREAKPOINT_DEFAULT

```TypeScript
BREAKPOINT_DEFAULT = 0
```

针对List和Swiper组件：在组件宽度属于sm及更小的断点区间时显示1列，属于md断点区间时显示2列，属于lg及更大的断点区间时显示3列。

针对Grid、WaterFlow和LazyVWaterFlowLayout组件：在组件宽度属于sm及更小的断点区间时显示2列，属于md断点区间时显示3列，属于lg及更大的断点区间时显示5列。LazyVWaterFlowLayout组件从API版本26.0.0开始支持。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BREAKPOINT_SM1MD2LG3

```TypeScript
BREAKPOINT_SM1MD2LG3 = 1
```

在组件宽度属于sm及更小的断点区间时显示1列，属于md断点区间时显示2列，属于lg及更大的断点区间时显示3列。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BREAKPOINT_SM2MD3LG5

```TypeScript
BREAKPOINT_SM2MD3LG5 = 2
```

在组件宽度属于sm及更小的断点区间时显示2列，属于md断点区间时显示3列，属于lg及更大的断点区间时显示5列。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
