# CollectionType

```TypeScript
export declare type CollectionType<S> = Array<S> | Map<string | number, S> |
  Set<S> | collections.Array<S> | collections.Map<string | number, S> | collections.Set<S>
```

Defines the types of persistent collection data supported by **globalConnect** using the generic type of the input parameter of **globalConnect**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| Array&lt;S&gt; | The value is of the array type. |
| Map&lt;string |  |
| number, S&gt; |  |
| Set&lt;S&gt; | The value is of the Set type. |
| collections.Array&lt;S&gt; | The value is of the collections.Array type. |
| collections.Map&lt;string |  |
| number, S&gt; |  |
| collections.Set&lt;S&gt; | The value is of the collections.Set type. |
