# BuilderCallback

```TypeScript
declare type BuilderCallback<Args extends Object[] = any[]> = (...args: Args) => void
```

Defines the callback type used in mutableBuilder.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| args | Args | Yes | The parameter of MutableBuilder. |
