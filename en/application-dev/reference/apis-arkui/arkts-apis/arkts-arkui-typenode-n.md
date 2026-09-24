# typeNode

```TypeScript
export namespace typeNode
```

Provides APIs for creating a specific type of FrameNode, which can be mounted through the basic API of the FrameNode and be displayed using a placeholder container.

When **typeNode** is used to create [Text](../arkts-components/arkts-arkui-text-comp.md#text), [Image](../arkts-components/arkts-arkui-image-comp.md#image), [Select](../arkts-components/arkts-arkui-select-comp.md#select), or [Toggle](../arkts-components/arkts-arkui-toggle-comp.md#toggle) nodes, if the UI instance corresponding to the input [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) is destroyed, this API returns an invalid FrameNode that cannot be properly mounted or displayed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode) | Creates a FrameNode of the **Text** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute) | Obtains the attributes of a **Text** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller) | Binds a [TextController](../arkts-components/arkts-arkui-text-comp-textcontroller-c.md) instance to a [Text](arkts-arkui-typenode-text-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-1) | Creates a FrameNode of the **Column** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-1) | Obtains the attributes of a **Column** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-2) | Creates a FrameNode of the Row type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-2) | Obtains the attributes of a **Row** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-3) | Creates a FrameNode of the **Stack** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-3) | Obtains the attributes of a **Stack** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-4) | Creates a FrameNode of the **GridRow** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-5) | Creates a FrameNode of the **GridCol** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-6) | Creates a FrameNode of the Flex type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-4) | Obtains the Flex node attributes. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-7) | Creates a FrameNode of the **Swiper** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-5) | Obtains the attributes of a **Swiper** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller-1) | Binds a [SwiperController](../arkts-components/arkts-arkui-swiper-comp-swipercontroller-c.md) instance to the [Swiper](arkts-arkui-typenode-swiper-t.md) node. Cross- language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-8) | Creates a FrameNode of the **Progress** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-6) | Obtains the attributes of a **Progress** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-9) | Creates a FrameNode of the **Scroll** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-7) | Obtains the attributes of a **Scroll** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [getEvent](arkts-arkui-typenode-getevent-f.md#getevent) | Obtains the **UIScrollEvent** object associated with the **Scroll** node for configuring scroll events. The scroll events configured through this API coexist with declarative events without overriding them. If both event callbacks are registered, the declaratively defined event callback takes precedence. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller-2) | Binds the [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) to the [Scroll](arkts-arkui-typenode-scroll-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-10) | Creates a FrameNode of the **RelativeContainer** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-8) | Obtains the attributes of a **RelativeContainer** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-11) | Creates a FrameNode of the **Divider** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-12) | Creates a FrameNode of the **LoadingProgress** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-9) | Obtains the attributes of a [LoadingProgress](../arkts-components/arkts-arkui-loadingprogress-comp.md#loading_progress) node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-13) | Creates a FrameNode of the **Search** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-14) | Creates a FrameNode of the **Blank** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-15) | Creates a FrameNode of the **Image** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-10) | Obtains the attributes of an **Image** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-16) | Creates a FrameNode of the **List** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-11) | Obtains the attributes of a **List** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller-3) | Binds a [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) instance to the [List](arkts-arkui-typenode-list-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0. |
| [getEvent](arkts-arkui-typenode-getevent-f.md#getevent-1) | Obtains the **UIListEvent** object associated with the **List** node for configuring scroll events. The scroll events configured through this API coexist with declarative events without overriding them. If both event callbacks are registered, the declaratively defined event callback takes precedence. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-17) | Creates a FrameNode of the **ListItem** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-12) | Obtains the attributes of a **ListItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-18) | Creates a FrameNode of the **TextInput** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-13) | Obtains the attributes of a **TextInput** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller-4) | Binds the [TextInputController](../arkts-components/arkts-arkui-textinput-comp-textinputcontroller-c.md) to the [TextInput](arkts-arkui-typenode-textinput-t.md) node. Cross -language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-19) | Creates a FrameNode of the **Button** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-14) | Obtains the attributes of a **Button** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-20) | Creates a FrameNode of the **ListItemGroup** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-15) | Obtains the attributes of a **ListItemGroup** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-21) | Creates a FrameNode of the **WaterFlow** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-16) | Obtains the attributes of a **WaterFlow** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller-5) | Binds a [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) instance to the [WaterFlow](arkts-arkui-typenode-waterflow-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0. |
| [getEvent](arkts-arkui-typenode-getevent-f.md#getevent-2) | Obtains the **UIWaterFlowEvent** object associated with the [WaterFlow](arkts-arkui-typenode-waterflow-t.md) node for configuring scroll events. The scroll events configured through this API coexist with declarative events without overriding them. If both event callbacks are registered, the declaratively defined event callback takes precedence. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-22) | Creates a FrameNode of the **FlowItem** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-17) | Obtains the attributes of a **FlowItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-23) | Creates a FrameNode of the **XComponent** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-24) | Creates a FrameNode of the **XComponent** type based on the settings specified in **options**. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-25) | Creates a FrameNode of the **XComponent** type based on the settings specified in **parameters**. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-18) | Obtain the attributes of an **XComponent** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-26) | Creates a FrameNode of the **Checkbox** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-19) | Obtains the attributes of a **Checkbox** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-27) | Creates a FrameNode of the **CheckboxGroup** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-28) | Creates a FrameNode of the **Radio** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-20) | Obtains the attributes of a **Radio** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-29) | Creates a FrameNode of the **Rating** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-30) | Creates a FrameNode of the **Select** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-31) | Creates a FrameNode of the **Slider** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-21) | Obtains the attributes of a **Slider** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-32) | Creates a FrameNode of the **Toggle** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-22) | Obtains the attributes of a **Toggle** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-33) | Creates a FrameNode of the **Marquee** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-34) | Creates a FrameNode of the **TextArea** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-23) | Obtains the attributes of a **TextArea** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller-6) | Binds a [TextAreaController](../arkts-components/arkts-arkui-textarea-comp-textareacontroller-c.md) instance to the [TextArea](arkts-arkui-typenode-textarea-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-35) | Creates a FrameNode of the **SymbolGlyph** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-36) | Creates a FrameNode of the **QRCode** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-37) | Creates a FrameNode of the **Badge** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-38) | Creates a FrameNode of the **TextClock** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-39) | Creates a FrameNode of the **TextTimer** type. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-40) | Creates a FrameNode of the **Grid** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-24) | Obtains the attributes of a **Grid** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md#bindcontroller-7) | Binds a [Scroller](../arkts-components/arkts-arkui-scroll-comp-scroller-c.md) instance to the [Grid](arkts-arkui-typenode-grid-t.md) node. Cross-language access must be enabled for nodes not created via ArkTS; otherwise, an exception will be thrown. This API supports declaratively created nodes since API version 26.0.0. |
| [getEvent](arkts-arkui-typenode-getevent-f.md#getevent-3) | Obtains the **UIGridEvent** object associated with the **Grid** node for configuring scroll events. The scroll events configured through this API coexist with declarative events without overriding them. If both event callbacks are registered, the declaratively defined event callback takes precedence. |
| [createNode](arkts-arkui-typenode-createnode-f.md#createnode-41) | Creates a FrameNode of the **GridItem** type. |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md#getattribute-25) | Obtains the attributes of a **GridItem** node. If the node is not created using ArkTS, cross-language access must be enabled; otherwise, **undefined** is returned. This API does not support declaratively created nodes. |

### Types

| Name | Description |
| --- | --- |
| [Text](arkts-arkui-typenode-text-t.md) | Represents a FrameNode of the **Text** type. This type of node does not allow child components to be added. |
| [Column](arkts-arkui-typenode-column-t.md) | Represents a FrameNode of the **Column** type. |
| [Row](arkts-arkui-typenode-row-t.md) | Represents a FrameNode of the **Row** type. |
| [Stack](arkts-arkui-typenode-stack-t.md) | Represents a FrameNode of the **Stack** type. |
| [GridRow](arkts-arkui-typenode-gridrow-t.md) | Represents a FrameNode of the **GridRow** type. This type of node only allows child components of the **GridCol** type. |
| [GridCol](arkts-arkui-typenode-gridcol-t.md) | Represents a FrameNode of the **GridCol** type. This type of node does not allow child components to be added. |
| [Flex](arkts-arkui-typenode-flex-t.md) | Represents a FrameNode of the Flex type. |
| [Swiper](arkts-arkui-typenode-swiper-t.md) | Represents a FrameNode of the **Swiper** type. |
| [Progress](arkts-arkui-typenode-progress-t.md) | Represents a FrameNode of the **Progress** type. This type of node does not allow child components to be added. |
| [Scroll](arkts-arkui-typenode-scroll-t.md) | Represents a FrameNode of the **Scroll** type. This type of node allows only one child component to be added. |
| [RelativeContainer](arkts-arkui-typenode-relativecontainer-t.md) | Represents a FrameNode of the **RelativeContainer** type. |
| [Divider](arkts-arkui-typenode-divider-t.md) | Represents a FrameNode of the **Divider** type. This type of node does not allow child components to be added. |
| [LoadingProgress](arkts-arkui-typenode-loadingprogress-t.md) | Represents a FrameNode of the **LoadingProgress** type. This type of node does not allow child components to be added. |
| [Search](arkts-arkui-typenode-search-t.md) | Represents a FrameNode of the **Search** type. |
| [Blank](arkts-arkui-typenode-blank-t.md) | Represents a FrameNode of the **Blank** type. This type of node does not allow child components to be added. |
| [Image](arkts-arkui-typenode-image-t.md) | Represents a FrameNode of the **Image** type. This type of node does not allow child components to be added. |
| [List](arkts-arkui-typenode-list-t.md) | Represents a FrameNode of the **List** type. This type of node only allows child components of the [ListItem](arkts-arkui-typenode-listitem-t.md) and [ListItemGroup](arkts-arkui-typenode-listitemgroup-t.md) types. |
| [ListItem](arkts-arkui-typenode-listitem-t.md) | Represents a FrameNode of the **ListItem** type. |
| [TextInput](arkts-arkui-typenode-textinput-t.md) | Represents a FrameNode of the **TextInput** type. |
| [Button](arkts-arkui-typenode-button-t.md) | Represents a FrameNode of the **Button** type. When created in child component mode, this type of node allows only one child component to be added. When created in label mode, it does not child components to be added. |
| [ListItemGroup](arkts-arkui-typenode-listitemgroup-t.md) | Represents a FrameNode of the **ListItemGroup** type. Only [ListItem](../arkts-components/arkts-arkui-listitem-comp.md#list_item) child components can be added. |
| [WaterFlow](arkts-arkui-typenode-waterflow-t.md) | Represents a FrameNode of the **WaterFlow** type. Only [FlowItem](../arkts-components/arkts-arkui-flowitem-comp-attribute.md#flowitemattribute) child components can be added. |
| [FlowItem](arkts-arkui-typenode-flowitem-t.md) | Represents a FrameNode of the **FlowItem** type. This type of node allows only one child component to be added. |
| [XComponent](arkts-arkui-typenode-xcomponent-t.md) | Represents a FrameNode of the **XComponent** type. |
| [Checkbox](arkts-arkui-typenode-checkbox-t.md) | Represents a FrameNode of the **Checkbox** type. |
| [CheckboxGroup](arkts-arkui-typenode-checkboxgroup-t.md) | Represents a FrameNode of the **CheckboxGroup** type. |
| [Radio](arkts-arkui-typenode-radio-t.md) | Represents a FrameNode of the **Radio** type. |
| [Rating](arkts-arkui-typenode-rating-t.md) | Represents a FrameNode of the **Rating** type. |
| [Select](arkts-arkui-typenode-select-t.md) | Represents a FrameNode of the **Select** type. |
| [Slider](arkts-arkui-typenode-slider-t.md) | Represents a FrameNode of the **Slider** type. |
| [Toggle](arkts-arkui-typenode-toggle-t.md) | FrameNode of the [Toggle](../arkts-components/arkts-arkui-toggle-comp.md#toggle) type. |
| [Marquee](arkts-arkui-typenode-marquee-t.md) | Represents a FrameNode of the **Marquee** type. |
| [TextArea](arkts-arkui-typenode-textarea-t.md) | Represents a FrameNode of the **TextArea** type. |
| [SymbolGlyph](arkts-arkui-typenode-symbolglyph-t.md) | Represents a FrameNode of the **SymbolGlyph** type. |
| [QRCode](arkts-arkui-typenode-qrcode-t.md) | Represents a FrameNode of the **QRCode** type. |
| [Badge](arkts-arkui-typenode-badge-t.md) | Represents a FrameNode of the **Badge** type. |
| [TextClock](arkts-arkui-typenode-textclock-t.md) | Represents a FrameNode of the **TextClock** type. |
| [TextTimer](arkts-arkui-typenode-texttimer-t.md) | Represents a FrameNode of the **TextTimer** type. |
| [Grid](arkts-arkui-typenode-grid-t.md) | Represents a FrameNode of the **Grid** type. |
| [GridItem](arkts-arkui-typenode-griditem-t.md) | Represents a FrameNode of the **GridItem** type. |
