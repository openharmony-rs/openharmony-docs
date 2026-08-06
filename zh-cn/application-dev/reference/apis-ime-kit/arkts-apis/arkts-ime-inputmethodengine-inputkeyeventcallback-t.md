# InputKeyEventCallback

```TypeScript
export type InputKeyEventCallback = (event: InputKeyEvent) => boolean
```

按键事件（keyEvent）的回调函数类型，用于定义keyEvent事件触发时执行的回调函数格式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-inputMethodEngine-export type InputKeyEventCallback = (event: InputKeyEvent) => boolean--><!--Device-inputMethodEngine-export type InputKeyEventCallback = (event: InputKeyEvent) => boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | InputKeyEvent | 是 | 输入按键事件对象，包含按键编码、事件类型、触发时间等按键事件相关信息。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否消费该按键事件：返回true表示消费此事件，系统不再向下传递该事件；返回false表示不消费此事件，系统将继续处理该事件。 |

