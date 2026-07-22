# RawInputEventWrapper

原始输入事件包装器类。

提供统一的接口来访问不同类型的输入事件，确保类型安全和向后兼容性。

此类封装了原始的MouseEvent、TouchEvent或KeyEvent对象，并通过类型安全的方法访问。

此类为抽象类，开发者无法自行创建实例。系统会在触发输入事件监听器时自动创建实例并传递回调函数。
> **说明：**  
>  
> 由于监听器在事件派发给具体组件之前执行，事件中的一些字段将无法提供有效值：如触发对象[target](arkts-arkui-eventtarget-i.md)、相对于组件的坐标  
> [x](arkts-arkui-mouseevent-i.md#x)和[y](arkts-arkui-mouseevent-i.md#y)、[getCurrentLocalPosition](arkts-arkui-touchobject-i.md#getcurrentlocalposition)和  
> [stopPropagation](arkts-arkui-touchevent-i.md#stoppropagation)方法、TouchEvent的[preventDefault](arkts-arkui-touchevent-i.md#preventdefault)和  
> [getHistoricalPoints](arkts-arkui-touchevent-i.md#gethistoricalpoints)方法以及KeyEvent的[metaKey](arkts-arkui-keyevent-i.md#metakey)属性和  
> [getModifierKeyState](arkts-arkui-keyevent-i.md#getmodifierkeystate)方法。

**起始版本：** 26.0.0

<!--Device-unnamed-declare abstract class RawInputEventWrapper--><!--Device-unnamed-declare abstract class RawInputEventWrapper-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## asKeyEvent

```TypeScript
asKeyEvent(): KeyEvent | null
```

获取按键事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RawInputEventWrapper-asKeyEvent(): KeyEvent | null--><!--Device-RawInputEventWrapper-asKeyEvent(): KeyEvent | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md) | Key event object if it is a key event, or **null** otherwise. |

## asMouseEvent

```TypeScript
asMouseEvent(): MouseEvent | null
```

获取鼠标事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RawInputEventWrapper-asMouseEvent(): MouseEvent | null--><!--Device-RawInputEventWrapper-asMouseEvent(): MouseEvent | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MouseEvent](arkts-arkui-mouseevent-i.md) | Mouse event object if it is a mouse event, or **null** otherwise. |

## asTouchEvent

```TypeScript
asTouchEvent(): TouchEvent | null
```

获取触摸事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RawInputEventWrapper-asTouchEvent(): TouchEvent | null--><!--Device-RawInputEventWrapper-asTouchEvent(): TouchEvent | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TouchEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-touchevent-touchevent-i.md) | Touch event object if it is a touch event, or **null** otherwise. |

## isKeyEvent

```TypeScript
isKeyEvent(): boolean
```

判断是否为按键事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RawInputEventWrapper-isKeyEvent(): boolean--><!--Device-RawInputEventWrapper-isKeyEvent(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断是否为按键事件，如果是按键事件则返回true，否则返回false。 |

## isMouseEvent

```TypeScript
isMouseEvent(): boolean
```

判断是否为鼠标事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RawInputEventWrapper-isMouseEvent(): boolean--><!--Device-RawInputEventWrapper-isMouseEvent(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断是否为鼠标事件，如果是鼠标事件则返回true，否则返回false。 |

## isTouchEvent

```TypeScript
isTouchEvent(): boolean
```

判断是否为触摸事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RawInputEventWrapper-isTouchEvent(): boolean--><!--Device-RawInputEventWrapper-isTouchEvent(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断是否为触摸事件，如果是触摸事件则返回true，否则返回false。 |

