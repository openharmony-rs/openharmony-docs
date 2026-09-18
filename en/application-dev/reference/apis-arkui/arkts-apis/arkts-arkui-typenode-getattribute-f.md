# getAttribute

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Text'): TextAttribute | undefined
```

Obtains the attributes of a **Text** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Text' | Yes | Node type. Set to **'Text'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextAttribute](../arkts-components/arkts-arkui-text-comp-attribute.md) &#124; undefined | Attributes of the **Text** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Column'): ColumnAttribute | undefined
```

Obtains the attributes of a **Column** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Column' | Yes | Node type. Set to **'Column'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColumnAttribute](../arkts-components/arkts-arkui-column-comp-attribute.md) &#124; undefined | Attributes of the **Column** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Row'): RowAttribute | undefined
```

Obtains the attributes of a **Row** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Row' | Yes | Node type. Set to **'Row'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [RowAttribute](../arkts-components/arkts-arkui-row-comp-attribute.md) &#124; undefined | Attributes of the **Row** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Stack'): StackAttribute | undefined
```

Obtains the attributes of a **Stack** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Stack' | Yes | Node type. Set to **'Stack'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [StackAttribute](../arkts-components/arkts-arkui-stack-comp-attribute.md) &#124; undefined | Attributes of the **Stack** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Flex'): FlexAttribute | undefined
```

Obtains the Flex node attributes. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Flex' | Yes | Flex node type. |

**Return value:**

| Type | Description |
| --- | --- |
| [FlexAttribute](../arkts-components/arkts-arkui-flex-comp-attribute.md) &#124; undefined | Flex node type. If the operation fails, undefined is returned. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Swiper'): SwiperAttribute | undefined
```

Obtains the attributes of a **Swiper** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Swiper' | Yes | Node type. Set to **'Swiper'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [SwiperAttribute](../arkts-components/arkts-arkui-swiper-comp-attribute.md) &#124; undefined | Properties of the **Swiper** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Progress'): ProgressAttribute | undefined
```

Obtains the attributes of a **Progress** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Progress' | Yes | Node type. Set to **'Progress'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ProgressAttribute](../arkts-components/arkts-arkui-progress-comp-attribute.md) &#124; undefined | Properties of the **Progress** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
function getAttribute(node: FrameNode, nodeType: 'Scroll'): ScrollAttribute | undefined
```

Obtains the attributes of a **Scroll** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Scroll' | Yes | Node type. Set to **'Scroll'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ScrollAttribute](../arkts-components/arkts-arkui-scroll-comp-attribute.md) &#124; undefined | Attributes of the **Scroll** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'RelativeContainer'): RelativeContainerAttribute | undefined
```

Obtains the attributes of a **RelativeContainer** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'RelativeContainer' | Yes | Node type. Set to **'RelativeContainer'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [RelativeContainerAttribute](../arkts-components/arkts-arkui-relativecontainer-comp-attribute.md) &#124; undefined | Attributes of the **RelativeContainer** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'LoadingProgress'): LoadingProgressAttribute | undefined
```

Obtains the attributes of a LoadingProgress node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'LoadingProgress' | Yes | Node type. Set to **'LoadingProgress'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [LoadingProgressAttribute](../arkts-components/arkts-arkui-loadingprogress-comp-attribute.md) &#124; undefined | Properties of the **LoadingProgress** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Image'): ImageAttribute | undefined
```

Obtains the attributes of an **Image** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Image' | Yes | Node type. Set to **'Image'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageAttribute](../arkts-components/arkts-arkui-image-comp-attribute.md) &#124; undefined | Properties of the **Image** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'List'): ListAttribute | undefined
```

Obtains the attributes of a **List** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'List' | Yes | Node type. Set to **'List'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ListAttribute](../arkts-components/arkts-arkui-list-comp-attribute.md) &#124; undefined | Attributes of the **List** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'ListItem'): ListItemAttribute | undefined
```

Obtains the attributes of a **ListItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'ListItem' | Yes | Node type. Set to **'ListItem'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ListItemAttribute](../arkts-components/arkts-arkui-listitem-comp-attribute.md) &#124; undefined | Attributes of the **ListItem** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'TextInput'): TextInputAttribute | undefined
```

