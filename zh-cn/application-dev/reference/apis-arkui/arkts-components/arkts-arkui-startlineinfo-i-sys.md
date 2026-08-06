# StartLineInfo（系统接口）

用于记录Grid页面内起始行的位置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

<!--Device-unnamed-declare interface StartLineInfo--><!--Device-unnamed-declare interface StartLineInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startIndex

```TypeScript
startIndex: int
```

在OnGetStartIndexByOffsetCallback中，表示滚动偏移量所在行的起始索引；在OnGetStartIndexByIndexCallback中，表示目标索引所在行的起始索引。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartLineInfo-startIndex: int--><!--Device-StartLineInfo-startIndex: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startLine

```TypeScript
startLine: int
```

startIndex对应GridItem在Grid布局中的起始行号。若该GridItem跨多行，且当前视窗从该GridItem中间位置开始显示，startLine仍表示该GridItem在完整Grid布局中实际占用的首行行号。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartLineInfo-startLine: int--><!--Device-StartLineInfo-startLine: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startOffset

```TypeScript
startOffset: double
```

startIndex对应的GridItem的顶部与Grid顶部之间的偏移量。 单位：vp

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartLineInfo-startOffset: double--><!--Device-StartLineInfo-startOffset: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## totalOffset

```TypeScript
totalOffset: double
```

总滚动偏移量，即Grid中第一个GridItem的顶部与Grid顶部之间的偏移量。 单位：vp

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartLineInfo-totalOffset: double--><!--Device-StartLineInfo-totalOffset: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

