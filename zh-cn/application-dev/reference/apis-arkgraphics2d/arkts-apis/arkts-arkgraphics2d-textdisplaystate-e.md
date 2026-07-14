# TextDisplayState

文本显示状态的枚举。表示文本排版后的原生结果，与外部画布裁切、溢出屏幕等外部显示因素无关。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Graphics.Drawing

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

未知显示状态，默认状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## ALL

```TypeScript
ALL = 1
```

完整显示状态，文本无截断、无省略，全部内容正常显示。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## CLIP

```TypeScript
CLIP = 2
```

裁剪显示状态，文本超出排版区域的部分被直接裁剪隐藏。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## OMITTED

```TypeScript
OMITTED = 3
```

省略显示状态，文本超出排版区域后，部分内容以指定字符（如省略号 '...'）替代展示。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

