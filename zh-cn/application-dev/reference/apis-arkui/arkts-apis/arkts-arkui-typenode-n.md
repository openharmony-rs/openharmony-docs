# typeNode

typeNode提供创建具体类型的FrameNode能力，可通过FrameNode的基础接口进行自定义的挂载，使用占位容器进行显示。适用于需要通过代码动态创建具体类型组件节点并进行自定义挂载的场景。使用typeNode创建Text、Image、 Select、Toggle节点时，当传入的 [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)对应的UI实例销毁后，调用该接口会返回一个无效的FrameNode节点，无法正常挂载和显示。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Text类型的FrameNode节点。使用typeNode创建Text节点时，当传入的UIContext对应的UI实例销毁后，调用该接口会返回一个无效的FrameNode节点，无法正常挂载和显示。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Text节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md) | 将文本控制器[TextController](../arkts-components/arkts-arkui-textcontroller-c.md)绑定到[Text](arkts-arkui-typenode-text-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言 访问，则抛出异常。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Column类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Column节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Row类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Row节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Stack类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Stack节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建GridRow类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建GridCol类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Flex类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Flex节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Swiper类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Swiper节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md) | 将控制器[SwiperController](../arkts-components/arkts-arkui-swipercontroller-c.md)绑定到[Swiper](arkts-arkui-typenode-swiper-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果 不支持跨语言访问，则抛出异常。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Progress类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Progress节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Scroll类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Scroll节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [getEvent](arkts-arkui-typenode-getevent-f.md) | 获取Scroll节点中持有的UIScrollEvent对象，用于设置滚动事件。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。设置的滚动 事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。 |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md) | 将滚动控制器[Scroller](../arkts-components/arkts-arkui-scroller-c.md)绑定到[Scroll](arkts-arkui-typenode-scroll-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异 常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建RelativeContainer类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取RelativeContainer节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Divider类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建LoadingProgress类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取LoadingProgress节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访 问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Search类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Blank类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Image类型的FrameNode节点。使用typeNode创建Image节点时，当传入的UIContext对应的UI实例销毁后，调用该接口会返回一个无效的FrameNode节点，无法正常挂载和显示。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Image节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建List类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取List节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md) | 将滚动控制器[Scroller](../arkts-components/arkts-arkui-scroller-c.md)绑定到[List](arkts-arkui-typenode-list-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从 API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。 |
| [getEvent](arkts-arkui-typenode-getevent-f.md) | 获取List节点中持有的UIListEvent对象，用于设置滚动事件。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。设置的滚动事件与声 明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建ListItem类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取ListItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建TextInput类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取TextInput节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md) | 将输入框控制器[TextInputController](../arkts-components/arkts-arkui-textinputcontroller-c.md)绑定到[TextInput](arkts-arkui-typenode-textinput-t.md)节点。若该节点非ArkTS语言创建，则需 要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从API版本26.0.0开始，该接口支持声明式方式创建的节点，API版本26.0.0以下版本不支持。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Button类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Button节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建ListItemGroup类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取ListItemGroup节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建WaterFlow类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取WaterFlow节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md) | 将滚动控制器[Scroller](../arkts-components/arkts-arkui-scroller-c.md)绑定到[WaterFlow](arkts-arkui-typenode-waterflow-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访 问，则抛出异常。从API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。 |
| [getEvent](arkts-arkui-typenode-getevent-f.md) | 获取[WaterFlow](arkts-arkui-typenode-waterflow-t.md)节点中持有的UIWaterFlowEvent对象，用于设置滚动事件。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则 返回undefined。该接口不支持声明式方式创建的节点。设置的滚动事件与声明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建FlowItem类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取FlowItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建XComponent类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 按照options中的配置参数创建XComponent类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 按照parameters中的配置参数创建XComponent类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取XComponent节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Checkbox类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Checkbox节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建CheckboxGroup类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Radio类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Radio节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Rating类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Select类型的FrameNode节点。使用typeNode创建Select节点时，当传入的UIContext对应的UI实例销毁后，调用该接口会返回一个无效的FrameNode节点，无法正常挂载和显示。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Slider类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Slider节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Toggle类型的FrameNode节点。使用typeNode创建Toggle节点时，当传入的UIContext对应的UI实例销毁后，调用该接口会返回一个无效的FrameNode节点，无法正常挂载和显示。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Toggle节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Marquee类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建TextArea类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取TextArea节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md) | 将输入框控制器[TextAreaController](../arkts-components/arkts-arkui-textareacontroller-c.md)绑定到[TextArea](arkts-arkui-typenode-textarea-t.md)节点。若该节点非ArkTS语言创建，则需要设置是 否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从API版本26.0.0开始，该接口支持声明式方式创建的节点，API版本26.0.0以下版本不支持。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建SymbolGlyph类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建QRCode类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Badge类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建TextClock类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建TextTimer类型的FrameNode节点。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建Grid类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取Grid节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |
| [bindController](arkts-arkui-typenode-bindcontroller-f.md) | 将滚动控制器[Scroller](../arkts-components/arkts-arkui-scroller-c.md)绑定到[Grid](arkts-arkui-typenode-grid-t.md)节点。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则抛出异常。从 API version 26.0.0开始，该接口支持声明式方式创建的节点，API version 26.0.0以下版本不支持。 |
| [getEvent](arkts-arkui-typenode-getevent-f.md) | 获取Grid节点中持有的UIGridEvent对象，用于设置滚动事件。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。设置的滚动事件与声 明式定义的事件平行；设置的滚动事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。 |
| [createNode](arkts-arkui-typenode-createnode-f.md) | 创建GridItem类型的FrameNode节点。 |
| [getAttribute](arkts-arkui-typenode-getattribute-f.md) | 获取GridItem节点的属性。若该节点非ArkTS语言创建，则需要设置是否支持跨语言访问，如果不支持跨语言访问，则返回undefined。该接口不支持声明式方式创建的节点。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Text](arkts-arkui-typenode-text-t.md) | Text类型的FrameNode节点类型。不允许添加子组件。 |
| [Column](arkts-arkui-typenode-column-t.md) | Column类型的FrameNode节点类型。 |
| [Row](arkts-arkui-typenode-row-t.md) | Row类型的FrameNode节点类型。 |
| [Stack](arkts-arkui-typenode-stack-t.md) | Stack类型的FrameNode节点类型。 |
| [GridRow](arkts-arkui-typenode-gridrow-t.md) | GridRow类型的FrameNode节点类型。只允许添加GridCol类型子组件。 |
| [GridCol](arkts-arkui-typenode-gridcol-t.md) | GridCol类型的FrameNode节点类型。不允许添加子组件。 |
| [Flex](arkts-arkui-typenode-flex-t.md) | Flex类型的FrameNode节点类型。 |
| [Swiper](arkts-arkui-typenode-swiper-t.md) | Swiper类型的FrameNode节点类型。 |
| [Progress](arkts-arkui-typenode-progress-t.md) | Progress类型的FrameNode节点类型。不允许添加子组件。 |
| [Scroll](arkts-arkui-typenode-scroll-t.md) | Scroll类型的FrameNode节点类型。允许添加一个子组件。 |
| [RelativeContainer](arkts-arkui-typenode-relativecontainer-t.md) | RelativeContainer类型的FrameNode节点类型。 |
| [Divider](arkts-arkui-typenode-divider-t.md) | Divider类型的FrameNode节点类型。不允许添加子组件。 |
| [LoadingProgress](arkts-arkui-typenode-loadingprogress-t.md) | LoadingProgress类型的FrameNode节点类型。不允许添加子组件。 |
| [Search](arkts-arkui-typenode-search-t.md) | Search类型的FrameNode节点类型。 |
| [Blank](arkts-arkui-typenode-blank-t.md) | Blank类型的FrameNode节点类型。不允许添加子组件。 |
| [Image](arkts-arkui-typenode-image-t.md) | Image类型的FrameNode节点类型。不允许添加子组件。 |
| [List](arkts-arkui-typenode-list-t.md) | List类型的FrameNode节点类型。只允许添加[ListItem](arkts-arkui-typenode-listitem-t.md)、[ListItemGroup](arkts-arkui-typenode-listitemgroup-t.md)类型子组件。 |
| [ListItem](arkts-arkui-typenode-listitem-t.md) | ListItem类型的FrameNode节点类型。 |
| [TextInput](arkts-arkui-typenode-textinput-t.md) | TextInput类型的FrameNode节点类型。 |
| [Button](arkts-arkui-typenode-button-t.md) | Button类型的FrameNode节点类型。以子组件模式创建允许添加一个子组件。以label模式创建不可以添加子组件。 |
| [ListItemGroup](arkts-arkui-typenode-listitemgroup-t.md) | ListItemGroup类型的FrameNode节点类型。只允许添加ListItem类型子组件。 |
| [WaterFlow](arkts-arkui-typenode-waterflow-t.md) | WaterFlow类型的FrameNode节点类型。只允许添加FlowItem类型子组件。 |
| [FlowItem](arkts-arkui-typenode-flowitem-t.md) | FlowItem类型的FrameNode节点类型。允许添加一个子组件。 |
| [XComponent](arkts-arkui-typenode-xcomponent-t.md) | XComponent类型的FrameNode节点类型。 |
| [Checkbox](arkts-arkui-typenode-checkbox-t.md) | Checkbox类型的FrameNode节点类型。 |
| [CheckboxGroup](arkts-arkui-typenode-checkboxgroup-t.md) | CheckboxGroup类型的FrameNode节点类型。 |
| [Radio](arkts-arkui-typenode-radio-t.md) | Radio类型的FrameNode节点类型。 |
| [Rating](arkts-arkui-typenode-rating-t.md) | Rating类型的FrameNode节点类型。 |
| [Select](arkts-arkui-typenode-select-t.md) | Select类型的FrameNode节点类型。 |
| [Slider](arkts-arkui-typenode-slider-t.md) | Slider类型的FrameNode节点类型。 |
| [Toggle](arkts-arkui-typenode-toggle-t.md) | Toggle类型的FrameNode节点类型。 |
| [Marquee](arkts-arkui-typenode-marquee-t.md) | Marquee类型的FrameNode节点类型。 |
| [TextArea](arkts-arkui-typenode-textarea-t.md) | TextArea类型的FrameNode节点类型。 |
| [SymbolGlyph](arkts-arkui-typenode-symbolglyph-t.md) | SymbolGlyph类型的FrameNode节点类型。 |
| [QRCode](arkts-arkui-typenode-qrcode-t.md) | QRCode类型的FrameNode节点类型。 |
| [Badge](arkts-arkui-typenode-badge-t.md) | Badge类型的FrameNode节点类型。 |
| [TextClock](arkts-arkui-typenode-textclock-t.md) | TextClock类型的FrameNode节点类型。 |
| [TextTimer](arkts-arkui-typenode-texttimer-t.md) | TextTimer类型的FrameNode节点类型。 |
| [Grid](arkts-arkui-typenode-grid-t.md) | Grid类型的FrameNode节点类型。 |
| [GridItem](arkts-arkui-typenode-griditem-t.md) | GridItem类型的FrameNode节点类型。 |
