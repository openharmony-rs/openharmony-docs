# @ohos.util.PlainArray(Nonlinear Container PlainArray)

PlainArray stores key-value (KV) pairs. Each key must be unique, be of the number type, and have only one value.
 PlainArray is based on generics and uses a lightweight structure. Keys in the array are searched using binary search
 and are mapped to values in other arrays.
 Both PlainArray and [LightWeightMap](arkts-arkts-util-lightweightmap-lightweightmap-c.md) are used to store KV pairs in the lightweight
 structure. However, the keys of PlainArray can only be of the number type.
 **Recommended use case**: Use PlainArray when you need to store KV pairs whose keys are of the **number** type.
 This topic uses the following to identify the use of generics:

- T: Type

> **NOTE**
 >
 > Container classes, implemented in static languages, have restrictions on storage locations and properties, and do
 > not support custom properties or methods.



## Modules to Import

```TypeScript
import { PlainArray } from '@kit.ArkTS';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [PlainArray](arkts-arkts-util-plainarray-plainarray-c.md) | PlainArray stores key-value (KV) pairs. Each key must be unique, be of the number type, and have only one value. PlainArray is based on generics and uses a lightweight structure. |
