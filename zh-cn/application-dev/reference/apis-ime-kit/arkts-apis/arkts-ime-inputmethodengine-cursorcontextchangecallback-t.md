# CursorContextChangeCallback

```TypeScript
export type CursorContextChangeCallback = (x: double, y: double, height: double) => void
```

光标上下文变化（cursorContextChange）事件的回调函数类型，用于定义该事件触发时执行的回调函数格式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputMethodEngine-export type CursorContextChangeCallback = (x: double, y: double, height: double) => void--><!--Device-inputMethodEngine-export type CursorContextChangeCallback = (x: double, y: double, height: double) => void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | x为光标上端的x坐标值，单位为px |
| y | double | 是 | y为光标上端的y坐标值，单位为px。 |
| height | double | 是 | height为光标的高度值，单位为px。 |

