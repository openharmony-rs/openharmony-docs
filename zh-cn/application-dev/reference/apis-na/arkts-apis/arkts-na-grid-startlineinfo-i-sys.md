# StartLineInfo（系统接口）

用于记录Grid页面内起始行的位置信息。 **系统接口：** 此接口为系统接口。 **模型约束：** 此接口仅可在Stage模型下使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface StartLineInfo--><!--Device-unnamed-export declare interface StartLineInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startIndex

```TypeScript
startIndex: int
```

目标索引或目标偏移量所在行的起始索引。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartLineInfo-startIndex: int--><!--Device-StartLineInfo-startIndex: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startLine

```TypeScript
startLine: int
```

startIndex对应的GridItem所在的起始行，一般为Grid视窗内的起始行，对于跨多行的GridItem需要找到该节点的起始行，可能在视窗外。 取值限定为整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartLineInfo-startLine: int--><!--Device-StartLineInfo-startLine: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## startOffset

```TypeScript
startOffset: double
```

startIndex对应的GridItem的顶部与Grid顶部之间的偏移量。 单位：vp。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartLineInfo-startOffset: double--><!--Device-StartLineInfo-startOffset: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## totalOffset

```TypeScript
totalOffset: double
```

总滚动偏移量，即Grid中第一个GridItem的顶部与Grid顶部之间的偏移量。 单位：vp。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartLineInfo-totalOffset: double--><!--Device-StartLineInfo-totalOffset: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

