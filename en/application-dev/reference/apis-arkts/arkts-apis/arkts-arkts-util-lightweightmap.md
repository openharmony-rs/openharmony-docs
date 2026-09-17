# @ohos.util.LightWeightMap(Nonlinear Container LightWeightMap)

LightWeightMap stores key-value (KV) pairs. Each key must be unique and have only one value.
 LightWeightMap is based on generics and uses a lightweight structure. Its default initial capacity is 8, and it has
 the capacity doubled in each expansion.
 The keys in such a set are searched using hash values, which are stored in an array.
 Compared with [HashMap](arkts-arkts-util-hashmap-hashmap-c.md), which can also store KV pairs, LightWeightMap occupies less
 memory.
 **Recommended use case**: Use LightWeightMap when you need to store and access KV pairs.
 This topic uses the following to identify the use of generics:

- K: Key<br>
 - V: Value

> **NOTE**
 >
 > - Container classes, implemented in static languages, have restrictions on storage locations and properties, and do
 > not support custom properties or methods.



## Modules to Import

```TypeScript
import { LightWeightMap } from '@kit.ArkTS';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [LightWeightMap](arkts-arkts-util-lightweightmap-lightweightmap-c.md) | LightWeightMap stores key-value (KV) pairs. Each key must be unique and have only one value. |
