# typeNode

```TypeScript
export namespace typeNode
```

Provides APIs for creating a specific type of FrameNode, which can be mounted through the basic API of the FrameNode and be displayed using a placeholder container. It is suitable for scenarios where component nodes of specific types need to be dynamically created through code and custom-mounted.

When **typeNode** is used to create [Text](../arkts-components/arkts-arkui-text-comp.md), [Image](../arkts-components/arkts-arkui-image-comp.md), [Select](../arkts-components/arkts-arkui-select-comp.md), or [Toggle](../arkts-components/arkts-arkui-toggle-comp.md) nodes, if the UI instance corresponding to the input [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) is destroyed, this API returns an invalid FrameNode that cannot be properly mounted or displayed.

**Since:** 12

<!--Device-unnamed-export namespace typeNode--><!--Device-unnamed-export namespace typeNode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Functions

| Name | Description |
| --- | --- |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller1) | Binds a [TextController](../arkts-components/arkts-arkui-text-comp-textcontroller-c.md) instance to a [Text](arkts-arkui-typenode-text-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API does not support declaratively created nodes. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller2) | Binds a [SwiperController](../arkts-components/arkts-arkui-swiper-comp-swipercontroller-c.md) instance to the [Swiper](arkts-arkui-typenode-swiper-t.md) node. Cross- language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API does not support declaratively created nodes. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller3) | Binds the [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) to the [Scroll](arkts-arkui-typenode-scroll-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0. Versions earlier than API version 26.0.0 do not support this. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller4) | Binds a [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) instance to the [List](arkts-arkui-typenode-list-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0. Versions earlier than API version 26.0.0 do not support this. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller5) | Binds the input box controller [TextInputController](../arkts-components/arkts-arkui-textinput-comp-textinputcontroller-c.md) to the [TextInput](arkts-arkui-typenode-textinput-t.md) node. If the node is not created via ArkTS, whether cross-language access is supported must be set. If cross-language access is not supported, an exception is thrown. Since API version 26.0.0, this API supports nodes created in a declarative manner. Versions earlier than API version 26.0.0 do not support this. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller6) | Binds a [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) instance to the [WaterFlow](arkts-arkui-typenode-waterflow-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller7) | Binds the input box controller [TextAreaController](../arkts-components/arkts-arkui-textarea-comp-textareacontroller-c.md) to the [TextArea](arkts-arkui-typenode-textarea-t.md) node. If the node is not created via ArkTS, whether cross-language access is supported must be set. If cross-language access is not supported, an exception is thrown. Since API version 26.0.0, this API supports nodes created in a declarative manner. Versions earlier than API version 26.0.0 do not support this. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller8) | Binds a [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) instance to the [Grid](arkts-arkui-typenode-grid-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0. Versions earlier than API version 26.0.0 do not support this. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode1) | Creates a FrameNode of the **Text** type. When **typeNode** is used to create a **Text** node, after the UI instance corresponding to the passed **UIContext** is destroyed, calling this API returns an invalid FrameNode that cannot be properly mounted and displayed. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode2) | Creates a FrameNode of the **Column** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode3) | Creates a FrameNode of the Row type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode4) | Creates a FrameNode of the **Stack** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode5) | Creates a FrameNode of the **GridRow** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode6) | Creates a FrameNode of the **GridCol** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode7) | Creates a FrameNode of the Flex type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode8) | Creates a FrameNode of the **Swiper** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode9) | Creates a FrameNode of the **Progress** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode10) | Creates a FrameNode of the **Scroll** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode11) | Creates a FrameNode of the **RelativeContainer** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode12) | Creates a FrameNode of the **Divider** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode13) | Creates a FrameNode of the **LoadingProgress** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode14) | Creates a FrameNode of the **Search** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode15) | Creates a FrameNode of the **Blank** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode16) | Creates a FrameNode of the **Image** type. When **typeNode** is used to create an **Image** node, after the UI instance corresponding to the passed **UIContext** is destroyed, calling this API returns an invalid FrameNode that cannot be properly mounted and displayed. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode17) | Creates a FrameNode of the **List** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode18) | Creates a FrameNode of the **ListItem** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode19) | Creates a FrameNode of the **TextInput** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode20) | Creates a FrameNode of the **Button** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode21) | Creates a FrameNode of the **ListItemGroup** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode22) | Creates a FrameNode of the **WaterFlow** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode23) | Creates a FrameNode of the **FlowItem** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode24) | Creates a FrameNode of the **XComponent** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode25) | Creates a FrameNode of the **XComponent** type based on the settings specified in **options**. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode26) | Creates a FrameNode of the **XComponent** type based on the settings specified in **parameters**. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode27) | Creates a FrameNode of the **Checkbox** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode28) | Creates a FrameNode of the **CheckboxGroup** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode29) | Creates a FrameNode of the **Radio** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode30) | Creates a FrameNode of the **Rating** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode31) | Creates a FrameNode of the **Select** type. When **typeNode** is used to create a **Select** node, after the UI instance corresponding to the passed **UIContext** is destroyed, calling this API returns an invalid FrameNode that cannot be properly mounted and displayed. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode32) | Creates a FrameNode of the **Slider** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode33) | Creates a FrameNode of the **Toggle** type. When **typeNode** is used to create a **Toggle** node, after the UI instance corresponding to the passed **UIContext** is destroyed, calling this API returns an invalid FrameNode that cannot be properly mounted and displayed. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode34) | Creates a FrameNode of the **Marquee** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode35) | Creates a FrameNode of the **TextArea** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode36) | Creates a FrameNode of the **SymbolGlyph** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode37) | Creates a FrameNode of the **QRCode** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode38) | Creates a FrameNode of the **Badge** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode39) | Creates a FrameNode of the **TextClock** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode40) | Creates a FrameNode of the **TextTimer** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode41) | Creates a FrameNode of the **Grid** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode42) | Creates a FrameNode of the **GridItem** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute1) | Obtains the attributes of a **Text** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute2) | Obtains the attributes of a **Column** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute3) | Obtains the attributes of a **Row** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute4) | Obtains the attributes of a **Stack** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute5) | Obtains the Flex node attributes. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute6) | Obtains the attributes of a **Swiper** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute7) | Obtains the attributes of a **Progress** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute8) | Obtains the attributes of a **Scroll** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute9) | Obtains the attributes of a **RelativeContainer** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute10) | Obtains the attributes of a [LoadingProgress](../arkts-components/arkts-arkui-loadingprogress-comp.md) node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute11) | Obtains the attributes of an **Image** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute12) | Obtains the attributes of a **List** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute13) | Obtains the attributes of a **ListItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute14) | Obtains the attributes of a **TextInput** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute15) | Obtains the attributes of a **Button** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute16) | Obtains the attributes of a **ListItemGroup** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute17) | Obtains the attributes of a **WaterFlow** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute18) | Obtains the attributes of a **FlowItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute19) | Obtain the attributes of an **XComponent** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute20) | Obtains the attributes of a **Checkbox** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute21) | Obtains the attributes of a **Radio** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute22) | Obtains the attributes of a **Slider** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute23) | Obtains the attributes of a **Toggle** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute24) | Obtains the attributes of a **TextArea** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute25) | Obtains the attributes of a **Grid** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute26) | Obtains the attributes of a **GridItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getEvent](arkts-arkui-typenode-getevent-f.md#getevent1) | Obtains the **UIScrollEvent** object held by the **Scroll** node, which is used to set scroll events. If the node is not created via ArkTS, whether cross-language access is supported must be set. If cross-language access is not supported, **undefined** is returned. This API does not support nodes created in a declarative manner. The scroll events set through this API coexist with declaratively defined events. The set scroll events do not override the original declarative events. When both event callbacks are set, the declarative event callback takes precedence. |
| [getEvent](arkts-arkui-typenode-getevent-f.md#getevent2) | Obtains the **UIListEvent** object held by the **List** node, which is used to set scroll events. If the node is not created via ArkTS, whether cross-language access is supported must be set. If cross-language access is not supported, **undefined** is returned. This API does not support nodes created in a declarative manner. The scroll events set through this API coexist with declaratively defined events. The set scroll events do not override the original declarative events. When both event callbacks are set, the declarative event callback takes precedence. |
| [getEvent](arkts-arkui-typenode-getevent-f.md#getevent3) | Obtains the **UIWaterFlowEvent** object held by the [WaterFlow](arkts-arkui-typenode-waterflow-t.md) node, which is used to set scroll events. If the node is not created via ArkTS, whether cross-language access is supported must be set. If cross-language access is not supported, **undefined** is returned. This API does not support nodes created in a declarative manner. The scroll events set through this API coexist with declaratively defined events. The set scroll events do not override the original declarative events. When both event callbacks are set, the declarative event callback takes precedence. |
| [getEvent](arkts-arkui-typenode-getevent-f.md#getevent4) | Obtains the **UIGridEvent** object held by the **Grid** node, which is used to set scroll events. If the node is not created via ArkTS, whether cross-language access is supported must be set. If cross-language access is not supported, **undefined** is returned. This API does not support nodes created in a declarative manner. The scroll events set through this API coexist with declaratively defined events. The set scroll events do not override the original declarative events. When both event callbacks are set, the declarative event callback takes precedence. |

### Types

| Name | Description |
| --- | --- |
| [Badge](arkts-arkui-typenode-badge-t.md) | Represents a FrameNode of the **Badge** type. |
| [Blank](arkts-arkui-typenode-blank-t.md) | Represents a FrameNode of the **Blank** type. This type of node does not allow child components to be added. |
| [Button](arkts-arkui-typenode-button-t.md) | Represents a FrameNode of the **Button** type. When created in child component mode, this type of node allows only one child component to be added. When created in label mode, it does not allow child components to be added. |
| [Checkbox](arkts-arkui-typenode-checkbox-t.md) | Represents a FrameNode of the **Checkbox** type. |
| [CheckboxGroup](arkts-arkui-typenode-checkboxgroup-t.md) | Represents a FrameNode of the **CheckboxGroup** type. |
| [Column](arkts-arkui-typenode-column-t.md) | Represents a FrameNode of the **Column** type. |
| [Divider](arkts-arkui-typenode-divider-t.md) | Represents a FrameNode of the **Divider** type. This type of node does not allow child components to be added. |
| [Flex](arkts-arkui-typenode-flex-t.md) | Represents a FrameNode of the Flex type. |
| [FlowItem](arkts-arkui-typenode-flowitem-t.md) | Represents a FrameNode of the **FlowItem** type. This type of node allows only one child component to be added. |
| [Grid](arkts-arkui-typenode-grid-t.md) | Represents a FrameNode of the **Grid** type. |
| [GridCol](arkts-arkui-typenode-gridcol-t.md) | Represents a FrameNode of the **GridCol** type. This type of node does not allow child components to be added. |
| [GridItem](arkts-arkui-typenode-griditem-t.md) | Represents a FrameNode of the **GridItem** type. |
| [GridRow](arkts-arkui-typenode-gridrow-t.md) | Represents a FrameNode of the **GridRow** type. This type of node only allows child components of the **GridCol** type. |
| [Image](arkts-arkui-typenode-image-t.md) | Represents a FrameNode of the **Image** type. This type of node does not allow child components to be added. |
| [List](arkts-arkui-typenode-list-t.md) | Represents a FrameNode of the **List** type. This type of node only allows child components of the [ListItem](arkts-arkui-typenode-listitem-t.md) and [ListItemGroup](arkts-arkui-typenode-listitemgroup-t.md) types. |
| [ListItem](arkts-arkui-typenode-listitem-t.md) | Represents a FrameNode of the **ListItem** type. |
| [ListItemGroup](arkts-arkui-typenode-listitemgroup-t.md) | Represents a FrameNode of the **ListItemGroup** type. Only [ListItem](../arkts-components/arkts-arkui-listitem-comp.md) child components can be added. |
| [LoadingProgress](arkts-arkui-typenode-loadingprogress-t.md) | Represents a FrameNode of the **LoadingProgress** type. This type of node does not allow child components to be added. |
| [Marquee](arkts-arkui-typenode-marquee-t.md) | Represents a FrameNode of the **Marquee** type. |
| [Progress](arkts-arkui-typenode-progress-t.md) | Represents a FrameNode of the **Progress** type. This type of node does not allow child components to be added. |
| [QRCode](arkts-arkui-typenode-qrcode-t.md) | Represents a FrameNode of the **QRCode** type. |
| [Radio](arkts-arkui-typenode-radio-t.md) | Represents a FrameNode of the **Radio** type. |
| [Rating](arkts-arkui-typenode-rating-t.md) | Represents a FrameNode of the **Rating** type. |
| [RelativeContainer](arkts-arkui-typenode-relativecontainer-t.md) | Represents a FrameNode of the **RelativeContainer** type. |
| [Row](arkts-arkui-typenode-row-t.md) | Represents a FrameNode of the **Row** type. |
| [Scroll](arkts-arkui-typenode-scroll-t.md) | Represents a FrameNode of the **Scroll** type. This type of node allows only one child component to be added. |
| [Search](arkts-arkui-typenode-search-t.md) | Represents a FrameNode of the **Search** type. |
| [Select](arkts-arkui-typenode-select-t.md) | Represents a FrameNode of the **Select** type. |
| [Slider](arkts-arkui-typenode-slider-t.md) | Represents a FrameNode of the **Slider** type. |
| [Stack](arkts-arkui-typenode-stack-t.md) | Represents a FrameNode of the **Stack** type. |
| [Swiper](arkts-arkui-typenode-swiper-t.md) | Represents a FrameNode of the **Swiper** type. |
| [SymbolGlyph](arkts-arkui-typenode-symbolglyph-t.md) | Represents a FrameNode of the **SymbolGlyph** type. |
| [Text](arkts-arkui-typenode-text-t.md) | Represents a FrameNode of the **Text** type. This type of node does not allow child components to be added. |
| [TextArea](arkts-arkui-typenode-textarea-t.md) | Represents a FrameNode of the **TextArea** type. |
| [TextClock](arkts-arkui-typenode-textclock-t.md) | Represents a FrameNode of the **TextClock** type. |
| [TextInput](arkts-arkui-typenode-textinput-t.md) | Represents a FrameNode of the **TextInput** type. |
| [TextTimer](arkts-arkui-typenode-texttimer-t.md) | Represents a FrameNode of the **TextTimer** type. |
| [Toggle](arkts-arkui-typenode-toggle-t.md) | FrameNode of the [Toggle](../arkts-components/arkts-arkui-toggle-comp.md) type. |
| [WaterFlow](arkts-arkui-typenode-waterflow-t.md) | Represents a FrameNode of the **WaterFlow** type. Only [FlowItem](../arkts-components/arkts-arkui-flowitem-comp-attribute.md#flowitemattribute) child components can be added. |
| [XComponent](arkts-arkui-typenode-xcomponent-t.md) | Represents a FrameNode of the **XComponent** type. |
