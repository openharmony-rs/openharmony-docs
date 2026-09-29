# ScreenOnVisibleOptions

```TypeScript
export interface ScreenOnVisibleOptions
```

Defines the options of the visible interface on the screen.

**Since:** 3

<!--Device-unnamed-export interface ScreenOnVisibleOptions--><!--Device-unnamed-export interface ScreenOnVisibleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { App, AppResponse, RequestFullWindowOptions, ScreenOnVisibleOptions } from '@kit.ArkUI';
```

## complete

```TypeScript
complete?: () => void
```

Called when the API call is complete.

**Since:** 3

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScreenOnVisibleOptions-complete?: () => void--><!--Device-ScreenOnVisibleOptions-complete?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Callback upon failure.

**Since:** 3

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScreenOnVisibleOptions-fail?: (data: string, code: number) => void--><!--Device-ScreenOnVisibleOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: () => void
```

Callback upon success.

**Since:** 3

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScreenOnVisibleOptions-success?: () => void--><!--Device-ScreenOnVisibleOptions-success?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## visible

```TypeScript
visible?: boolean
```

Whether to keep the application visible. The default value is **false**.

**Type:** boolean

**Since:** 3

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScreenOnVisibleOptions-visible?: boolean--><!--Device-ScreenOnVisibleOptions-visible?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
