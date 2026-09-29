# PopupTextOptions

```TypeScript
export interface PopupTextOptions
```

Provides text style settings.

**Since:** 11

<!--Device-unnamed-export interface PopupTextOptions--><!--Device-unnamed-export interface PopupTextOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Popup, PopupButtonOptions, PopupIconOptions, PopupOptions, PopupTextOptions } from '@kit.ArkUI';
```

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Text font color.

Default value: **$r('sys.color.ohos_id_color_text_secondary')**

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupTextOptions-fontColor?: ResourceColor--><!--Device-PopupTextOptions-fontColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

Font size of the text.

Default value: `$r('sys.float.ohos_id_text_size_body2')`

For the string type, the value can be a string that can be converted to a number (such as '10') or a string with a length unit (such as '10px'). Setting a percentage string is not supported.

For the number type, the value range is (0, +∞). When the type is number, the unit is fp.

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupTextOptions-fontSize?: number | string | Resource--><!--Device-PopupTextOptions-fontSize?: number | string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

Text font weight.

For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a heavier font weight. The default value is **400**.

For the string type, only strings of the number type are supported, for example, **"400"**, **"bold"**, **"bolder"**, **"lighter"**, **"regular"**, and **"medium"**, which correspond to the enumerated values in **FontWeight**.

Default value: **FontWeight.Regular**

**Type:** number &#124; [FontWeight](arkts-arkui-fontweight-e.md) &#124; string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupTextOptions-fontWeight?: number | FontWeight | string--><!--Device-PopupTextOptions-fontWeight?: number | FontWeight | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

Text content.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PopupTextOptions-text: ResourceStr--><!--Device-PopupTextOptions-text: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