Obtains the attributes of a **TextInput** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'TextInput' | Yes | Node type. Set to **'TextInput'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextInputAttribute](../arkts-components/arkts-arkui-textinput-comp-attribute.md) &#124; undefined | Properties of the **TextInput** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Button'): ButtonAttribute | undefined
```

Obtains the attributes of a **Button** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Button' | Yes | Node type. Set to **'Button'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ButtonAttribute](../arkts-components/arkts-arkui-button-comp-attribute.md) &#124; undefined | Attributes of the **Button** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'ListItemGroup'): ListItemGroupAttribute | undefined
```

Obtains the attributes of a **ListItemGroup** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'ListItemGroup' | Yes | Node type. Set to **'ListItemGroup'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ListItemGroupAttribute](../arkts-components/arkts-arkui-listitemgroup-comp-attribute.md) &#124; undefined | Attributes of the **ListItemGroup** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'WaterFlow'): WaterFlowAttribute | undefined
```

Obtains the attributes of a **WaterFlow** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'WaterFlow' | Yes | Node type. Set to **'WaterFlow'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [WaterFlowAttribute](../arkts-components/arkts-arkui-waterflow-comp-attribute.md) &#124; undefined | Properties of the **WaterFlow** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'FlowItem'): FlowItemAttribute | undefined
```

Obtains the attributes of a **FlowItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'FlowItem' | Yes | Node type. Set to **'FlowItem'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [FlowItemAttribute](../arkts-components/arkts-arkui-flowitem-comp-attribute.md) &#124; undefined | Properties of the **FlowItem** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'XComponent'): XComponentAttribute | undefined
```

Obtain the attributes of an **XComponent** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'XComponent' | Yes | Node type. Set to **'XComponent'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [XComponentAttribute](../arkts-components/arkts-arkui-xcomponent-comp-attribute.md) &#124; undefined | Properties of the **XComponent** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Checkbox'): CheckboxAttribute | undefined
```

Obtains the attributes of a **Checkbox** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Checkbox' | Yes | Node type. Set to **'Checkbox'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [CheckboxAttribute](../arkts-components/arkts-arkui-checkbox-comp-attribute.md) &#124; undefined | Attributes of the **Checkbox** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Radio'): RadioAttribute | undefined
```

Obtains the attributes of a **Radio** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Radio' | Yes | Node type. Set to **'Radio'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [RadioAttribute](../arkts-components/arkts-arkui-radio-comp-attribute.md) &#124; undefined | Properties of the **Radio** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Slider'): SliderAttribute | undefined
```

Obtains the attributes of a **Slider** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Slider' | Yes | Node type. Set to **'Slider'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [SliderAttribute](../arkts-components/arkts-arkui-slider-comp-attribute.md) &#124; undefined | Properties of the **Slider** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Toggle'): ToggleAttribute | undefined
```

Obtains the attributes of a **Toggle** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Toggle' | Yes | Node type. Set to **'Toggle'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [ToggleAttribute](../arkts-components/arkts-arkui-toggle-comp-attribute.md) &#124; undefined | Properties of the **Toggle** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'TextArea'): TextAreaAttribute | undefined
```

Obtains the attributes of a **TextArea** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'TextArea' | Yes | Node type. Set to **'TextArea'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextAreaAttribute](../arkts-components/arkts-arkui-textarea-comp-attribute.md) &#124; undefined | Properties of the **TextArea** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Grid'): GridAttribute | undefined
```

Obtains the attributes of a **Grid** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'Grid' | Yes | Node type. Set to **'Grid'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [GridAttribute](../arkts-components/arkts-arkui-grid-comp-attribute.md) &#124; undefined | Properties of the **Grid** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'GridItem'): GridItemAttribute | undefined
```

Obtains the attributes of a **GridItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | Yes | Target node from which to obtain attributes. |
| nodeType | 'GridItem' | Yes | Node type. Set to **'GridItem'**. |

**Return value:**

| Type | Description |
| --- | --- |
| [GridItemAttribute](../arkts-components/arkts-arkui-griditem-comp-attribute.md) &#124; undefined | Properties of the **GridItem** node, or **undefined** if they fail to be obtained. |
