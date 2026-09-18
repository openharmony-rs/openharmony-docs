# RepeatArray

```TypeScript
declare type RepeatArray<T> = Array<T> | ReadonlyArray<T> | Readonly<Array<T>>
```

Defines a union type for **Repeat** data source parameters.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| Array&lt;T&gt; | Regular array type. |
| ReadonlyArray&lt;T&gt; | Read-only array type, where the array object cannot be modified. |
| Readonly&lt;Array&lt;T&gt;&gt; | Read-only array type, where the array object cannot be modified. |
