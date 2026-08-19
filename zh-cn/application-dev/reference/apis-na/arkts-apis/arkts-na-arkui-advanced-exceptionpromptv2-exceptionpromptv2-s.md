# ExceptionPromptV2

Declare struct ExceptionPromptV2 higher-order component. The exception prompt component is used to show an error message when an error arises.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare struct ExceptionPromptV2--><!--Device-unnamed-export declare struct ExceptionPromptV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## build

```TypeScript
@Builder
  build(): void
```

The method to build component.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExceptionPromptV2-@Builder  build(): void--><!--Device-ExceptionPromptV2-@Builder  build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onActionTextClick

```TypeScript
@Event
  onActionTextClick?: OnActionTextClickCallback
```

Callback invoked when the icon on the right is clicked.

**类型：** [OnActionTextClickCallback](../../apis-arkui/arkts-apis/arkts-arkui-onactiontextclickcallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExceptionPromptV2-@Event  onActionTextClick?: OnActionTextClickCallback--><!--Device-ExceptionPromptV2-@Event  onActionTextClick?: OnActionTextClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTipClick

```TypeScript
@Event
  onTipClick?: OnTipClickCallback
```

Callback invoked when the prompt text on the left is clicked.

**类型：** [OnTipClickCallback](../../apis-arkui/arkts-apis/arkts-arkui-ontipclickcallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExceptionPromptV2-@Event  onTipClick?: OnTipClickCallback--><!--Device-ExceptionPromptV2-@Event  onTipClick?: OnTipClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
@Param
  options: PromptOptionsV2
```

ExceptionPromptV2 configuration.

**类型：** [PromptOptionsV2](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExceptionPromptV2-@Param  options: PromptOptionsV2--><!--Device-ExceptionPromptV2-@Param  options: PromptOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

