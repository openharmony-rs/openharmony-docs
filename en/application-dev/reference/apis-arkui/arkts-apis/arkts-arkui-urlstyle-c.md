# UrlStyle

```TypeScript
declare class UrlStyle
```

Describes the hyperlink style.

The default color, font size, and font weight are **'#ff0a59f7'**, **'16fp'**, and **'FontWeight.Regular'**, respectively. If the styled string has **TextStyle** set, the **TextStyle** settings take precedence.

**Since:** 14

<!--Device-unnamed-declare class UrlStyle--><!--Device-unnamed-declare class UrlStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(url: string)
```

A constructor used to create a URL object.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-UrlStyle-constructor(url: string)--><!--Device-UrlStyle-constructor(url: string)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | Hyperlink URL setting. Must be a valid URL address. |

## url

```TypeScript
readonly url: string
```

Hyperlink content of the styled string.

**Type:** string

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-UrlStyle-readonly url: string--><!--Device-UrlStyle-readonly url: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
