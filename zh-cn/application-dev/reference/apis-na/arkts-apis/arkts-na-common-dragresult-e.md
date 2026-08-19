# DragResult

Enum for Drag Result.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum DragResult--><!--Device-unnamed-export declare enum DragResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## UNKNOWN

```TypeScript
UNKNOWN = -1
```

If the drag is not finished and the result is not set by receiver, return DragResult.UNKNOWN.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragResult-UNKNOWN = -1--><!--Device-DragResult-UNKNOWN = -1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DRAG_SUCCESSFUL

```TypeScript
DRAG_SUCCESSFUL = 0
```

If the drag is successful, return DragResult.DRAG_SUCCESSFUL.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragResult-DRAG_SUCCESSFUL = 0--><!--Device-DragResult-DRAG_SUCCESSFUL = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DRAG_FAILED

```TypeScript
DRAG_FAILED = 1
```

If drag fail, return DragResult.DRAG_FAILED.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragResult-DRAG_FAILED = 1--><!--Device-DragResult-DRAG_FAILED = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DRAG_CANCELED

```TypeScript
DRAG_CANCELED = 2
```

If drag action cancel, return DragResult.DRAG_CANCELED.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragResult-DRAG_CANCELED = 2--><!--Device-DragResult-DRAG_CANCELED = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DROP_ENABLED

```TypeScript
DROP_ENABLED = 3
```

If node allow drop in, return DragResult.DROP_ENABLED.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragResult-DROP_ENABLED = 3--><!--Device-DragResult-DROP_ENABLED = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DROP_DISABLED

```TypeScript
DROP_DISABLED = 4
```

If node don't allow drop in, return DragResult.DROP_DISABLED.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragResult-DROP_DISABLED = 4--><!--Device-DragResult-DROP_DISABLED = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

