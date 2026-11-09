# PreviewTextStyle

```TypeScript
export interface PreviewTextStyle
```

Style of the preview text.

**Since:** 26.1.0

<!--Device-inputMethodEngine-export interface PreviewTextStyle--><!--Device-inputMethodEngine-export interface PreviewTextStyle-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## underlineColor

```TypeScript
underlineColor?: number
```

Underline color in 0xRRGGBB format. Optional; when not specified, the underline color should follow the application's theme color. If transparency is provided, it is invalid and will be ignored by the editor. The value must be an integer. Default: when not provided, no color is passed to the edit box; the edit box handles it and defaults to following the cursor color.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PreviewTextStyle-underlineColor?: int--><!--Device-PreviewTextStyle-underlineColor?: int-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## underlineStyle

```TypeScript
underlineStyle: UnderlineStyle
```

Underline style.

**Type:** [UnderlineStyle](arkts-ime-inputmethodengine-underlinestyle-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PreviewTextStyle-underlineStyle: UnderlineStyle--><!--Device-PreviewTextStyle-underlineStyle: UnderlineStyle-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
