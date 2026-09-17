# @ohos.util.HashMap(Nonlinear Container HashMap)

HashMap is implemented using an array, linked lists, and red-black trees as its core, supporting efficient querying,
 insertion and deletion operations. It stores data as key-value pairs where duplicate keys are not allowed - each key
 can only map to a single value.
 HashMap is faster in accessing data than [TreeMap](arkts-arkts-util-treemap-treemap-c.md), because the former accesses the keys
 based on the hash codes, whereas the latter stores and accesses the keys in sorted order.
 [HashSet](arkts-arkts-util-hashset-hashset-c.md) is implemented based on HashMap. The input parameter of HashMap consists of
 **key** and **value**. In HashSet, only the **value** object is processed.
 **Recommended use case**: Use HashMap when you need to quickly access, remove, and insert key-value pairs.
 This topic uses the following to identify the use of generics:<br>

- K: Key<br>
 - V: Value

> **NOTE**
 >
 > Container classes, implemented in static languages, have restrictions on storage locations and properties, and do
 > not support custom properties or methods.



## Modules to Import

```TypeScript
import { HashMap } from '@kit.ArkTS';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [HashMap](arkts-arkts-util-hashmap-hashmap-c.md) | HashMap is a map implemented based on the array, linked list, and red-black tree. It provides efficient data query, insertion, and removal. The elements in a HashMap instance are mappings of key-value pairs. Each key must be unique and have only one value. |
