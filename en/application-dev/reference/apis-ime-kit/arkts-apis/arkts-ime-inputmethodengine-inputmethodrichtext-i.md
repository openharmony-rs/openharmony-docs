# InputMethodRichText

```TypeScript
export interface InputMethodRichText
```

Defines the rich text.

**Since:** 26.1.0

<!--Device-inputMethodEngine-export interface InputMethodRichText--><!--Device-inputMethodEngine-export interface InputMethodRichText-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## getSpans

```TypeScript
getSpans(): Array<RichTextSpan>
```

Obtains the spans that make up the rich text.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodRichText-getSpans(): Array<RichTextSpan>--><!--Device-InputMethodRichText-getSpans(): Array<RichTextSpan>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[RichTextSpan](arkts-ime-inputmethodengine-richtextspan-i.md)&gt; | Array of spans that make up the rich text. |

## getString

```TypeScript
getString(): string
```

Extracts the plain text from the rich text.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodRichText-getString(): string--><!--Device-InputMethodRichText-getString(): string-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| string | Plain text extracted from the rich text. |
