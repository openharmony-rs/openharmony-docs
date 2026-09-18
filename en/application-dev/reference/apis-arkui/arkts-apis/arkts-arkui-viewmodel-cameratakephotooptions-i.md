# CameraTakePhotoOptions

CameraTakePhotoOptions

@interface CameraTakePhotoOptions

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

## quality

```TypeScript
quality: "high" | "normal" | "low"
```

Picture quality.

**Type:** "high" &#124; "normal" &#124; "low"

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
