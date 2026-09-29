# @Entry

```TypeScript
declare const Entry: ClassDecorator & ((options?: LocalStorage | EntryOptions) => ClassDecorator)
```

A custom component decorated by \@Entry serves as the entry to a UI page and is identified by the framework as the root component of the page. It is suitable for building standalone UI pages.

In a single UI page, only one custom component decorated by \@Entry is allowed as the page entry.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const Entry: ClassDecorator & ((options?: LocalStorage | EntryOptions) => ClassDecorator)--><!--Device-unnamed-declare const Entry: ClassDecorator & ((options?: LocalStorage | EntryOptions) => ClassDecorator)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
