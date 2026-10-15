# getEvent

<a id="getevent1"></a>

## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'Scroll'): UIScrollEvent | undefined
```

Obtains the **UIScrollEvent** object held by the **Scroll** node, which is used to set scroll events. If the node is not created via ArkTS, whether cross-language access is supported must be set. If cross-language access is not supported, **undefined** is returned. This API does not support nodes created in a declarative manner. The scroll events set through this API coexist with declaratively defined events. The set scroll events do not override the original declarative events. When both event callbacks are set, the declarative event callback takes precedence.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'Scroll'): UIScrollEvent | undefined--><!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'Scroll'): UIScrollEvent | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node. |
| nodeType | 'Scroll' | Yes | **Scroll** node type for scroll event configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| [UIScrollEvent](../arkts-components/arkts-arkui-scroll-comp-uiscrollevent-i.md) &#124; undefined | **UIScrollEvent** object for the **Scroll** node, or **undefined** if it fails to be obtained. |

**Examples**

See Scroll Event Example.


<a id="getevent2"></a>

## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'List'): UIListEvent | undefined
```

Obtains the **UIListEvent** object held by the **List** node, which is used to set scroll events. If the node is not created via ArkTS, whether cross-language access is supported must be set. If cross-language access is not supported, **undefined** is returned. This API does not support nodes created in a declarative manner. The scroll events set through this API coexist with declaratively defined events. The set scroll events do not override the original declarative events. When both event callbacks are set, the declarative event callback takes precedence.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'List'): UIListEvent | undefined--><!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'List'): UIListEvent | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node. |
| nodeType | 'List' | Yes | **List** node type for scroll event configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| [UIListEvent](../arkts-components/arkts-arkui-list-comp-uilistevent-i.md) &#124; undefined | **UIListEvent** object for the **List** node, or **undefined** if it fails to be obtained. |

**Examples**

See Scroll Event Example.


<a id="getevent3"></a>

## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'WaterFlow'): UIWaterFlowEvent | undefined
```

Obtains the **UIWaterFlowEvent** object held by the [WaterFlow](arkts-arkui-typenode-waterflow-t.md) node, which is used to set scroll events. If the node is not created via ArkTS, whether cross-language access is supported must be set. If cross-language access is not supported, **undefined** is returned. This API does not support nodes created in a declarative manner. The scroll events set through this API coexist with declaratively defined events. The set scroll events do not override the original declarative events. When both event callbacks are set, the declarative event callback takes precedence.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'WaterFlow'): UIWaterFlowEvent | undefined--><!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'WaterFlow'): UIWaterFlowEvent | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node. |
| nodeType | 'WaterFlow' | Yes | **WaterFlow** node type for scroll event configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| [UIWaterFlowEvent](../arkts-components/arkts-arkui-waterflow-comp-uiwaterflowevent-i.md) &#124; undefined | **UIWaterFlowEvent** object for the **WaterFlow** node, or **undefined** if it fails to be obtained. |

**Examples**

See Scroll Event Example.


<a id="getevent4"></a>

## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'Grid'): UIGridEvent | undefined
```

Obtains the **UIGridEvent** object held by the **Grid** node, which is used to set scroll events. If the node is not created via ArkTS, whether cross-language access is supported must be set. If cross-language access is not supported, **undefined** is returned. This API does not support nodes created in a declarative manner. The scroll events set through this API coexist with declaratively defined events. The set scroll events do not override the original declarative events. When both event callbacks are set, the declarative event callback takes precedence.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'Grid'): UIGridEvent | undefined--><!--Device-typeNode-function getEvent(node: FrameNode, nodeType: 'Grid'): UIGridEvent | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node. |
| nodeType | 'Grid' | Yes | **Grid** node type for scroll event configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| [UIGridEvent](../arkts-components/arkts-arkui-grid-comp-uigridevent-i.md) &#124; undefined | **UIGridEvent** object for the **Grid** node, or **undefined** if it fails to be obtained. |

**Examples**

See Scroll Event Example.
