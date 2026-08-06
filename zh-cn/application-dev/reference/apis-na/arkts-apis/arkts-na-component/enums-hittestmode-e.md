# HitTestMode

Defines the hit test mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum HitTestMode--><!--Device-unnamed-export declare enum HitTestMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Default

```TypeScript
Default = 0
```

Both self and children nodes respond to the hit test for touch events, but block hit test of the other nodes which is masked by this node.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HitTestMode-Default = 0--><!--Device-HitTestMode-Default = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Block

```TypeScript
Block = 1
```

Self respond to the hit test for touch events, but block hit test of children and other nodes which is masked by this node.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HitTestMode-Block = 1--><!--Device-HitTestMode-Block = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Transparent

```TypeScript
Transparent = 2
```

Self and children respond to the hit test for touch events, and allow hit test of other nodes which is masked by this node.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HitTestMode-Transparent = 2--><!--Device-HitTestMode-Transparent = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None = 3
```

Self not respond to the hit test for touch events, but children respond to the hit test for touch events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HitTestMode-None = 3--><!--Device-HitTestMode-None = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BLOCK_HIERARCHY

```TypeScript
BLOCK_HIERARCHY = 4
```

Blocks all lower-priority siblings and parent nodes from receiving the event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HitTestMode-BLOCK_HIERARCHY = 4--><!--Device-HitTestMode-BLOCK_HIERARCHY = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BLOCK_DESCENDANTS

```TypeScript
BLOCK_DESCENDANTS = 5
```

Self not respond to the hit test for touch events, and all descendants (children, grandchildren, etc.) not respond to the hit test for touch events too.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HitTestMode-BLOCK_DESCENDANTS = 5--><!--Device-HitTestMode-BLOCK_DESCENDANTS = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

