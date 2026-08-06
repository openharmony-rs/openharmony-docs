# ExceptionPromptV2

Declare struct ExceptionPromptV2 higher-order component. The exception prompt component is used to show an error message when an error arises.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct ExceptionPromptV2--><!--Device-unnamed-export declare struct ExceptionPromptV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

The method to build component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExceptionPromptV2-build(): void--><!--Device-ExceptionPromptV2-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onActionTextClick

```TypeScript
onActionTextClick?: OnActionTextClickCallback
```

Callback invoked when the icon on the right is clicked.

**类型：** OnActionTextClickCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExceptionPromptV2-onActionTextClick?: OnActionTextClickCallback--><!--Device-ExceptionPromptV2-onActionTextClick?: OnActionTextClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTipClick

```TypeScript
onTipClick?: OnTipClickCallback
```

Callback invoked when the prompt text on the left is clicked.

**类型：** OnTipClickCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExceptionPromptV2-onTipClick?: OnTipClickCallback--><!--Device-ExceptionPromptV2-onTipClick?: OnTipClickCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: PromptOptionsV2
```

ExceptionPromptV2 configuration.

**类型：** PromptOptionsV2

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExceptionPromptV2-options: PromptOptionsV2--><!--Device-ExceptionPromptV2-options: PromptOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

