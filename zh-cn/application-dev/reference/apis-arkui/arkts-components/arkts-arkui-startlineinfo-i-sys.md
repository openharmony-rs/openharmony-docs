# StartLineInfo（系统接口）

用于记录Grid页面内起始行的位置信息。

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## startIndex

```TypeScript
startIndex: number
```

在OnGetStartIndexByOffsetCallback中，表示滚动偏移量所在行的起始索引；在OnGetStartIndexByIndexCallback中，表示目标索引所在行的起始索引。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startLine

```TypeScript
startLine: number
```

startIndex对应GridItem在Grid布局中的起始行号。若该GridItem跨多行，且当前视窗从该GridItem中间位置开始显示，startLine仍表示该GridItem在完整Grid布局中实际占用的首行行号。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startOffset

```TypeScript
startOffset: number
```

startIndex对应的GridItem的顶部与Grid顶部之间的偏移量。单位：vp

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## totalOffset

```TypeScript
totalOffset: number
```

总滚动偏移量，即Grid中第一个GridItem的顶部与Grid顶部之间的偏移量。单位：vp

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
