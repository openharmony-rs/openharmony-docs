# GaugeIndicatorOptions

数据量规图表指针选项。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## icon

```TypeScript
icon?: ResourceStr
```

图标资源路径。  
**说明：**不配置则使用系统默认样式，系统默认样式为三角形指针。仅支持使用svg格式的图标，若使用其他格式，则使用默认的三角形样式指针。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**默认值：** system style.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: Dimension
```

指针距离圆环外边的间距。默认值：8单位：vp  
**说明：**不支持百分比。对于默认的三角形样式指针，为黑色三角形到圆环外边的间距。若设置值小于0，则使用默认值。若设置值大于圆环半径，则使用默认值。

**类型：** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**默认值：** 8vp

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
