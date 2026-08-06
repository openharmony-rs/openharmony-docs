# MenuKeyboardAvoidMode

Define the mode of menu how to avoid keyboard.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum MenuKeyboardAvoidMode--><!--Device-unnamed-export declare enum MenuKeyboardAvoidMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

Menu will not avoid keyboard.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuKeyboardAvoidMode-NONE = 0--><!--Device-MenuKeyboardAvoidMode-NONE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TRANSLATE_AND_RESIZE

```TypeScript
TRANSLATE_AND_RESIZE = 1
```

First menu will avoid keyboard by changing its placement. And then menu will avoid by resizing height when new placement is still not high enough.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuKeyboardAvoidMode-TRANSLATE_AND_RESIZE = 1--><!--Device-MenuKeyboardAvoidMode-TRANSLATE_AND_RESIZE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

