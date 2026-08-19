# KeyEventCallback

```TypeScript
export type KeyEventCallback = (event: KeyEvent) => boolean
```

按键按下（keyDown）或按键抬起（keyUp）事件的回调函数类型，用于定义这两类按键事件触发时执行的回调函数格式。

**起始版本：** 23

<!--Device-inputMethodEngine-export type KeyEventCallback = (event: KeyEvent) => boolean--><!--Device-inputMethodEngine-export type KeyEventCallback = (event: KeyEvent) => boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | KeyEvent | 是 | 按键事件对象，包含按键码、按键类型、事件时间等按键相关信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否消费该按键事件：返回true表示消费，系统不再向下传递该事件；返回false表示不消费，系统继续处理该事件。 |

