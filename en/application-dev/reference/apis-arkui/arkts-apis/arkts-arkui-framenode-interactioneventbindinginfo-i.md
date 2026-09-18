# InteractionEventBindingInfo

Describes the binding state of interaction events on components. When querying reveals an interaction event bound to the current node, this object provides detailed event binding information.

**Since:** 19

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## baseEventRegistered

```TypeScript
baseEventRegistered: boolean
```

Whether the event is bound declaratively.

**true** means that the event is bound declaratively, and **false** means the opposite.

**Type:** boolean

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builtInEventRegistered

```TypeScript
builtInEventRegistered: boolean
```

Whether the component has built-in events (events that are defined internally by the component and do not require manual binding).

The value **true** means that the component has built-in events, and **false** means the opposite.

**Type:** boolean

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## nativeEventRegistered

```TypeScript
nativeEventRegistered: boolean
```

Whether the event is bound through node event registration ([registerNodeEvent](../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)).

The value **true** means that the event is bound through node event registration, and **false** means the opposite.

**Type:** boolean

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## nodeEventRegistered

```TypeScript
nodeEventRegistered: boolean
```

Whether the event is bound through a custom component node. For the implementation example, see [Basic Event Example](../../../reference/apis-arkui/js-apis-arkui-frameNode.md#basic-event-example).

The value **true** means that the event is bound through a custom component node, and **false** means the opposite.

**Type:** boolean

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
