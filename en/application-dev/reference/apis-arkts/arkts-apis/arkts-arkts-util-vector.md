# @ohos.util.Vector(Linear Container Vector)

## Modules to Import

```TypeScript
import { Vector } from '@kit.ArkTS';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Vector](arkts-arkts-util-vector-vector-c.md) | Vector is a linear data structure that is implemented based on arrays. When the memory of a vector is used up, a larger contiguous memory area is automatically allocated, all the elements are copied to the new memory area, and the current memory area is reclaimed. Vector can be used to efficiently access elements. Both Vector and [ArrayList](arkts-arkts-util-arraylist-arraylist-c.md) are implemented based on arrays, but Vector provides more interfaces for operating the arrays. Both of them can dynamically adjust the capacity. Vector doubles the capacity each time, whereas ArrayList increases the capacity by 50%. **Recommended use case**: Use Vector when the data volume is large. This topic uses the following to identify the use of generics: |
