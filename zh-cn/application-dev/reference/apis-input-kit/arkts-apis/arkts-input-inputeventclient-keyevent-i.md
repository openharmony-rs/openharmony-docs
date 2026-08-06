# KeyEvent

按键注入描述信息。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-inputEventClient-interface KeyEvent--><!--Device-inputEventClient-interface KeyEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## isIntercepted

```TypeScript
isIntercepted: boolean
```

按键是否可以被拦截。 true表示可以被拦截，false表示不可被拦截。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-KeyEvent-isIntercepted: boolean--><!--Device-KeyEvent-isIntercepted: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## isPressed

```TypeScript
isPressed: boolean
```

按键是否按下。 true表示按键按下，false表示按键抬起。

**类型：** boolean

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-KeyEvent-isPressed: boolean--><!--Device-KeyEvent-isPressed: boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## keyCode

```TypeScript
keyCode: int
```

按键键值。当前仅支持返回键/KEYCODE\_BACK键。

**类型：** int

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-KeyEvent-keyCode: int--><!--Device-KeyEvent-keyCode: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

## keyDownDuration

```TypeScript
keyDownDuration: int
```

按键按下持续时间，单位为微秒（μs）。

**类型：** int

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-KeyEvent-keyDownDuration: int--><!--Device-KeyEvent-keyDownDuration: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

