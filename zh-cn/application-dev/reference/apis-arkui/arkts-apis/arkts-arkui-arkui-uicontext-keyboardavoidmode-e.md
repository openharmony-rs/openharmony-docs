# KeyboardAvoidMode

```TypeScript
export const enum KeyboardAvoidMode
```

配置键盘弹出时页面的避让模式。

**起始版本：** 11

<!--Device-unnamed-export const enum KeyboardAvoidMode--><!--Device-unnamed-export const enum KeyboardAvoidMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 4
```

不避让键盘。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

<!--Device-KeyboardAvoidMode-NONE = 4--><!--Device-KeyboardAvoidMode-NONE = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSET

```TypeScript
OFFSET = 0
```

上抬模式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-KeyboardAvoidMode-OFFSET = 0--><!--Device-KeyboardAvoidMode-OFFSET = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSET_WITH_CARET

```TypeScript
OFFSET_WITH_CARET = 2
```

上抬模式，输入框光标位置发生变化时也会触发避让。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

<!--Device-KeyboardAvoidMode-OFFSET_WITH_CARET = 2--><!--Device-KeyboardAvoidMode-OFFSET_WITH_CARET = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RESIZE

```TypeScript
RESIZE = 1
```

压缩模式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-KeyboardAvoidMode-RESIZE = 1--><!--Device-KeyboardAvoidMode-RESIZE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_WITH_CARET

```TypeScript
RESIZE_WITH_CARET = 3
```

压缩模式，输入框光标位置发生变化时也会触发避让。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

<!--Device-KeyboardAvoidMode-RESIZE_WITH_CARET = 3--><!--Device-KeyboardAvoidMode-RESIZE_WITH_CARET = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
