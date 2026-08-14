# StyledStringChangedListener

属性字符串的文本内容变化监听器。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare interface StyledStringChangedListener--><!--Device-unnamed-declare interface StyledStringChangedListener-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidChange

```TypeScript
onDidChange?: OnDidChangeCallback
```

文本内容完成变化回调函数。

**类型：** [OnDidChangeCallback](arkts-arkui-ondidchangecallback-t.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-StyledStringChangedListener-onDidChange?: OnDidChangeCallback--><!--Device-StyledStringChangedListener-onDidChange?: OnDidChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillChange

```TypeScript
onWillChange?: Callback<StyledStringChangeValue, boolean>
```

文本内容将要变化回调函数。

**类型：** Callback&lt;[StyledStringChangeValue](arkts-arkui-styledstringchangevalue-i.md), boolean&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-StyledStringChangedListener-onWillChange?: Callback<StyledStringChangeValue, boolean>--><!--Device-StyledStringChangedListener-onWillChange?: Callback<StyledStringChangeValue, boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

