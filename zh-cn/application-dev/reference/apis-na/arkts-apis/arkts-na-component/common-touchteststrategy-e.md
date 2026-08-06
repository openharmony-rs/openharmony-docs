# TouchTestStrategy

Defines the touch test strategy object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum TouchTestStrategy--><!--Device-unnamed-export declare enum TouchTestStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Custom dispatch has no effect; the system distributes events based on the hit status of the current node.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchTestStrategy-DEFAULT = 0--><!--Device-TouchTestStrategy-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FORWARD_COMPETITION

```TypeScript
FORWARD_COMPETITION = 1
```

The specified event is forwarded to a particular child node, and the system determines whether to distribute the event to other sibling nodes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchTestStrategy-FORWARD_COMPETITION = 1--><!--Device-TouchTestStrategy-FORWARD_COMPETITION = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FORWARD

```TypeScript
FORWARD = 2
```

The specified event is forwarded to a particular child node, and the system no longer distributes the event to other sibling nodes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TouchTestStrategy-FORWARD = 2--><!--Device-TouchTestStrategy-FORWARD = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

