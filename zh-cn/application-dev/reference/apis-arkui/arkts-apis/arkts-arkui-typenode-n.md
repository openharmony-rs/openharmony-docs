# typeNode

typeNode提供创建具体类型的FrameNode能力，可通过FrameNode的基础接口进行自定义的挂载，使用占位容器进行显示。

使用typeNode创建[Text](../../apis-arkgraphics2d/arkts-apis/arkts-graphics-text.md)、[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)、[Select](../arkts-components/arkts-arkui-select.md)、[Toggle](../arkts-components/arkts-arkui-toggle.md)节点时，当传入的
[UIContext](arkts-arkui-uicontext.md)对应的UI实例销毁后，调用该接口会返回一个无效的FrameNode节点，无法正常挂载和显示。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createNode](arkts-arkui-createnode-f.md#createnode-1) | 创建Text类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-1) | 获取Text节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-bindcontroller-f.md#bindcontroller-1) | 将文本控制器[TextController](../arkts-components/arkts-arkui-textcontroller-c.md)绑定到[Text](arkts-arkui-text-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-2) | 创建Column类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-2) | 获取Column节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-3) | 创建Row类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-3) | 获取Row节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-4) | 创建Stack类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-4) | 获取Stack节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-5) | 创建GridRow类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-6) | 创建GridCol类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-7) | 创建Flex类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-5) | 获取Flex节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-8) | 创建Swiper类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-6) | 获取Swiper节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-bindcontroller-f.md#bindcontroller-2) | 将控制器[SwiperController](../arkts-components/arkts-arkui-swipercontroller-c.md)绑定到[Swiper](arkts-arkui-swiper-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-9) | 创建Progress类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-7) | 获取Progress节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-10) | 创建Scroll类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-8) | 获取Scroll节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [getEvent](arkts-arkui-getevent-f.md#getevent-1) | 获取Scroll节点中持有的UIScrollEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。 |
| [bindController](arkts-arkui-bindcontroller-f.md#bindcontroller-3) | 将滚动控制器[Scroller](../arkts-components/arkts-arkui-scroller-c.md)绑定到[Scroll](arkts-arkui-scroll-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-11) | 创建RelativeContainer类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-9) | 获取RelativeContainer节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-12) | 创建Divider类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-13) | 创建LoadingProgress类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-10) | 获取[LoadingProgress](../arkts-components/arkts-arkui-loadingprogress.md)节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-14) | 创建Search类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-15) | 创建Blank类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-16) | 创建Image类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-11) | 获取Image节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-17) | 创建List类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-12) | 获取List节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-bindcontroller-f.md#bindcontroller-4) | 将滚动控制器[Scroller](../arkts-components/arkts-arkui-scroller-c.md)绑定到[List](arkts-arkui-list-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。 |
| [getEvent](arkts-arkui-getevent-f.md#getevent-2) | 获取List节点中持有的UIListEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-18) | 创建ListItem类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-13) | 获取ListItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-19) | 创建TextInput类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-14) | 获取TextInput节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-bindcontroller-f.md#bindcontroller-5) | 将输入框控制器[TextInputController](../arkts-components/arkts-arkui-textinputcontroller-c.md)绑定到[TextInput](arkts-arkui-textinput-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口从API版本26.0.0开始支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-20) | 创建Button类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-15) | 获取Button节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-21) | 创建ListItemGroup类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-16) | 获取ListItemGroup节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-22) | 创建WaterFlow类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-17) | 获取WaterFlow节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-bindcontroller-f.md#bindcontroller-6) | 将滚动控制器[Scroller](../arkts-components/arkts-arkui-scroller-c.md)绑定到[WaterFlow](arkts-arkui-waterflow-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。 |
| [getEvent](arkts-arkui-getevent-f.md#getevent-3) | 获取[WaterFlow](arkts-arkui-waterflow-t.md)节点中持有的UIWaterFlowEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-23) | 创建FlowItem类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-18) | 获取FlowItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-24) | 创建XComponent类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-25) | 按照options中的配置参数创建XComponent类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-26) | 按照parameters中的配置参数创建XComponent类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-19) | 获取XComponent节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-27) | 创建Checkbox类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-20) | 获取Checkbox节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-28) | 创建CheckboxGroup类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-29) | 创建Radio类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-21) | 获取Radio节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-30) | 创建Rating类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-31) | 创建Select类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-32) | 创建Slider类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-22) | 获取Slider节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-33) | 创建Toggle类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-23) | 获取Toggle节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-34) | 创建Marquee类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-35) | 创建TextArea类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-24) | 获取TextArea节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-bindcontroller-f.md#bindcontroller-7) | 将输入框控制器[TextAreaController](../arkts-components/arkts-arkui-textareacontroller-c.md)绑定到[TextArea](arkts-arkui-textarea-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。该接口从API版本26.0.0开始支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-36) | 创建SymbolGlyph类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-37) | 创建QRCode类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-38) | 创建Badge类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-39) | 创建TextClock类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-40) | 创建TextTimer类型的FrameNode节点。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-41) | 创建Grid类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-25) | 获取Grid节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-bindcontroller-f.md#bindcontroller-8) | 将滚动控制器[Scroller](../arkts-components/arkts-arkui-scroller-c.md)绑定到[Grid](arkts-arkui-grid-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。 |
| [getEvent](arkts-arkui-getevent-f.md#getevent-4) | 获取Grid节点中持有的UIGridEvent对象，用于设置滚动事件。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。 |
| [createNode](arkts-arkui-createnode-f.md#createnode-42) | 创建GridItem类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-getattribute-f.md#getattribute-26) | 获取GridItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Text](arkts-arkui-text-t.md) | Text类型的FrameNode节点类型。不允许添加子组件。 |
| [Column](arkts-arkui-column-t.md) | Column类型的FrameNode节点类型。 |
| [Row](arkts-arkui-row-t.md) | Row类型的FrameNode节点类型。 |
| [Stack](arkts-arkui-stack-t.md) | Stack类型的FrameNode节点类型。 |
| [GridRow](arkts-arkui-gridrow-t.md) | GridRow类型的FrameNode节点类型。只允许添加GridCol类型子组件。 |
| [GridCol](arkts-arkui-gridcol-t.md) | GridCol类型的FrameNode节点类型。不允许添加子组件。 |
| [Flex](arkts-arkui-flex-t.md) | Flex类型的FrameNode节点类型。 |
| [Swiper](arkts-arkui-swiper-t.md) | Swiper类型的FrameNode节点类型。 |
| [Progress](arkts-arkui-progress-t.md) | Progress类型的FrameNode节点类型。不允许添加子组件。 |
| [Scroll](arkts-arkui-scroll-t.md) | Scroll类型的FrameNode节点类型。允许添加一个子组件。 |
| [RelativeContainer](arkts-arkui-relativecontainer-t.md) | RelativeContainer类型的FrameNode节点类型。 |
| [Divider](arkts-arkui-divider-t.md) | Divider类型的FrameNode节点类型。不允许添加子组件。 |
| [LoadingProgress](arkts-arkui-loadingprogress-t.md) | LoadingProgress类型的FrameNode节点类型。不允许添加子组件。 |
| [Search](arkts-arkui-search-t.md) | Search类型的FrameNode节点类型。 |
| [Blank](arkts-arkui-blank-t.md) | Blank类型的FrameNode节点类型。不允许添加子组件。 |
| [Image](arkts-arkui-image-t.md) | Image类型的FrameNode节点类型。不允许添加子组件。 |
| [List](arkts-arkui-list-t.md) | List类型的FrameNode节点类型。只允许添加[ListItem](arkts-arkui-listitem-t.md)、[ListItemGroup](arkts-arkui-listitemgroup-t.md)类型子组件。 |
| [ListItem](arkts-arkui-listitem-t.md) | ListItem类型的FrameNode节点类型。 |
| [TextInput](arkts-arkui-textinput-t.md) | TextInput类型的FrameNode节点类型。 |
| [Button](arkts-arkui-button-t.md) | Button类型的FrameNode节点类型。以子组件模式创建允许添加一个子组件。以label模式创建不可以添加子组件。 |
| [ListItemGroup](arkts-arkui-listitemgroup-t.md) | ListItemGroup类型的FrameNode节点类型。只允许添加[ListItem](../arkts-components/arkts-arkui-listitem.md)类型子组件。 |
| [WaterFlow](arkts-arkui-waterflow-t.md) | WaterFlow类型的FrameNode节点类型。只允许添加[FlowItem](../arkts-components/arkts-arkui-flowitem.md)类型子组件。 |
| [FlowItem](arkts-arkui-flowitem-t.md) | FlowItem类型的FrameNode节点类型。允许添加一个子组件。 |
| [XComponent](arkts-arkui-xcomponent-t.md) | XComponent类型的FrameNode节点类型。 |
| [Checkbox](arkts-arkui-checkbox-t.md) | Checkbox类型的FrameNode节点类型。 |
| [CheckboxGroup](arkts-arkui-checkboxgroup-t.md) | CheckboxGroup类型的FrameNode节点类型。 |
| [Radio](arkts-arkui-radio-t.md) | Radio类型的FrameNode节点类型。 |
| [Rating](arkts-arkui-rating-t.md) | Rating类型的FrameNode节点类型。 |
| [Select](arkts-arkui-select-t.md) | Select类型的FrameNode节点类型。 |
| [Slider](arkts-arkui-slider-t.md) | Slider类型的FrameNode节点类型。 |
| [Toggle](arkts-arkui-toggle-t.md) | [Toggle](../arkts-components/arkts-arkui-toggle.md)类型的FrameNode节点类型。 |
| [Marquee](arkts-arkui-marquee-t.md) | Marquee类型的FrameNode节点类型。 |
| [TextArea](arkts-arkui-textarea-t.md) | TextArea类型的FrameNode节点类型。 |
| [SymbolGlyph](arkts-arkui-symbolglyph-t.md) | SymbolGlyph类型的FrameNode节点类型。 |
| [QRCode](arkts-arkui-qrcode-t.md) | QRCode类型的FrameNode节点类型。 |
| [Badge](arkts-arkui-badge-t.md) | Badge类型的FrameNode节点类型。 |
| [TextClock](arkts-arkui-textclock-t.md) | TextClock类型的FrameNode节点类型。 |
| [TextTimer](arkts-arkui-texttimer-t.md) | TextTimer类型的FrameNode节点类型。 |
| [Grid](arkts-arkui-grid-t.md) | Grid类型的FrameNode节点类型。 |
| [GridItem](arkts-arkui-griditem-t.md) | GridItem类型的FrameNode节点类型。 |

