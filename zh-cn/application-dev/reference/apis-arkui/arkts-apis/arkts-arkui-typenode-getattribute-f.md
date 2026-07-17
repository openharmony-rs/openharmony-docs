# getAttribute

## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Text'): TextAttribute | undefined
```

获取Text节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Text'): TextAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Text'): TextAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Text' | 是 | 获取Text节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextAttribute](../arkts-components/arkts-arkui-text-attribute.md) | Attributes of the **Text** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Column'): ColumnAttribute | undefined
```

获取Column节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Column'): ColumnAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Column'): ColumnAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Column' | 是 | 获取Column节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColumnAttribute](../arkts-components/arkts-arkui-column-attribute.md) | Attributes of the **Column** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Row'): RowAttribute | undefined
```

获取Row节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Row'): RowAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Row'): RowAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Row' | 是 | 获取Row节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RowAttribute](../arkts-components/arkts-arkui-row-attribute.md) | Attributes of the **Row** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Stack'): StackAttribute | undefined
```

获取Stack节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Stack'): StackAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Stack'): StackAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Stack' | 是 | 获取Stack节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StackAttribute](../arkts-components/arkts-arkui-stack-attribute.md) | Attributes of the **Stack** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Flex'): FlexAttribute | undefined
```

获取Flex节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Flex'): FlexAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Flex'): FlexAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Flex' | 是 | 获取Flex节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FlexAttribute](../arkts-components/arkts-arkui-flex-attribute.md) | 获取Flex节点类型的属性。 If the operation fails, undefined is returned. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Swiper'): SwiperAttribute | undefined
```

获取Swiper节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Swiper'): SwiperAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Swiper'): SwiperAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Swiper' | 是 | 获取Swiper节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SwiperAttribute](../arkts-components/arkts-arkui-swiper-attribute.md) | Properties of the **Swiper** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Progress'): ProgressAttribute | undefined
```

获取Progress节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Progress'): ProgressAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Progress'): ProgressAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Progress' | 是 | 获取Progress节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ProgressAttribute](../arkts-components/arkts-arkui-progress-attribute.md) | Properties of the **Progress** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
function getAttribute(node: FrameNode, nodeType: 'Scroll'): ScrollAttribute | undefined
```

获取Scroll节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-function getAttribute(node: FrameNode, nodeType: 'Scroll'): ScrollAttribute | undefined--><!--Device-typeNode-function getAttribute(node: FrameNode, nodeType: 'Scroll'): ScrollAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Scroll' | 是 | 获取Scroll节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ScrollAttribute](../arkts-components/arkts-arkui-scroll-attribute.md) | Attributes of the **Scroll** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'RelativeContainer'): RelativeContainerAttribute | undefined
```

获取RelativeContainer节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'RelativeContainer'): RelativeContainerAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'RelativeContainer'): RelativeContainerAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'RelativeContainer' | 是 | 获取RelativeContainer节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RelativeContainerAttribute](../arkts-components/arkts-arkui-relativecontainer-attribute.md) | Attributes of the **RelativeContainer** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'LoadingProgress'): LoadingProgressAttribute | undefined
```

获取[LoadingProgress](../arkts-components/arkts-arkui-loadingprogress.md)节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'LoadingProgress'): LoadingProgressAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'LoadingProgress'): LoadingProgressAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'LoadingProgress' | 是 | 获取LoadingProgress节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LoadingProgressAttribute](../arkts-components/arkts-arkui-loadingprogress-attribute.md) | Properties of the **LoadingProgress** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Image'): ImageAttribute | undefined
```

获取Image节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Image'): ImageAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Image'): ImageAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Image' | 是 | 获取Image节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageAttribute](../arkts-components/arkts-arkui-image-attribute.md) | Properties of the **Image** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'List'): ListAttribute | undefined
```

获取List节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'List'): ListAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'List'): ListAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'List' | 是 | 获取List节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ListAttribute](../arkts-components/arkts-arkui-list-attribute.md) | Attributes of the **List** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'ListItem'): ListItemAttribute | undefined
```

获取ListItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'ListItem'): ListItemAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'ListItem'): ListItemAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'ListItem' | 是 | 获取ListItem节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ListItemAttribute](../arkts-components/arkts-arkui-listitem-attribute.md) | Attributes of the **ListItem** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'TextInput'): TextInputAttribute | undefined
```

