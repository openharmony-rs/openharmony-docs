# ExceptionPromptV2

```TypeScript
export declare struct ExceptionPromptV2
```

Defines an exception prompt component, which is used when there is an exception that needs to be prompted.

**Since:** 26.0.0

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct ExceptionPromptV2--><!--Device-unnamed-export declare struct ExceptionPromptV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { MarginTypeV2, PromptOptionsV2, PromptOptionsV2Config, ExceptionPromptV2 } from '@kit.ArkUI';
```

## onActionTextClick

```TypeScript
onActionTextClick?: OnActionTextClickCallback
```

Callback invoked when the right-side icon button is tapped. When not set, no operation is performed.

**Since:** 26.0.0

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExceptionPromptV2-onActionTextClick?: OnActionTextClickCallback--><!--Device-ExceptionPromptV2-onActionTextClick?: OnActionTextClickCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onTipClick

```TypeScript
onTipClick?: OnTipClickCallback
```

Callback invoked when the left-side tip text is tapped. When not set, no operation is performed.

**Since:** 26.0.0

**Decorator:** @Event

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExceptionPromptV2-onTipClick?: OnTipClickCallback--><!--Device-ExceptionPromptV2-onTipClick?: OnTipClickCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: PromptOptionsV2
```

Configuration information of the current exception prompt.

**Type:** [PromptOptionsV2](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ExceptionPromptV2-options: PromptOptionsV2--><!--Device-ExceptionPromptV2-options: PromptOptionsV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
