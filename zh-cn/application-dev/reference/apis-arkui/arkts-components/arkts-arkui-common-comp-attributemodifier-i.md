# AttributeModifier

```TypeScript
declare interface AttributeModifier<T>
```

开发者需要自定义class实现AttributeModifier接口。

> **说明：** 
> 
> 在以下回调函数中，当对instance对象的同一个属性重复设置相同的值或对象时，不会触发该属性的更新。

## Attribute类型支持范围

| 名称 | 说明 |  
| ----------------- | --------------- |  
| [AlphabetIndexerAttribute](arkts-arkui-alphabetindexer-comp-attribute.md) | AlphabetIndexer的[属性](arkts-arkui-alphabetindexer-comp-attribute.md)。 |
| [BadgeAttribute](arkts-arkui-badge-comp-attribute.md) | Badge的[属性](arkts-arkui-badge-comp-attribute.md)。 |
| [BlankAttribute](arkts-arkui-blank-comp-attribute.md) | Blank的[属性](arkts-arkui-blank-comp-attribute.md)。 |
| [ButtonAttribute](arkts-arkui-button-comp-attribute.md) | Button的[属性](arkts-arkui-button-comp-attribute.md)。 |
| [CalendarPickerAttribute](arkts-arkui-calendarpicker-comp-attribute.md) | CalendarPicker的[属性](arkts-arkui-calendarpicker-comp-attribute.md)。 |
| [CanvasAttribute](arkts-arkui-canvas-comp-attribute.md) | Canvas的[属性](arkts-arkui-canvas-comp-attribute.md)。 |
| [CheckboxAttribute](arkts-arkui-checkbox-comp-attribute.md) | Checkbox的[属性](arkts-arkui-checkbox-comp-attribute.md)。 |
| [CheckboxGroupAttribute](arkts-arkui-checkboxgroup-comp-attribute.md) | CheckboxGroup的[属性](arkts-arkui-checkboxgroup-comp-attribute.md)。 |
| [CircleAttribute](arkts-arkui-circle-comp-attribute.md) | Circle的[属性](arkts-arkui-circle-comp-attribute.md)。 |
| [ColumnAttribute](arkts-arkui-column-comp-attribute.md) | Column的[属性](arkts-arkui-column-comp-attribute.md)。 |
| [ColumnSplitAttribute](arkts-arkui-columnsplit-comp-attribute.md) | ColumnSplit的[属性](arkts-arkui-columnsplit-comp-attribute.md)。 |
| [CommonAttribute](arkts-arkui-common-comp-attribute.md) | Common的[属性](arkts-arkui-common-comp-attribute.md)。 |
| [CounterAttribute](arkts-arkui-counter-comp-attribute.md) | Counter的[属性](arkts-arkui-counter-comp-attribute.md)。 |
| [DataPanelAttribute](arkts-arkui-datapanel-comp-attribute.md) | DataPanel的[属性](arkts-arkui-datapanel-comp-attribute.md)。 |
| [DatePickerAttribute](arkts-arkui-datepicker-comp-attribute.md) | DatePicker的[属性](arkts-arkui-datepicker-comp-attribute.md)。 |
| [DividerAttribute](arkts-arkui-divider-comp-attribute.md) | Divider的[属性](arkts-arkui-divider-comp-attribute.md)。 |
| [EllipseAttribute](arkts-arkui-ellipse-comp-attribute.md) | Ellipse的[属性](arkts-arkui-ellipse-comp-attribute.md)。 |
| [FlexAttribute](arkts-arkui-flex-comp-attribute.md) | Flex的[属性](arkts-arkui-flex-comp-attribute.md)。 |
| [FlowItemAttribute](arkts-arkui-flowitem-comp-attribute.md) | FlowItem的[属性](arkts-arkui-flowitem-comp-attribute.md)。 |
| [FormLinkAttribute](arkts-arkui-formlink-comp-attribute.md) | FormLink的[属性](arkts-arkui-formlink-comp-attribute.md)。 |
| [GaugeAttribute](arkts-arkui-gauge-comp-attribute.md) | Gauge的[属性](arkts-arkui-gauge-comp-attribute.md)。 |
| [GridAttribute](arkts-arkui-grid-comp-attribute.md) | Grid的[属性](arkts-arkui-grid-comp-attribute.md)。 |
| [GridColAttribute](arkts-arkui-gridcol-comp-attribute.md) | GridCol的[属性](arkts-arkui-gridcol-comp-attribute.md)。 |
| [GridItemAttribute](arkts-arkui-griditem-comp-attribute.md) | GridItem的[属性](arkts-arkui-griditem-comp-attribute.md)。 |
| [GridRowAttribute](arkts-arkui-gridrow-comp-attribute.md) | GridRow的[属性](arkts-arkui-gridrow-comp-attribute.md)。 |
| [HyperlinkAttribute](arkts-arkui-hyperlink-comp-attribute.md) | Hyperlink的[属性](arkts-arkui-hyperlink-comp-attribute.md)。 |
| [IndicatorComponentAttribute](arkts-arkui-indicatorcomponent-comp-attribute.md) | IndicatorComponent的[属性](arkts-arkui-indicatorcomponent-comp-attribute.md)。 |
| [ImageAttribute](arkts-arkui-image-comp-attribute.md) | Image的[属性](arkts-arkui-image-comp-attribute.md)。 |
| [ImageAnimatorAttribute](arkts-arkui-imageanimator-comp-attribute.md) | ImageAnimator的[属性](arkts-arkui-imageanimator-comp-attribute.md)。 |
| [ImageSpanAttribute](arkts-arkui-imagespan-comp-attribute.md) | ImageSpan的[属性](arkts-arkui-imagespan-comp-attribute.md)。 |
| [ContainerSpanAttribute](arkts-arkui-containerspan-comp-attribute.md) | ContainerSpan的[属性](arkts-arkui-containerspan-comp-attribute.md)。 |
| [LineAttribute](arkts-arkui-line-comp-attribute.md) | Line的[属性](arkts-arkui-line-comp-attribute.md)。 |
| [ListAttribute](arkts-arkui-list-comp-attribute.md) | List的[属性](arkts-arkui-list-comp-attribute.md)。 |
| [ListItemAttribute](arkts-arkui-listitem-comp-attribute.md) | ListItem的[属性](arkts-arkui-listitem-comp-attribute.md)。 |
| [ListItemGroupAttribute](arkts-arkui-listitemgroup-comp-attribute.md) | ListItemGroup的[属性](arkts-arkui-listitemgroup-comp-attribute.md)。 |
| [LoadingProgressAttribute](arkts-arkui-loadingprogress-comp-attribute.md) | LoadingProgress的[属性](arkts-arkui-loadingprogress-comp-attribute.md)。 |
| [MarqueeAttribute](arkts-arkui-marquee-comp-attribute.md) | Marquee的[属性](arkts-arkui-marquee-comp-attribute.md)。 |
| [MenuAttribute](arkts-arkui-menu-comp-attribute.md) | Menu的[属性](arkts-arkui-menu-comp-attribute.md)。 |
| [MenuItemAttribute](arkts-arkui-menuitem-comp-attribute.md) | MenuItem的[属性](arkts-arkui-menuitem-comp-attribute.md)。 |
| [MenuItemGroupAttribute](arkts-arkui-menuitemgroup-comp-attribute.md) | [MenuItemGroup](arkts-arkui-menuitemgroup-comp.md#menu_item_group)的属性。 |
| [NavDestinationAttribute](arkts-arkui-navdestination-comp-attribute.md) | NavDestination的[属性](arkts-arkui-navdestination-comp-attribute.md)。 |
| [NavigationAttribute](arkts-arkui-navigation-comp-attribute.md) | Navigation的[属性](arkts-arkui-navigation-comp-attribute.md)。 |
| [NavigatorAttribute](arkts-arkui-navigator-comp-attribute.md) | Navigator的[属性](arkts-arkui-navigator-comp-attribute.md)。 |
| [NavRouterAttribute](arkts-arkui-navrouter-comp-attribute.md) | NavRouter的[属性](arkts-arkui-navrouter-comp-attribute.md)。 |
| [PanelAttribute](arkts-arkui-panel-comp-attribute.md) | Panel的[属性](arkts-arkui-panel-comp-attribute.md)。 |
| [PathAttribute](arkts-arkui-path-comp-attribute.md) | Path的[属性](arkts-arkui-path-comp-attribute.md)。 |
| [PatternLockAttribute](arkts-arkui-patternlock-comp-attribute.md) | PatternLock的[属性](arkts-arkui-patternlock-comp-attribute.md)。 |
| [PolygonAttribute](arkts-arkui-polygon-comp-attribute.md) | Polygon的[属性](arkts-arkui-polygon-comp-attribute.md)。 |
| [PolylineAttribute](arkts-arkui-polyline-comp-attribute.md) | Polyline的[属性](arkts-arkui-polyline-comp-attribute.md)。 |
| [ProgressAttribute](arkts-arkui-progress-comp-attribute.md) | Progress的[属性](arkts-arkui-progress-comp-attribute.md)。 |
| [QRCodeAttribute](arkts-arkui-qrcode-comp-attribute.md) | QRCode的[属性](arkts-arkui-qrcode-comp-attribute.md)。 |
| [RadioAttribute](arkts-arkui-radio-comp-attribute.md) | Radio的[属性](arkts-arkui-radio-comp-attribute.md)。 |
| [RatingAttribute](arkts-arkui-rating-comp-attribute.md) | Rating的[属性](arkts-arkui-rating-comp-attribute.md)。 |
| [RectAttribute](arkts-arkui-rect-comp-attribute.md) | Rect的[属性](arkts-arkui-rect-comp-attribute.md)。 |
| [RefreshAttribute](arkts-arkui-refresh-comp-attribute.md) | Refresh的[属性](arkts-arkui-refresh-comp-attribute.md)。 |
| [RelativeContainerAttribute](arkts-arkui-relativecontainer-comp-attribute.md) | RelativeContainer的[属性](arkts-arkui-relativecontainer-comp-attribute.md)。 |
| [RichEditorAttribute](arkts-arkui-richeditor-comp-attribute.md) | RichEditor的[属性](arkts-arkui-richeditor-comp-attribute.md)。 |
| [RichTextAttribute](arkts-arkui-richtext-comp-attribute.md) | RichText的[属性](arkts-arkui-richtext-comp-attribute.md)。 |
| [RowAttribute](arkts-arkui-row-comp-attribute.md) | Row的[属性](arkts-arkui-row-comp-attribute.md)。 |
| [RowSplitAttribute](arkts-arkui-rowsplit-comp-attribute.md) | RowSplit的[属性](arkts-arkui-rowsplit-comp-attribute.md)。 |
| [ScrollAttribute](arkts-arkui-scroll-comp-attribute.md) | Scroll的[属性](arkts-arkui-scroll-comp-attribute.md)。 |
| [ScrollBarAttribute](arkts-arkui-scrollbar-comp-attribute.md) | ScrollBar的[属性](arkts-arkui-scrollbar-comp-attribute.md)。 |
| [SearchAttribute](arkts-arkui-search-comp-attribute.md) | Search的[属性](arkts-arkui-search-comp-attribute.md)。 |
| [SelectAttribute](arkts-arkui-select-comp-attribute.md) | Select的[属性](arkts-arkui-select-comp-attribute.md)。 |
| [ShapeAttribute](arkts-arkui-shape-comp-attribute.md) | Shape的[属性](arkts-arkui-shape-comp-attribute.md)。 |
| [SideBarContainerAttribute](arkts-arkui-sidebarcontainer-comp-attribute.md) | SideBarContainer的[属性](arkts-arkui-sidebarcontainer-comp-attribute.md)。 |
| [SliderAttribute](arkts-arkui-slider-comp-attribute.md) | Slider的[属性](arkts-arkui-slider-comp-attribute.md)。 |
| [SpanAttribute](arkts-arkui-span-comp-attribute.md) | Span的[属性](arkts-arkui-span-comp-attribute.md)。 |
| [SymbolSpanAttribute](arkts-arkui-symbolspan-comp-attribute.md) | SymbolSpan的[属性](arkts-arkui-symbolspan-comp-attribute.md)。 |
| [StackAttribute](arkts-arkui-stack-comp-attribute.md) | Stack的[属性](arkts-arkui-stack-comp-attribute.md)。 |
| [StepperAttribute](arkts-arkui-stepper-comp-attribute.md) | Stepper的[属性](arkts-arkui-stepper-comp-attribute.md)。 |
| [StepperItemAttribute](arkts-arkui-stepperitem-comp-attribute.md) | StepperItem的[属性](arkts-arkui-stepperitem-comp-attribute.md)。 |
| [SwiperAttribute](arkts-arkui-swiper-comp-attribute.md) | Swiper的[属性](arkts-arkui-swiper-comp-attribute.md)。 |
| [SymbolGlyphAttribute](arkts-arkui-symbolglyph-comp-attribute.md) | SymbolGlyph的[属性](arkts-arkui-symbolglyph-comp-attribute.md)。 |
| [TabContentAttribute](arkts-arkui-tabcontent-comp-attribute.md) | TabContent的[属性](arkts-arkui-tabcontent-comp-attribute.md)。 |
| [TabsAttribute](arkts-arkui-tabs-comp-attribute.md) | Tabs的[属性](arkts-arkui-tabs-comp-attribute.md)。 |
| [TextAttribute](arkts-arkui-text-comp-attribute.md) | Text的[属性](arkts-arkui-text-comp-attribute.md)。 |
| [TextAreaAttribute](arkts-arkui-textarea-comp-attribute.md) | TextArea的[属性](arkts-arkui-textarea-comp-attribute.md)。 |
| [TextClockAttribute](arkts-arkui-textclock-comp-attribute.md) | TextClock的[属性](arkts-arkui-textclock-comp-attribute.md)。 |
| [TextInputAttribute](arkts-arkui-textinput-comp-attribute.md) | TextInput的[属性](arkts-arkui-textinput-comp-attribute.md)。 |
| [TextPickerAttribute](arkts-arkui-textpicker-comp-attribute.md) | TextPicker的[属性](arkts-arkui-textpicker-comp-attribute.md)。 |
| [TextTimerAttribute](arkts-arkui-texttimer-comp-attribute.md) | TextTimer的[属性](arkts-arkui-texttimer-comp-attribute.md)。 |
| [TimePickerAttribute](arkts-arkui-timepicker-comp-attribute.md) | TimePicker的[属性](arkts-arkui-timepicker-comp-attribute.md)。 |
| [ToggleAttribute](arkts-arkui-toggle-comp-attribute.md) | Toggle的[属性](arkts-arkui-toggle-comp-attribute.md)。 |
| [VideoAttribute](arkts-arkui-video-comp-attribute.md) | Video的[属性](arkts-arkui-video-comp-attribute.md)。 |
| [WaterFlowAttribute](arkts-arkui-waterflow-comp-attribute.md) | WaterFlow的[属性](arkts-arkui-waterflow-comp-attribute.md)。 |
| [XComponentAttribute](arkts-arkui-xcomponent-comp-attribute.md) | XComponent的[属性](arkts-arkui-xcomponent-comp-attribute.md)。 |
| [ParticleAttribute](arkts-arkui-particle-comp-attribute.md) | Particle的[属性](arkts-arkui-particle-comp-attribute.md)。 |
| UIPickerComponentAttribute&lt;sup&gt;22+&lt;/sup&gt; | UIPickerComponent的[属性](arkts-arkui-uipickercomponent-comp-attribute.md)。 |
| <!--DelRow-->EffectComponentAttribute | EffectComponent的[属性](arkts-arkui-effectcomponent-comp-attribute.md#effectcomponentattribute系统接口)。 |
| <!--DelRow-->FormComponentAttribute | FormComponent的[属性](arkts-arkui-formcomponent-comp-attribute.md#formcomponentattribute系统接口)。 |
| <!--DelRow-->PluginComponentAttribute | PluginComponent的[属性](arkts-arkui-plugincomponent-comp-attribute.md#plugincomponentattribute系统接口)。 |
| <!--DelRow-->RemoteWindowAttribute | RemoteWindow的[属性](arkts-arkui-remotewindow-comp-attribute.md#remotewindowattribute系统接口)。 |
| [UIExtensionComponentAttribute](arkts-arkui-uiextensioncomponent-comp-attribute.md) | UIExtensionComponent的[属性](arkts-arkui-uiextensioncomponent-comp-attribute.md#uiextensioncomponentattribute系统接口)。 |
| [ContainerReaderAttribute](arkts-arkui-containerreader-comp-attribute.md) | ContainerReader的[属性](arkts-arkui-containerreader-comp-attribute.md)。<br>**起始版本：** 26.0.0|

> **说明：** 
> StepperAttribute从API version 11开始支持，从API version 22开始废弃。建议使用SwiperAttribute替代。
> StepperItemAttribute从API version 11开始支持，从API version 22开始废弃。建议使用SwiperAttribute替代。
> NavigatorAttribute从API version 11开始支持，从API version 20开始废弃。建议使用NavigationAttribute替代。
> NavRouterAttribute从API version 11开始支持，从API version 20开始废弃。建议使用NavigationAttribute替代。
> PanelAttribute从API version 11开始支持，从API version 20开始废弃。建议使用通用属性bindSheet替代。
> **属性支持范围：**
> 
> 1. 不支持入参或者返回值为[CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)的属性。
> 2. 不支持入参为[modifier](../../../ui/arkts-user-defined-modifier.md)类型的属性，具体为以下属性方法：[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)、[drawModifier](arkts-arkui-common-comp-commonmethod-c.md#drawmodifier)和[gestureModifier](arkts-arkui-common-comp-commonmethod-c.md#gesturemodifier)。
> 3. 不支持[animation](arkts-arkui-common-comp-commonmethod-c.md#animation)属性。
> 4. 不支持[gesture](../../../ui/arkts-gesture-events-binding.md)类型的属性。
> 5. 不支持[stateStyles](arkts-arkui-common-comp-commonmethod-c.md#statestyles)属性。
> 6. 不支持已废弃属性。<!--Del-->
> 7. 不支持系统组件属性。<!--DelEnd-->不支持或者未实现的属性在使用时会抛出"Method not implemented."、"is not callable"、"Builder is not supported."等异常信息。具体Modifier支持范围可参考[属性或事件对attributeModifier的支持情况](../../../ui/arkts-user-defined-extension-attributeModifier.md#属性或事件对attributemodifier的支持情况)。

@interface AttributeModifier&lt;T&gt;

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyDisabledAttribute

```TypeScript
applyDisabledAttribute?(instance: T) : void
```

组件禁用状态的样式。参考[示例6（组件绑定Modifier禁用状态的样式）](#applydisabledattribute)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md#button)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md#text)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |

## applyFocusedAttribute

```TypeScript
applyFocusedAttribute?(instance: T) : void
```

组件获焦状态的样式。参考[示例5（组件绑定Modifier获焦样式）](#applyfocusedattribute)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md#button)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md#text)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |

## applyHoveredAttribute

```TypeScript
applyHoveredAttribute?(instance: T) : void
```

组件悬浮状态的样式。参考[示例9（组件绑定Modifier实现鼠标悬浮态效果）](#applyhoveredattribute)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md#button)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md#text)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |

## applyNormalAttribute

```TypeScript
applyNormalAttribute?(instance: T) : void
```

组件普通状态时的样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md#button)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md#text)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |

## applyPressedAttribute

```TypeScript
applyPressedAttribute?(instance: T) : void
```

组件按压状态的样式。参考[示例2（组件绑定Modifier实现按压态效果）](#applypressedattribute)、[示例8（自定义组件绑定Modifier实现按压态效果）](#applypressedattribute)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md#button)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md#text)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |

## applySelectedAttribute

```TypeScript
applySelectedAttribute?(instance: T) : void
```

组件选中状态的样式。

开发者可根据需要自定义实现上述回调方法，通过传入的参数识别组件类型，对instance设置属性，支持使用if/else语法进行动态设置。参考[示例7（组件绑定Modifier选中状态样式）](#applyselectedattribute)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md#button)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md#text)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |
