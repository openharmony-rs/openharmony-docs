# SelectionChangeCallback

```TypeScript
export type SelectionChangeCallback = (oldBegin: int, oldEnd: int, newBegin: int, newEnd: int) => void
```

文本选择范围变化（selectionChange）事件的回调函数类型，用于定义该事件触发时执行的回调函数格式。

**起始版本：** 23

<!--Device-inputMethodEngine-export type SelectionChangeCallback = (oldBegin: int, oldEnd: int, newBegin: int, newEnd: int) => void--><!--Device-inputMethodEngine-export type SelectionChangeCallback = (oldBegin: int, oldEnd: int, newBegin: int, newEnd: int) => void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldBegin | int | 是 | oldBegin为变化前被选中文本的起始下标。 |
| oldEnd | int | 是 | oldEnd为变化前被选中文本的终止下标。 |
| newBegin | int | 是 | newBegin为变化后被选中文本的起始下标。 |
| newEnd | int | 是 | newEnd为变化后被选中文本的终止下标。 |

