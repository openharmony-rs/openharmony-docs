# MenuGridStyleOptions

菜单栅格样式选项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: number
```

栅格中元素的数量。

默认值：3

取值范围：

当为上图下文形的栅格样式时，元素数量范围为[0, 6]。

当为纯图标形的栅格样式时，元素数量范围[0, 4]。

未设置、异常值按照默认值处理。

**类型：** number

**默认值：** 3

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## horizontalSize

```TypeScript
horizontalSize?: number
```

栅格中元素的水平尺寸，表示栅格内每行可显示的元素数量。

默认值：3

**说明：**

当为上图下文形的栅格样式时，水平尺寸范围为[1, 3]，即栅格行数为[1, 2]。

当为纯图标形的栅格样式时，水平尺寸范围为[1, 4]，即栅格行数为1。

未设置、异常值按照默认值处理。

**类型：** number

**默认值：** 3

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: MenuGridPosition
```

栅格在菜单中的位置。

默认值：MenuGridPosition.TOP

**类型：** MenuGridPosition

**默认值：** MenuGridPosition.TOP

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

