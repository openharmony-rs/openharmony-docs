# BuilderSpanInfo

```TypeScript
declare interface BuilderSpanInfo
```

Defines the identity and position information of a BuilderSpan in **RichEditor**.

> **NOTE:** 
> 
> This interface is not supported when the **RichEditor** component is constructed with
> [RichEditorStyledStringOptions](arkts-arkui-richeditor-comp-richeditorstyledstringoptions-i.md).

**Since:** 26.2.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

Developer-defined tracking identifier for tracking BuilderSpan. The framework does not enforce uniqueness constraints; developers are responsible for ensuring uniqueness. When not provided, the value is **undefined**.

**Type:** string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

Current offset position of the BuilderSpan in the text content. This value is maintained by the framework and dynamically updated as text content changes.

**Type:** number

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
