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
| AlphabetIndexerAttribute | AlphabetIndexer的[属性](arkts-arkui-alphabetindexer-comp-attribute.md)。 |
| BadgeAttribute | Badge的[属性](arkts-arkui-badge-comp-attribute.md)。 |
| BlankAttribute | Blank的[属性](arkts-arkui-blank-comp-attribute.md)。 |
| ButtonAttribute | Button的[属性](arkts-arkui-button-comp-attribute.md)。 |
| CalendarPickerAttribute | CalendarPicker的[属性](arkts-arkui-calendarpicker-comp-attribute.md)。 |
| CanvasAttribute | Canvas的[属性](arkts-arkui-canvas-comp-attribute.md)。 |
| CheckboxAttribute | Checkbox的[属性](arkts-arkui-checkbox-comp-attribute.md)。 |
| CheckboxGroupAttribute | CheckboxGroup的[属性](arkts-arkui-checkboxgroup-comp-attribute.md)。 |
| CircleAttribute | Circle的[属性](arkts-arkui-circle-comp-attribute.md)。 |
| ColumnAttribute | Column的[属性](arkts-arkui-column-comp-attribute.md)。 |
| ColumnSplitAttribute | ColumnSplit的[属性](arkts-arkui-columnsplit-comp-attribute.md)。 |
| CommonAttribute | Common的[属性](arkts-arkui-common-comp-attribute.md)。 |
| CounterAttribute | Counter的[属性](arkts-arkui-counter-comp-attribute.md)。 |
| DataPanelAttribute | DataPanel的[属性](arkts-arkui-datapanel-comp-attribute.md)。 |
| DatePickerAttribute | DatePicker的[属性](arkts-arkui-datepicker-comp-attribute.md)。 |
| DividerAttribute | Divider的[属性](arkts-arkui-divider-comp-attribute.md)。 |
| EllipseAttribute | Ellipse的[属性](arkts-arkui-ellipse-comp-attribute.md)。 |
| FlexAttribute | Flex的[属性](arkts-arkui-flex-comp-attribute.md)。 |
| FlowItemAttribute | FlowItem的[属性](arkts-arkui-flowitem-comp-attribute.md)。 |
| FormLinkAttribute | FormLink的[属性](arkts-arkui-formlink-comp-attribute.md)。 |
| GaugeAttribute | Gauge的[属性](arkts-arkui-gauge-comp-attribute.md)。 |
| GridAttribute | Grid的[属性](arkts-arkui-grid-comp-attribute.md)。 |
| GridColAttribute | GridCol的[属性](arkts-arkui-gridcol-comp-attribute.md)。 |
| GridItemAttribute | GridItem的[属性](arkts-arkui-griditem-comp-attribute.md)。 |
| GridRowAttribute | GridRow的[属性](arkts-arkui-gridrow-comp-attribute.md)。 |
| HyperlinkAttribute | Hyperlink的[属性](arkts-arkui-hyperlink-comp-attribute.md)。 |
| IndicatorComponentAttribute | IndicatorComponent的[属性](arkts-arkui-indicatorcomponent-comp-attribute.md)。 |
| ImageAttribute | Image的[属性](arkts-arkui-image-comp-attribute.md)。 |
| ImageAnimatorAttribute | ImageAnimator的[属性](arkts-arkui-imageanimator-comp-attribute.md)。 |
| ImageSpanAttribute | ImageSpan的[属性](arkts-arkui-imagespan-comp-attribute.md)。 |
| ContainerSpanAttribute | ContainerSpan的[属性](arkts-arkui-containerspan-comp-attribute.md)。 |
| LineAttribute | Line的[属性](arkts-arkui-line-comp-attribute.md)。 |
| ListAttribute | List的[属性](arkts-arkui-list-comp-attribute.md)。 |
| ListItemAttribute | ListItem的[属性](arkts-arkui-listitem-comp-attribute.md)。 |
| ListItemGroupAttribute | ListItemGroup的[属性](arkts-arkui-listitemgroup-comp-attribute.md)。 |
| LoadingProgressAttribute | LoadingProgress的[属性](arkts-arkui-loadingprogress-comp-attribute.md)。 |
| MarqueeAttribute | Marquee的[属性](arkts-arkui-marquee-comp-attribute.md)。 |
| MenuAttribute | Menu的[属性](arkts-arkui-menu-comp-attribute.md)。 |
| MenuItemAttribute | MenuItem的[属性](arkts-arkui-menuitem-comp-attribute.md)。 |
| MenuItemGroupAttribute | [MenuItemGroup](arkts-arkui-menuitemgroup-comp.md)的属性。 |
| NavDestinationAttribute | NavDestination的[属性](arkts-arkui-navdestination-comp-attribute.md)。 |
| NavigationAttribute | Navigation的[属性](arkts-arkui-navigation-comp-attribute.md)。 |
| NavigatorAttribute | Navigator的[属性](arkts-arkui-navigator-comp-attribute.md)。 |
| NavRouterAttribute | NavRouter的[属性](arkts-arkui-navrouter-comp-attribute.md)。 |
| PanelAttribute | Panel的[属性](arkts-arkui-panel-comp-attribute.md)。 |
| PathAttribute | Path的[属性](arkts-arkui-path-comp-attribute.md)。 |
| PatternLockAttribute | PatternLock的[属性](arkts-arkui-patternlock-comp-attribute.md)。 |
| PolygonAttribute | Polygon的[属性](arkts-arkui-polygon-comp-attribute.md)。 |
| PolylineAttribute | Polyline的[属性](arkts-arkui-polyline-comp-attribute.md)。 |
| ProgressAttribute | Progress的[属性](arkts-arkui-progress-comp-attribute.md)。 |
| QRCodeAttribute | QRCode的[属性](arkts-arkui-qrcode-comp-attribute.md)。 |
| RadioAttribute | Radio的[属性](arkts-arkui-radio-comp-attribute.md)。 |
| RatingAttribute | Rating的[属性](arkts-arkui-rating-comp-attribute.md)。 |
| RectAttribute | Rect的[属性](arkts-arkui-rect-comp-attribute.md)。 |
| RefreshAttribute | Refresh的[属性](arkts-arkui-refresh-comp-attribute.md)。 |
| RelativeContainerAttribute | RelativeContainer的[属性](arkts-arkui-relativecontainer-comp-attribute.md)。 |
| RichEditorAttribute | RichEditor的[属性](arkts-arkui-richeditor-comp-attribute.md)。 |
| RichTextAttribute | RichText的[属性](arkts-arkui-richtext-comp-attribute.md)。 |
| RowAttribute | Row的[属性](arkts-arkui-row-comp-attribute.md)。 |
| RowSplitAttribute | RowSplit的[属性](arkts-arkui-rowsplit-comp-attribute.md)。 |
| ScrollAttribute | Scroll的[属性](arkts-arkui-scroll-comp-attribute.md)。 |
| ScrollBarAttribute | ScrollBar的[属性](arkts-arkui-scrollbar-comp-attribute.md)。 |
| SearchAttribute | Search的[属性](arkts-arkui-search-comp-attribute.md)。 |
| SelectAttribute | Select的[属性](arkts-arkui-select-comp-attribute.md)。 |
| ShapeAttribute | Shape的[属性](arkts-arkui-shape-comp-attribute.md)。 |
| SideBarContainerAttribute | SideBarContainer的[属性](arkts-arkui-sidebarcontainer-comp-attribute.md)。 |
| SliderAttribute | Slider的[属性](arkts-arkui-slider-comp-attribute.md)。 |
| SpanAttribute | Span的[属性](arkts-arkui-span-comp-attribute.md)。 |
| SymbolSpanAttribute | SymbolSpan的[属性](arkts-arkui-symbolspan-comp-attribute.md)。 |
| StackAttribute | Stack的[属性](arkts-arkui-stack-comp-attribute.md)。 |
| StepperAttribute | Stepper的[属性](arkts-arkui-stepper-comp-attribute.md)。 |
| StepperItemAttribute | StepperItem的[属性](arkts-arkui-stepperitem-comp-attribute.md)。 |
| SwiperAttribute | Swiper的[属性](arkts-arkui-swiper-comp-attribute.md)。 |
| SymbolGlyphAttribute | SymbolGlyph的[属性](arkts-arkui-symbolglyph-comp-attribute.md)。 |
| TabContentAttribute | TabContent的[属性](arkts-arkui-tabcontent-comp-attribute.md)。 |
| TabsAttribute | Tabs的[属性](arkts-arkui-tabs-comp-attribute.md)。 |
| TextAttribute | Text的[属性](arkts-arkui-text-comp-attribute.md)。 |
| TextAreaAttribute | TextArea的[属性](arkts-arkui-textarea-comp-attribute.md)。 |
| TextClockAttribute | TextClock的[属性](arkts-arkui-textclock-comp-attribute.md)。 |
| TextInputAttribute | TextInput的[属性](arkts-arkui-textinput-comp-attribute.md)。 |
| TextPickerAttribute | TextPicker的[属性](arkts-arkui-textpicker-comp-attribute.md)。 |
| TextTimerAttribute | TextTimer的[属性](arkts-arkui-texttimer-comp-attribute.md)。 |
| TimePickerAttribute | TimePicker的[属性](arkts-arkui-timepicker-comp-attribute.md)。 |
| ToggleAttribute | Toggle的[属性](arkts-arkui-toggle-comp-attribute.md)。 |
| VideoAttribute | Video的[属性](arkts-arkui-video-comp-attribute.md)。 |
| WaterFlowAttribute | WaterFlow的[属性](arkts-arkui-waterflow-comp-attribute.md)。 |
| XComponentAttribute | XComponent的[属性](arkts-arkui-xcomponent-comp-attribute.md)。 |
| ParticleAttribute | Particle的[属性](arkts-arkui-particle-comp-attribute.md)。 |
| UIPickerComponentAttribute&lt;sup&gt;22+&lt;/sup&gt; | UIPickerComponent的[属性](arkts-arkui-uipickercomponent-comp-attribute.md)。 |
| <!--DelRow-->EffectComponentAttribute | EffectComponent的[属性](arkts-arkui-effectcomponent-comp-attribute.md#effectcomponentattribute系统接口)。 |
| <!--DelRow-->FormComponentAttribute | FormComponent的[属性](arkts-arkui-formcomponent-comp-attribute.md#formcomponentattribute系统接口)。 |
| <!--DelRow-->PluginComponentAttribute | PluginComponent的[属性](arkts-arkui-plugincomponent-comp-attribute.md#plugincomponentattribute系统接口)。 |
| <!--DelRow-->RemoteWindowAttribute | RemoteWindow的[属性](arkts-arkui-remotewindow-comp-attribute.md#remotewindowattribute系统接口)。 |
| UIExtensionComponentAttribute | UIExtensionComponent的[属性](arkts-arkui-uiextensioncomponent-comp-attribute.md#uiextensioncomponentattribute系统接口)。 |
| ContainerReaderAttribute | ContainerReader的[属性](arkts-arkui-containerreader-comp-attribute.md)。<br>**起始版本：** 26.0.0|

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

<!--Device-unnamed-declare interface AttributeModifier<T>--><!--Device-unnamed-declare interface AttributeModifier<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyDisabledAttribute

```TypeScript
applyDisabledAttribute?(instance: T) : void
```

组件禁用状态的样式。参考[示例6（组件绑定Modifier禁用状态的样式）](#applydisabledattribute)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AttributeModifier-applyDisabledAttribute?(instance: T) : void--><!--Device-AttributeModifier-applyDisabledAttribute?(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |

## applyFocusedAttribute

```TypeScript
applyFocusedAttribute?(instance: T) : void
```

组件获焦状态的样式。参考[示例5（组件绑定Modifier获焦样式）](#applyfocusedattribute)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AttributeModifier-applyFocusedAttribute?(instance: T) : void--><!--Device-AttributeModifier-applyFocusedAttribute?(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |

## applyHoveredAttribute

```TypeScript
applyHoveredAttribute?(instance: T) : void
```

组件悬浮状态的样式。参考[示例9（组件绑定Modifier实现鼠标悬浮态效果）](#applyhoveredattribute)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-AttributeModifier-applyHoveredAttribute?(instance: T) : void--><!--Device-AttributeModifier-applyHoveredAttribute?(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |

## applyNormalAttribute

```TypeScript
applyNormalAttribute?(instance: T) : void
```

组件普通状态时的样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AttributeModifier-applyNormalAttribute?(instance: T) : void--><!--Device-AttributeModifier-applyNormalAttribute?(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |

## applyPressedAttribute

```TypeScript
applyPressedAttribute?(instance: T) : void
```

组件按压状态的样式。参考[示例2（组件绑定Modifier实现按压态效果）](#applypressedattribute)、[示例8（自定义组件绑定Modifier实现按压态效果）](#applypressedattribute)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AttributeModifier-applyPressedAttribute?(instance: T) : void--><!--Device-AttributeModifier-applyPressedAttribute?(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |

## applySelectedAttribute

```TypeScript
applySelectedAttribute?(instance: T) : void
```

组件选中状态的样式。

开发者可根据需要自定义实现上述回调方法，通过传入的参数识别组件类型，对instance设置属性，支持使用if/else语法进行动态设置。参考[示例7（组件绑定Modifier选中状态样式）](#applyselectedattribute)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AttributeModifier-applySelectedAttribute?(instance: T) : void--><!--Device-AttributeModifier-applySelectedAttribute?(instance: T) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | 组件的属性类，用来标识进行属性设置的组件的类型，比如[Button](arkts-arkui-button-comp.md)组件的[属性](arkts-arkui-button-comp-attribute.md)（ButtonAttribute），[Text](arkts-arkui-text-comp.md)组件的[属性](arkts-arkui-text-comp-attribute.md)（TextAttribute）等。具体取值请参考[Attribute类型支持范围](#attribute类型支持范围)。 |
