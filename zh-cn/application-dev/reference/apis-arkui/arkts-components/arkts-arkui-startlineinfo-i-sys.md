# StartLineInfo（系统接口）

用于记录Grid页面内起始行的位置信息。

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startIndex

```TypeScript
startIndex: number
```

目标索引或目标偏移量所在行的起始索引。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startLine

```TypeScript
startLine: number
```

startIndex对应的GridItem所在的起始行，一般为Grid视窗内的起始行，对于跨多行的GridItem需要找到该节点的起始行，可能在视窗外。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startOffset

```TypeScript
startOffset: number
```

startIndex对应的GridItem的顶部与Grid顶部之间的偏移量。<br/>单位：vp

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## totalOffset

```TypeScript
totalOffset: number
```

总滚动偏移量，即Grid中第一个GridItem的顶部与Grid顶部之间的偏移量。<br/>单位：vp

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

