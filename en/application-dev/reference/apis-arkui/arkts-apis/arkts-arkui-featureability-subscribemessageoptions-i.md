# SubscribeMessageOptions

```TypeScript
export interface SubscribeMessageOptions
```

@typedef SubscribeMessageOptions

**Since:** 5

**Deprecated since:** 8

<!--Device-unnamed-export interface SubscribeMessageOptions--><!--Device-unnamed-export interface SubscribeMessageOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Called when the messages fail to be sent.

**Since:** 5

**Deprecated since:** 8

<!--Device-SubscribeMessageOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeMessageOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (data: SubscribeMessageResponse) => void
```

Called when the messages are sent successfully.

**Since:** 5

**Deprecated since:** 8

<!--Device-SubscribeMessageOptions-success?: (data: SubscribeMessageResponse) => void--><!--Device-SubscribeMessageOptions-success?: (data: SubscribeMessageResponse) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [SubscribeMessageResponse](arkts-arkui-featureability-subscribemessageresponse-i.md) | Yes |  |
