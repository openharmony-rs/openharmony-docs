# StyledStringChangedListener

属性字符串的文本内容变化监听器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface StyledStringChangedListener--><!--Device-unnamed-export declare interface StyledStringChangedListener-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidChange

```TypeScript
onDidChange?: OnDidChangeCallback
```

文本内容完成变化回调函数。

**类型：** [OnDidChangeCallback](arkts-arkui-ondidchangecallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledStringChangedListener-onDidChange?: OnDidChangeCallback--><!--Device-StyledStringChangedListener-onDidChange?: OnDidChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillChange

```TypeScript
onWillChange?: Callback<StyledStringChangeValue, boolean>
```

文本内容将要变化回调函数。

**类型：** [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[StyledStringChangeValue](arkts-arkui-textcommon-styledstringchangevalue-i.md), boolean&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StyledStringChangedListener-onWillChange?: Callback<StyledStringChangeValue, boolean>--><!--Device-StyledStringChangedListener-onWillChange?: Callback<StyledStringChangeValue, boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

