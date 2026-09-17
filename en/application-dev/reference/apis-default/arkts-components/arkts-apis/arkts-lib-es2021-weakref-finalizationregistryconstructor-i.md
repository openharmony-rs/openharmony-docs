# FinalizationRegistryConstructor

## Modules to Import

```TypeScript
```

## [[Construct]]

```TypeScript
new<T>(cleanupCallback: (heldValue: T) => void): FinalizationRegistry<T>
```

Creates a finalization registry with an associated cleanup callback

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cleanupCallback | (heldValue: T) =&gt; void | Yes |  |

## prototype

```TypeScript
readonly prototype: FinalizationRegistry<any>
```

**Type:** [FinalizationRegistry](arkts-lib-es2021-weakref-finalizationregistry-i.md)&lt;any&gt;
