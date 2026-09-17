# @ohos.util.Deque(Linear Container Deque)

Double-Ended Queue (Deque) is a data structure implemented based on a circular queue. It supports insertion and
 deletion of elements at both ends. It follows the principles of First In First Out (FIFO) and Last In First Out (LIFO
 ). Deque can dynamically adjust the capacity based on project requirements. It doubles the capacity each time.
 Queue allows element removal at the front and insertion at the rear. Compared with [Queue](arkts-arkts-util-queue-queue-c.md),
 which only allows element deletion at the front and insertion at the back, Deque permits insertion and deletion at
 both ends.
 Both [ArrayList](arkts-arkts-util-arraylist-arraylist-c.md) and Deque support insertion and deletion at the ends, but Deque does not
 support insertion in the middle. Deque is more efficient than an ArrayList for inserting and deleting elements at the
 front, whereas an ArrayList excels in element access efficiency.
 **Recommended use case**: Use **Deque** when you need to frequently insert or remove elements at both the ends of a
 container.
 This topic uses the following to identify the use of generics:

- T: Type

> **NOTE**
 >
 > - Container classes, implemented in static languages, have restrictions on storage locations and properties, and do
 > not support custom properties or methods.



## Modules to Import

```TypeScript
import { Deque } from '@kit.ArkTS';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Deque](arkts-arkts-util-deque-deque-c.md) | Double-ended queue (deque) is a sequence container implemented based on the queue data structure that follows the principles of First In First Out (FIFO) and Last In First Out (LIFO). It allows insertion and removal of elements at both the ends. |
