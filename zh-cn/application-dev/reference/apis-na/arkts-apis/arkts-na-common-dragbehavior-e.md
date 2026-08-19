# DragBehavior

Enum for Drag Behavior. &lt;strong&gt;NOTE&lt;/strong&gt;:<br> DragBehavior serves to inform you about the intended method of data handling, whether it's a copy or a move, but it does not actually dictate the real processing of the data.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum DragBehavior--><!--Device-unnamed-export declare enum DragBehavior-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COPY

```TypeScript
COPY = 0
```

If drag use copy event, then set DragBehavior.COPY.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragBehavior-COPY = 0--><!--Device-DragBehavior-COPY = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MOVE

```TypeScript
MOVE = 1
```

If drag use move event, then set DragBehavior.MOVE.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragBehavior-MOVE = 1--><!--Device-DragBehavior-MOVE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

