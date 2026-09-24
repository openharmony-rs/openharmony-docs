# getEvent

## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'Scroll'): UIScrollEvent | undefined
```

Obtains the **UIScrollEvent** object associated with the **Scroll** node for configuring scroll events. The scroll events configured through this API coexist with declarative events without overriding them. If both event callbacks are registered, the declaratively defined event callback takes precedence.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

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


<a id="getevent-1"></a>

## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'List'): UIListEvent | undefined
```

Obtains the **UIListEvent** object associated with the **List** node for configuring scroll events. The scroll events configured through this API coexist with declarative events without overriding them. If both event callbacks are registered, the declaratively defined event callback takes precedence.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

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


<a id="getevent-2"></a>

## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'WaterFlow'): UIWaterFlowEvent | undefined
```

Obtains the **UIWaterFlowEvent** object associated with the [WaterFlow](arkts-arkui-typenode-waterflow-t.md) node for configuring scroll events. The scroll events configured through this API coexist with declarative events without overriding them. If both event callbacks are registered, the declaratively defined event callback takes precedence.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

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


<a id="getevent-3"></a>

## getEvent

```TypeScript
function getEvent(node: FrameNode, nodeType: 'Grid'): UIGridEvent | undefined
```

Obtains the **UIGridEvent** object associated with the **Grid** node for configuring scroll events. The scroll events configured through this API coexist with declarative events without overriding them. If both event callbacks are registered, the declaratively defined event callback takes precedence.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

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
