# ScrollOptions

ScrollOptions

@interface ScrollOptions

**Since:** 6

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## complete

```TypeScript
complete?: (result: Object) => void
```

Callback function at the end of the interface invoking (executed both successfully and unsuccessfully).

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | Object | Yes |  |

## fail

```TypeScript
fail?: (result: Object) => void
```

Callback function for interface invocation failure.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | Object | Yes |  |

## success

```TypeScript
success?: (result: Object) => void
```

Callback function for successful interface invocation.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | Object | Yes |  |

## duration

```TypeScript
duration: number
```

Duration of the scrolling animation, in ms.

**Type:** number

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

The selector for current scroll.

**Type:** string

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position: number
```

Scroll to the target position of the page. Unit: px

**Type:** number

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timingFunction

```TypeScript
timingFunction?: string
```

The timing function for current scroll animation.

**Type:** string

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
