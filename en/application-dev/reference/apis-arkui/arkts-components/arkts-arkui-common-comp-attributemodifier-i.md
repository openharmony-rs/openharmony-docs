# AttributeModifier

```TypeScript
declare interface AttributeModifier<T>
```

You need a custom class to implement the **AttributeModifier** API.

> **NOTE:** 
> 
> In the following APIs, setting the same value or object for the same attribute of the **instance** object will not
> trigger an update.

## Attribute Type Support Scope

| Name | Description |  
| ----------------- | --------------- |  
| AlphabetIndexerAttribute | [Attributes](arkts-arkui-alphabetindexer-comp-attribute.md#alphabetindexerattribute) of AlphabetIndexer. |
| BadgeAttribute | [Attributes](arkts-arkui-badge-comp-attribute.md#badgeattribute) of Badge. |
| BlankAttribute | [Attributes](arkts-arkui-blank-comp-attribute.md#blankattribute) of Blank. |
| ButtonAttribute | [Attributes](arkts-arkui-button-comp-attribute.md#buttonattribute) of Button. |
| CalendarPickerAttribute | [Attributes](arkts-arkui-calendarpicker-comp-attribute.md#calendarpickerattribute) of CalendarPicker. |
| CanvasAttribute | [Attributes](arkts-arkui-canvas-comp-attribute.md#canvasattribute) of Canvas. |
| CheckboxAttribute | [Attributes](arkts-arkui-checkbox-comp-attribute.md#checkboxattribute) of Checkbox. |
| CheckboxGroupAttribute | [Attributes](arkts-arkui-checkboxgroup-comp-attribute.md#checkboxgroupattribute) of CheckboxGroup. |
| CircleAttribute | [Attributes](arkts-arkui-circle-comp-attribute.md#circleattribute) of Circle. |
| ColumnAttribute | [Attributes](arkts-arkui-column-comp-attribute.md#columnattribute) of Column. |
| ColumnSplitAttribute | [Attributes](arkts-arkui-columnsplit-comp-attribute.md#columnsplitattribute) of ColumnSplit. |
| CommonAttribute | [Attributes](arkts-arkui-common-comp-attribute.md#commonattribute) of Common. |
| CounterAttribute | [Attributes](arkts-arkui-counter-comp-attribute.md#counterattribute) of Counter. |
| DataPanelAttribute | [Attributes](arkts-arkui-datapanel-comp-attribute.md#datapanelattribute) of DataPanel. |
| DatePickerAttribute | [Attributes](arkts-arkui-datepicker-comp-attribute.md#datepickerattribute) of DatePicker. |
| DividerAttribute | [Attributes](arkts-arkui-divider-comp-attribute.md#dividerattribute) of Divider. |
| EllipseAttribute | [Attributes](arkts-arkui-ellipse-comp-attribute.md#ellipseattribute) of Ellipse. |
| FlexAttribute | [Attributes](arkts-arkui-flex-comp-attribute.md#flexattribute) of Flex. |
| FlowItemAttribute | [Attributes](arkts-arkui-flowitem-comp-attribute.md#flowitemattribute) of FlowItem. |
| FormLinkAttribute | [Attributes](arkts-arkui-formlink-comp-attribute.md#formlinkattribute) of FormLink. |
| GaugeAttribute | [Attributes](arkts-arkui-gauge-comp-attribute.md#gaugeattribute) of Gauge. |
| GridAttribute | [Attributes](arkts-arkui-grid-comp-attribute.md#gridattribute) of Grid. |
| GridColAttribute | [Attributes](arkts-arkui-gridcol-comp-attribute.md#gridcolattribute) of GridCol. |
| GridItemAttribute | [Attributes](arkts-arkui-griditem-comp-attribute.md#griditemattribute) of GridItem. |
| GridRowAttribute | [Attributes](arkts-arkui-gridrow-comp-attribute.md#gridrowattribute) of GridRow. |
| HyperlinkAttribute | [Attributes](arkts-arkui-hyperlink-comp-attribute.md#hyperlinkattribute) of Hyperlink. |
| IndicatorComponentAttribute | [Attributes](arkts-arkui-indicatorcomponent-comp-attribute.md#indicatorcomponentattribute) of IndicatorComponent. |
| ImageAttribute | [Attributes](arkts-arkui-image-comp-attribute.md#imageattribute) of Image. |
| ImageAnimatorAttribute | [Attributes](arkts-arkui-imageanimator-comp-attribute.md#imageanimatorattribute) of ImageAnimator. |
| ImageSpanAttribute | [Attributes](arkts-arkui-imagespan-comp-attribute.md#imagespanattribute) of ImageSpan. |
| ContainerSpanAttribute | [Attributes](arkts-arkui-containerspan-comp-attribute.md#containerspanattribute) of ContainerSpan. |
| LineAttribute | [Attributes](arkts-arkui-line-comp-attribute.md#lineattribute) of Line. |
| ListAttribute | [Attributes](arkts-arkui-list-comp-attribute.md#listattribute) of List. |
| ListItemAttribute | [Attributes](arkts-arkui-listitem-comp-attribute.md#listitemattribute) of ListItem. |
| ListItemGroupAttribute | [Attributes](arkts-arkui-listitemgroup-comp-attribute.md#listitemgroupattribute) of ListItemGroup. |
| LoadingProgressAttribute | [Attributes](arkts-arkui-loadingprogress-comp-attribute.md#loadingprogressattribute) of LoadingProgress. |
| MarqueeAttribute | [Attributes](arkts-arkui-marquee-comp-attribute.md#marqueeattribute) of Marquee. |
| MenuAttribute | [Attributes](arkts-arkui-menu-comp-attribute.md#menuattribute) of Menu. |
| MenuItemAttribute | [Attributes](arkts-arkui-menuitem-comp-attribute.md#menuitemattribute) of MenuItem. |
| MenuItemGroupAttribute | Attributes of [MenuItemGroup](arkts-arkui-menuitemgroup-comp.md). |
| NavDestinationAttribute | [Attributes](arkts-arkui-navdestination-comp-attribute.md#navdestinationattribute) of NavDestination. |
| NavigationAttribute | [Attributes](arkts-arkui-navigation-comp-attribute.md#navigationattribute) of Navigation. |
| NavigatorAttribute | [Attributes](arkts-arkui-navigator-comp-attribute.md#navigatorattribute) of Navigator. |
| NavRouterAttribute | [Attributes](arkts-arkui-navrouter-comp-attribute.md#navrouterattribute) of NavRouter. |
| PanelAttribute | [Attributes](arkts-arkui-panel-comp-attribute.md#panelattribute) of Panel. |
| PathAttribute | [Attributes](arkts-arkui-path-comp-attribute.md#pathattribute) of Path. |
| PatternLockAttribute | [Attributes](arkts-arkui-patternlock-comp-attribute.md#patternlockattribute) of PatternLock. |
| PolygonAttribute | [Attributes](arkts-arkui-polygon-comp-attribute.md#polygonattribute) of Polygon. |
| PolylineAttribute | [Attributes](arkts-arkui-polyline-comp-attribute.md#polylineattribute) of Polyline. |
| ProgressAttribute | [Attributes](arkts-arkui-progress-comp-attribute.md#progressattribute) of Progress. |
| QRCodeAttribute | [Attributes](arkts-arkui-qrcode-comp-attribute.md#qrcodeattribute) of QRCode. |
| RadioAttribute | [Attributes](arkts-arkui-radio-comp-attribute.md#radioattribute) of Radio. |
| RatingAttribute | [Attributes](arkts-arkui-rating-comp-attribute.md#ratingattribute) of Rating. |
| RectAttribute | [Attributes](arkts-arkui-rect-comp-attribute.md#rectattribute) of Rect. |
| RefreshAttribute | [Attributes](arkts-arkui-refresh-comp-attribute.md#refreshattribute) of Refresh. |
| RelativeContainerAttribute | [Attributes](arkts-arkui-relativecontainer-comp-attribute.md#relativecontainerattribute) of RelativeContainer. |
| RichEditorAttribute | [Attributes](arkts-arkui-richeditor-comp-attribute.md#richeditorattribute) of RichEditor. |
| RichTextAttribute | [Attributes](arkts-arkui-richtext-comp-attribute.md#richtextattribute) of RichText. |
| RowAttribute | [Attributes](arkts-arkui-row-comp-attribute.md#rowattribute) of Row. |
| RowSplitAttribute | [Attributes](arkts-arkui-rowsplit-comp-attribute.md#rowsplitattribute) of RowSplit. |
| ScrollAttribute | [Attributes](arkts-arkui-scroll-comp-attribute.md#scrollattribute) of Scroll. |
| ScrollBarAttribute | [Attributes](arkts-arkui-scrollbar-comp-attribute.md#scrollbarattribute) of ScrollBar. |
| SearchAttribute | [Attributes](arkts-arkui-search-comp-attribute.md#searchattribute) of Search. |
| SelectAttribute | [Attributes](arkts-arkui-select-comp-attribute.md#selectattribute) of Select. |
| ShapeAttribute | [Attributes](arkts-arkui-shape-comp-attribute.md#shapeattribute) of Shape. |
| SideBarContainerAttribute | [Attributes](arkts-arkui-sidebarcontainer-comp-attribute.md#sidebarcontainerattribute) of SideBarContainer. |
| SliderAttribute | [Attributes](arkts-arkui-slider-comp-attribute.md#sliderattribute) of Slider. |
| SpanAttribute | [Attributes](arkts-arkui-span-comp-attribute.md#spanattribute) of Span. |
| SymbolSpanAttribute | [Attributes](arkts-arkui-symbolspan-comp-attribute.md#symbolspanattribute) of SymbolSpan. |
| StackAttribute | [Attributes](arkts-arkui-stack-comp-attribute.md#stackattribute) of Stack. |
| StepperAttribute | [Attributes](arkts-arkui-stepper-comp-attribute.md#stepperattribute) of Stepper. |
| StepperItemAttribute | [Attributes](arkts-arkui-stepperitem-comp-attribute.md#stepperitemattribute) of StepperItem. |
| SwiperAttribute | [Attributes](arkts-arkui-swiper-comp-attribute.md#swiperattribute) of Swiper. |
| SymbolGlyphAttribute | [Attributes](arkts-arkui-symbolglyph-comp-attribute.md#symbolglyphattribute) of SymbolGlyph. |
| TabContentAttribute | [Attributes](arkts-arkui-tabcontent-comp-attribute.md#tabcontentattribute) of TabContent. |
| TabsAttribute | [Attributes](arkts-arkui-tabs-comp-attribute.md#tabsattribute) of Tabs. |
| TextAttribute | [Attributes](arkts-arkui-text-comp-attribute.md#textattribute) of Text. |
| TextAreaAttribute | [Attributes](arkts-arkui-textarea-comp-attribute.md#textareaattribute) of TextArea. |
| TextClockAttribute | [Attributes](arkts-arkui-textclock-comp-attribute.md#textclockattribute) of TextClock. |
| TextInputAttribute | [Attributes](arkts-arkui-textinput-comp-attribute.md#textinputattribute) of TextInput. |
| TextPickerAttribute | [Attributes](arkts-arkui-textpicker-comp-attribute.md#textpickerattribute) of TextPicker. |
| TextTimerAttribute | [Attributes](arkts-arkui-texttimer-comp-attribute.md#texttimerattribute) of TextTimer. |
| TimePickerAttribute | [Attributes](arkts-arkui-timepicker-comp-attribute.md#timepickerattribute) of TimePicker. |
| ToggleAttribute | [Attributes](arkts-arkui-toggle-comp-attribute.md#toggleattribute) of Toggle. |
| VideoAttribute | [Attributes](arkts-arkui-video-comp-attribute.md#videoattribute) of Video. |
| WaterFlowAttribute | [Attributes](arkts-arkui-waterflow-comp-attribute.md#waterflowattribute) of WaterFlow. |
| XComponentAttribute | [Attributes](arkts-arkui-xcomponent-comp-attribute.md#xcomponentattribute) of XComponent. |
| ParticleAttribute | [Attributes](arkts-arkui-particle-comp-attribute.md#particleattribute) of Particle. |
| UIPickerComponentAttribute&lt;sup&gt;22+&lt;/sup&gt; | [Attributes](arkts-arkui-uipickercomponent-comp-attribute.md#uipickercomponentattribute) of UIPickerComponent. |
| <!--DelRow-->EffectComponentAttribute | [Attributes](arkts-arkui-effectcomponent-comp-attribute.md#effectcomponentattribute-system-api) of EffectComponent. |
| <!--DelRow-->FormComponentAttribute | [Attributes](arkts-arkui-formcomponent-comp-attribute.md#formcomponentattribute-system-api) of FormComponent. |
| <!--DelRow-->PluginComponentAttribute | [Attributes](arkts-arkui-plugincomponent-comp-attribute.md#plugincomponentattribute-system-api) of PluginComponent. |
| <!--DelRow-->RemoteWindowAttribute | [Attributes](arkts-arkui-remotewindow-comp-attribute.md#remotewindowattribute-system-api) of RemoteWindow. |
| UIExtensionComponentAttribute | [Attributes](arkts-arkui-uiextensioncomponent-comp-attribute.md#uiextensioncomponentattribute-system-api) of UIExtensionComponent. |
| ContainerReaderAttribute | [Attributes](arkts-arkui-containerreader-comp-attribute.md#containerreaderattribute) of ContainerReader.<br>**Since:** 26.0.0|

> **NOTE:** 
> 
> - **StepperAttribute** is supported since API version 11 and deprecated since API version 22. You are advised to use **SwiperAttribute** instead.
> 
> - **StepperItemAttribute** is supported since API version 11 and deprecated since API version 22. You are advised to use **SwiperAttribute** instead.
> 
> - **NavigatorAttribute** is supported since API version 11 and deprecated since API version 20. You are advised to use **NavigationAttribute** instead.
> 
> - **NavRouterAttribute** is supported since API version 11 and deprecated since API version 20. You are advised to use **NavigationAttribute** instead.
> 
> - **PanelAttribute** is supported since API version 11 and deprecated since API version 20. You are advised to use the universal attribute **bindSheet** instead.

**Supported attributes**

1. Attributes that accept or return a [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) are not supported.
2. Attributes whose input parameter is of the [modifier](../../../ui/arkts-user-defined-modifier.md) type are not
supported, specifically the following attribute methods: [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier), [drawModifier](arkts-arkui-common-comp-commonmethod-c.md#drawmodifier), and [gestureModifier](arkts-arkui-common-comp-commonmethod-c.md#gesturemodifier).
3. Attribute related to [animation](arkts-arkui-common-comp-commonmethod-c.md#animation) are not supported.
4. Attributes of the [gesture](../../../ui/arkts-gesture-events-binding.md) type are not supported.
5. The [stateStyles](arkts-arkui-common-comp-commonmethod-c.md#statestyles) attribute is not supported.
6. Deprecated attributes are not supported.
<!--Del-->
7. Built-in component attributes are not supported.<!--DelEnd-->

When unsupported or unimplemented attributes are used, exceptions such as "Method not implemented.", "is not callable", or "Builder is not supported." are thrown. For details about the supported scope of modifiers, see[attributeModifier Support for Attributes and Events](../../../ui/arkts-user-defined-extension-attributeModifier.md#attributemodifier-support-for-attributes-and-events).

@interface AttributeModifier&lt;T&gt;

**Since:** 11

<!--Device-unnamed-declare interface AttributeModifier<T>--><!--Device-unnamed-declare interface AttributeModifier<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## applyDisabledAttribute

```TypeScript
applyDisabledAttribute?(instance: T) : void
```

Style of a component in the disabled state. See [Example 6: Setting the Disabled State Style with a Modifier](#applydisabledattribute).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AttributeModifier-applyDisabledAttribute?(instance: T) : void--><!--Device-AttributeModifier-applyDisabledAttribute?(instance: T) : void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | T | Yes | Attribute class of the component, used to identify the component type for attribute setting, for example, the [attribute](arkts-arkui-button-comp-attribute.md#buttonattribute) (**ButtonAttribute**) of the [Button](arkts-arkui-button-comp.md) component and the [attribute](arkts-arkui-text-comp-attribute.md#textattribute) (**TextAttribute**) of the [Text](arkts-arkui-text-comp.md) component. For details about the values, see [Attribute Type Support Scope](#attribute-type-support-scope). |

## applyFocusedAttribute

```TypeScript
applyFocusedAttribute?(instance: T) : void
```

Applies the style of a component in the focused state. For the implementation example, see [Example 5: Setting the Focused State Style with a Modifier](#applyfocusedattribute).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AttributeModifier-applyFocusedAttribute?(instance: T) : void--><!--Device-AttributeModifier-applyFocusedAttribute?(instance: T) : void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | T | Yes | Attribute class of the component, used to identify the component type for attribute setting, for example, the [attribute](arkts-arkui-button-comp-attribute.md#buttonattribute) (**ButtonAttribute**) of the [Button](arkts-arkui-button-comp.md) component and the [attribute](arkts-arkui-text-comp-attribute.md#textattribute) (**TextAttribute**) of the [Text](arkts-arkui-text-comp.md) component. For details about the values, see [Attribute Type Support Scope](#attribute-type-support-scope). |

## applyHoveredAttribute

```TypeScript
applyHoveredAttribute?(instance: T) : void
```

Defines the style of a component in the hover state. See [Example 9: Implementing the Mouse Hover Effect with a Modifier](#applyhoveredattribute).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-AttributeModifier-applyHoveredAttribute?(instance: T) : void--><!--Device-AttributeModifier-applyHoveredAttribute?(instance: T) : void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | T | Yes | Component attribute class, used to identify the component type for attribute setting, for example, the [attributes](arkts-arkui-button-comp-attribute.md#buttonattribute) (ButtonAttribute) of the [Button](arkts-arkui-button-comp.md) component and the [attributes](arkts-arkui-text-comp-attribute.md#textattribute) (TextAttribute) of the [Text](arkts-arkui-text-comp.md) component. For details about the specific values, see [Attribute Type Support Scope](#attribute-type-support-scope). |

## applyNormalAttribute

```TypeScript
applyNormalAttribute?(instance: T) : void
```

Applies the style of a component in the normal state.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AttributeModifier-applyNormalAttribute?(instance: T) : void--><!--Device-AttributeModifier-applyNormalAttribute?(instance: T) : void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | T | Yes | Attribute class of the component, used to identify the component type for attribute setting, for example, the [attribute](arkts-arkui-button-comp-attribute.md#buttonattribute) (**ButtonAttribute**) of the [Button](arkts-arkui-button-comp.md) component and the [attribute](arkts-arkui-text-comp-attribute.md#textattribute) (**TextAttribute**) of the [Text](arkts-arkui-text-comp.md) component. For details about the values, see [Attribute Type Support Scope](#attribute-type-support-scope). |

## applyPressedAttribute

```TypeScript
applyPressedAttribute?(instance: T) : void
```

Applies the style of a component in the pressed state. For implementation examples, see [Example 2: Implementing the Pressed State Effect with a Modifier](#applypressedattribute) and [Example 8: Implementing the Pressed State Effect for a Custom Component with a Modifier](#applypressedattribute).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AttributeModifier-applyPressedAttribute?(instance: T) : void--><!--Device-AttributeModifier-applyPressedAttribute?(instance: T) : void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | T | Yes | Attribute class of the component, used to identify the component type for attribute setting, for example, the [attribute](arkts-arkui-button-comp-attribute.md#buttonattribute) (**ButtonAttribute**) of the [Button](arkts-arkui-button-comp.md) component and the [attribute](arkts-arkui-text-comp-attribute.md#textattribute) (**TextAttribute**) of the [Text](arkts-arkui-text-comp.md) component. For details about the values, see [Attribute Type Support Scope](#attribute-type-support-scope). |

## applySelectedAttribute

```TypeScript
applySelectedAttribute?(instance: T) : void
```

Applies the style of a component in the selected state.

You can customize the implementation of the preceding callback methods as needed, identify the component type through the passed-in parameter, set attributes on the instance, and use the **if/else** syntax for dynamic setting. See [Example 7: Setting the Selected State Style with a Modifier](#applyselectedattribute).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AttributeModifier-applySelectedAttribute?(instance: T) : void--><!--Device-AttributeModifier-applySelectedAttribute?(instance: T) : void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | T | Yes | Attribute class of the component, used to identify the component type for attribute setting, for example, the [attribute](arkts-arkui-button-comp-attribute.md#buttonattribute) (**ButtonAttribute**) of the [Button](arkts-arkui-button-comp.md) component and the [attribute](arkts-arkui-text-comp-attribute.md#textattribute) (**TextAttribute**) of the [Text](arkts-arkui-text-comp.md) component. For details about the values, see [Attribute Type Support Scope](#attribute-type-support-scope). |
