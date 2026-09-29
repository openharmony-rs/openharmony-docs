# requestAutoFill

## Modules to Import

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

## requestAutoFill

```TypeScript
export function requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void
```

Trigger an auto fill request.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-autoFillManager-export function requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void--><!--Device-autoFillManager-export function requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | Indicates the ui context where the filling operation will be performed. |
| request | [FillRequest](arkts-ability-autofillmanager-fillrequest-t.md) | Yes | Indicates the struct of automatic filling request. |
| callback | [AutoFillCallback](arkts-ability-autofillmanager-autofillcallback-i.md) | No | Indicates the callback that used to receive the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**
