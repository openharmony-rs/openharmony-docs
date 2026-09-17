# Nullable

```TypeScript
declare type Nullable<T> = T | undefined
```

This type allows for an object of a custom type or **undefined**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| T | The object can be of any custom type. |
| undefined | The object can be **undefined**. |
