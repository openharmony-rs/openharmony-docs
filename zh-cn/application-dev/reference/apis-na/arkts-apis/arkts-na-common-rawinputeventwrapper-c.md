# RawInputEventWrapper

Defines the raw input event wrapper.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class RawInputEventWrapper--><!--Device-unnamed-export declare abstract class RawInputEventWrapper-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## asKeyEvent

```TypeScript
asKeyEvent(): KeyEvent | null
```

Attempts to get the keyboard event. Returns the event object if it is a keyboard event, otherwise returns null.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RawInputEventWrapper-asKeyEvent(): KeyEvent | null--><!--Device-RawInputEventWrapper-asKeyEvent(): KeyEvent | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KeyEvent](arkts-na-common-keyevent-i.md) | The keyboard event object or null. |

## asMouseEvent

```TypeScript
asMouseEvent(): MouseEvent | null
```

Attempts to get the mouse event. Returns the event object if it is a mouse event, otherwise returns null.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RawInputEventWrapper-asMouseEvent(): MouseEvent | null--><!--Device-RawInputEventWrapper-asMouseEvent(): MouseEvent | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MouseEvent](arkts-na-common-mouseevent-i.md) | The mouse event object or null. |

## asTouchEvent

```TypeScript
asTouchEvent(): TouchEvent | null
```

Attempts to get the touch event. Returns the event object if it is a touch event, otherwise returns null.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RawInputEventWrapper-asTouchEvent(): TouchEvent | null--><!--Device-RawInputEventWrapper-asTouchEvent(): TouchEvent | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TouchEvent](arkts-na-common-touchevent-i.md) | The touch event object or null. |

## isKeyEvent

```TypeScript
isKeyEvent(): boolean
```

Checks whether the event is a keyboard event.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RawInputEventWrapper-isKeyEvent(): boolean--><!--Device-RawInputEventWrapper-isKeyEvent(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the event is a keyboard event, otherwise returns false. |

## isMouseEvent

```TypeScript
isMouseEvent(): boolean
```

Checks whether the event is a mouse event.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RawInputEventWrapper-isMouseEvent(): boolean--><!--Device-RawInputEventWrapper-isMouseEvent(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the event is a mouse event, otherwise returns false. |

## isTouchEvent

```TypeScript
isTouchEvent(): boolean
```

Checks whether the event is a touch event.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RawInputEventWrapper-isTouchEvent(): boolean--><!--Device-RawInputEventWrapper-isTouchEvent(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns true if the event is a touch event, otherwise returns false. |

