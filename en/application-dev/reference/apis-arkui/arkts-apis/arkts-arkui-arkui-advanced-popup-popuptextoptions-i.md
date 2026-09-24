# PopupTextOptions

```TypeScript
export interface PopupTextOptions
```

Provides text style settings.

**Since:** 11

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

Text font size.

Default value: **$r('sys.float.ohos_id_text_size_body2')**

The string value must be convertible to a number (for example, **'10'**) or include a length unit (for example, **'10px'**); percentage-based strings are not supported.

Value range of number values: (0, +∞)

**Type:** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