获取TextInput节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'TextInput'): TextInputAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'TextInput'): TextInputAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'TextInput' | 是 | 获取TextInput节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextInputAttribute](../arkts-components/arkts-arkui-textinput-attribute.md) | Properties of the **TextInput** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Button'): ButtonAttribute | undefined
```

获取Button节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Button'): ButtonAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Button'): ButtonAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Button' | 是 | 获取Button节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ButtonAttribute](../arkts-components/arkts-arkui-button-attribute.md) | Attributes of the **Button** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'ListItemGroup'): ListItemGroupAttribute | undefined
```

获取ListItemGroup节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'ListItemGroup'): ListItemGroupAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'ListItemGroup'): ListItemGroupAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'ListItemGroup' | 是 | 获取ListItemGroup节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ListItemGroupAttribute](../arkts-components/arkts-arkui-listitemgroup-attribute.md) | Attributes of the **ListItemGroup** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'WaterFlow'): WaterFlowAttribute | undefined
```

获取WaterFlow节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'WaterFlow'): WaterFlowAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'WaterFlow'): WaterFlowAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'WaterFlow' | 是 | 获取WaterFlow节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WaterFlowAttribute](../arkts-components/arkts-arkui-waterflow-attribute.md) | Properties of the **WaterFlow** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'FlowItem'): FlowItemAttribute | undefined
```

获取FlowItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'FlowItem'): FlowItemAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'FlowItem'): FlowItemAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'FlowItem' | 是 | 获取FlowItem节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FlowItemAttribute](../arkts-components/arkts-arkui-flowitem-attribute.md) | Properties of the **FlowItem** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'XComponent'): XComponentAttribute | undefined
```

获取XComponent节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'XComponent'): XComponentAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'XComponent'): XComponentAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'XComponent' | 是 | 获取XComponent节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [XComponentAttribute](../arkts-components/arkts-arkui-xcomponent-attribute.md) | Properties of the **XComponent** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Checkbox'): CheckboxAttribute | undefined
```

获取Checkbox节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Checkbox'): CheckboxAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Checkbox'): CheckboxAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Checkbox' | 是 | 获取Checkbox节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CheckboxAttribute](../arkts-components/arkts-arkui-checkbox-attribute.md) | Attributes of the **Checkbox** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Radio'): RadioAttribute | undefined
```

获取Radio节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Radio'): RadioAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Radio'): RadioAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Radio' | 是 | 获取Radio节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RadioAttribute](../arkts-components/arkts-arkui-radio-attribute.md) | Properties of the **Radio** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Slider'): SliderAttribute | undefined
```

获取Slider节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Slider'): SliderAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Slider'): SliderAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Slider' | 是 | 获取Slider节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SliderAttribute](../arkts-components/arkts-arkui-slider-attribute.md) | Properties of the **Slider** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Toggle'): ToggleAttribute | undefined
```

获取Toggle节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Toggle'): ToggleAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Toggle'): ToggleAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Toggle' | 是 | 获取Toggle节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ToggleAttribute](../arkts-components/arkts-arkui-toggle-attribute.md) | Properties of the **Toggle** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'TextArea'): TextAreaAttribute | undefined
```

获取TextArea节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'TextArea'): TextAreaAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'TextArea'): TextAreaAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'TextArea' | 是 | 获取TextArea节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextAreaAttribute](../arkts-components/arkts-arkui-textarea-attribute.md) | Properties of the **TextArea** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'Grid'): GridAttribute | undefined
```

获取Grid节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Grid'): GridAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'Grid'): GridAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'Grid' | 是 | 获取Grid节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GridAttribute](../arkts-components/arkts-arkui-grid-attribute.md) | Properties of the **Grid** node, or **undefined** if they fail to be obtained. |


## getAttribute

```TypeScript
export function getAttribute(node: FrameNode, nodeType: 'GridItem'): GridItemAttribute | undefined
```

获取GridItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'GridItem'): GridItemAttribute | undefined--><!--Device-typeNode-export function getAttribute(node: FrameNode, nodeType: 'GridItem'): GridItemAttribute | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 获取属性时所需的目标节点。 |
| nodeType | 'GridItem' | 是 | 获取GridItem节点类型的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GridItemAttribute](../arkts-components/arkts-arkui-griditem-attribute.md) | Properties of the **GridItem** node, or **undefined** if they fail to be obtained. |

