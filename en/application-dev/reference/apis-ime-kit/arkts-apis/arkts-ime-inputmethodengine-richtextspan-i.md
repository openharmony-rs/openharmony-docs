# RichTextSpan

```TypeScript
export interface RichTextSpan
```

Defines a span in the rich text.

**Since:** 26.1.0

<!--Device-inputMethodEngine-export interface RichTextSpan--><!--Device-inputMethodEngine-export interface RichTextSpan-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## getContent

```TypeScript
getContent(): string
```

Obtains the content of the span. <br> <br>  
> **NOTE:** <br> <br>
> If the span type is image, the content is the tag information carried when the image is inserted into the ArkUI rich text component.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RichTextSpan-getContent(): string--><!--Device-RichTextSpan-getContent(): string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| string | Content of the span. |

## getRange

```TypeScript
getRange(): Range
```

Obtains the range of the span in the rich text.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RichTextSpan-getRange(): Range--><!--Device-RichTextSpan-getRange(): Range-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [Range](arkts-ime-inputmethodengine-range-i.md) | Range of the span in the rich text, represented by the start and end positions. |

## getType

```TypeScript
getType(): SpanType
```

Obtains the type of the span.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RichTextSpan-getType(): SpanType--><!--Device-RichTextSpan-getType(): SpanType-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| [SpanType](arkts-ime-inputmethodengine-spantype-e.md) | Type of the span. |
