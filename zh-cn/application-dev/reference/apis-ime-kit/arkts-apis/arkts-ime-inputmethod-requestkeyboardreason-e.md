# RequestKeyboardReason

请求键盘输入的原因。

**起始版本：** 15

<!--Device-inputMethod-export enum RequestKeyboardReason--><!--Device-inputMethod-export enum RequestKeyboardReason-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## NONE

```TypeScript
NONE = 0
```

表示没有特定的原因触发键盘请求。

**使用场景：**默认值，不指定特定触发原因时使用。

**起始版本：** 15

<!--Device-RequestKeyboardReason-NONE = 0--><!--Device-RequestKeyboardReason-NONE = 0-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## MOUSE

```TypeScript
MOUSE = 1
```

表示键盘请求是由鼠标操作触发的。

**使用场景：**用户通过鼠标点击编辑框触发键盘弹出时使用。

**起始版本：** 15

<!--Device-RequestKeyboardReason-MOUSE = 1--><!--Device-RequestKeyboardReason-MOUSE = 1-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## TOUCH

```TypeScript
TOUCH = 2
```

表示键盘请求是由触摸操作触发的。

**使用场景：**用户通过触摸点击编辑框触发键盘弹出时使用。

**起始版本：** 15

<!--Device-RequestKeyboardReason-TOUCH = 2--><!--Device-RequestKeyboardReason-TOUCH = 2-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## OTHER

```TypeScript
OTHER = 20
```

表示键盘请求是由其他原因触发的。

**使用场景：**键盘弹出的触发原因不属于鼠标和触摸时使用。

**起始版本：** 15

<!--Device-RequestKeyboardReason-OTHER = 20--><!--Device-RequestKeyboardReason-OTHER = 20-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

