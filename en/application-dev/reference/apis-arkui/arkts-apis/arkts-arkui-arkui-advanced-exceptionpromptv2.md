# @ohos.arkui.advanced.ExceptionPromptV2

## Modules to Import

```TypeScript
import { MarginTypeV2, PromptOptionsV2, PromptOptionsV2Config, ExceptionPromptV2 } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [PromptOptionsV2](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2-c.md) | Configuration parameter of ExceptionPromptV2. Use @ObservedV2 and @Trace to support deep observation and dynamic refresh of properties. |

### Structs

| Name | Description |
| --- | --- |
| [ExceptionPromptV2](arkts-arkui-arkui-advanced-exceptionpromptv2-exceptionpromptv2-s.md) | Declare struct ExceptionPromptV2 higher-order component. The exception prompt component is used to show an error message when an error arises. @struct { ExceptionPromptV2 } |

### Interfaces

| Name | Description |
| --- | --- |
| [PromptOptionsV2Config](arkts-arkui-arkui-advanced-exceptionpromptv2-promptoptionsv2config-i.md) | Configuration information interface for PromptOptionsV2. Used to construct PromptOptionsV2 object. |

### Enums

| Name | Description |
| --- | --- |
| [MarginTypeV2](arkts-arkui-arkui-advanced-exceptionpromptv2-margintypev2-e.md) | Control margin status of ExceptionPromptV2. |

### Types

| Name | Description |
| --- | --- |
| [OnActionTextClickCallback](arkts-arkui-onactiontextclickcallback-t.md) | Declare the callback function type to be called when clicking the icon button. @typedef { function } OnActionTextClickCallback |
| [OnTipClickCallback](arkts-arkui-ontipclickcallback-t.md) | Declare the callback function type to be called when clicking the text on the left. @typedef { function } OnTipClickCallback |

## Examples

```TypeScript
### Example 1: Setting an Exception Prompt

Starting from API version 26.0.0, this example shows how to set the exception icon, exception prompt text, margin style, and text content of the right icon button for the exception prompt.
```

```TypeScript
### Example 2 Setting an Exception Prompt of the Dialog Box Type

Since API version 26.0.0, this example uses a custom dialog box to set an exception prompt of the dialog box type.
```

```TypeScript
### Example 3: Setting a Symbol Icon

Since API version 26.0.0, this example demonstrates custom symbol icons by setting the symbolStyle property of PromptOptionsV2.
```
