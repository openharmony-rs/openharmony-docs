# @ohos.util.List(Linear Container List)

List is implemented based on the singly linked list. Each node has a reference pointing to the next element. Elements
 must be traversed from the beginning, making querying inefficient. However, insertion and deletion operations are
 highly efficient. List allows null elements.
 Unlike [LinkedList](arkts-arkts-util-linkedlist-linkedlist-c.md), which is a doubly linked list, List is a singly linked list that
 does not support insertion or removal at both ends.

> **NOTE**
 >
 > Accessing elements in a List using the \[index\] syntax may lead to undefined results. You are advised to use
 > **get()** instead.
 > **Recommended use case**: Use List for frequent insertion and removal operations when a singly linked list is
 > required.
 > This topic uses the following to identify the use of generics:

- T: Type

> **NOTE**
 >
 > - Container classes, implemented in static languages, have restrictions on storage locations and properties, and do
 > not support custom properties or methods.



## Modules to Import

```TypeScript
import { List } from '@kit.ArkTS';
import { ListComparatorFn } from '@kit.ArkTS';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [List](arkts-arkts-util-list-list-c.md) | List is implemented based on the singly linked list. Each node has a reference pointing to the next element. When querying an element, the system traverses the list from the beginning. |

### Types

| Name | Description |
| --- | --- |
| [ListComparatorFn](arkts-arkts-listcomparatorfn-t.md) | This type specifies the comparator of sort in comparation. |
