# RichText properties/events

```TypeScript
declare class RichTextAttribute extends CommonMethod<RichTextAttribute>
```

Defines the RichText attribute functions.

**Inheritance/Implementation:** RichTextAttribute extends CommonMethod<RichTextAttribute>

**Since:** 8

<!--Device-unnamed-declare class RichTextAttribute extends CommonMethod<RichTextAttribute>--><!--Device-unnamed-declare class RichTextAttribute extends CommonMethod<RichTextAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onComplete

```TypeScript
onComplete(callback: () => void)
```

Triggered when the RichText loading ends.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11 - 11.

<!--Device-RichTextAttribute-onComplete(callback: () => void): RichTextAttribute--><!--Device-RichTextAttribute-onComplete(callback: () => void): RichTextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | () =&gt; void | Yes |  |

## onStart

```TypeScript
onStart(callback: () => void)
```

Triggered when the RichText loading starts.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11 - 11.

<!--Device-RichTextAttribute-onStart(callback: () => void): RichTextAttribute--><!--Device-RichTextAttribute-onStart(callback: () => void): RichTextAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | () =&gt; void | Yes |  |
