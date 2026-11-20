# 监听页面变化事件

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 简介

从API版本26.1.0开始，应用可以通过ArkUI NDK接口为自身UI实例注册监听页面显著变化事件，在回调中获取页面变化事件及其时间戳。页面内容的显著变化事件会在事件相关动效完成时回调开发者，是UI感知的重要信息来源，应用在智能化场景或自动化运维测试场景中，可以据此判断界面发生变化并进入稳定状态，再决定后续的控件树采集或命令注入操作。

页面变化事件监听具有以下特点。

- 仅上报页面、滚动和浮层三类稳定状态变化的开始、结束、取消等关键事件，不上报动画过程帧、逐帧滚动偏移及页面中的微小内容更新。
- 事件以只读快照形式在回调中交付，应用可在回调内读取事件类型、时间戳、所属UI上下文和事件详情JSON。
- 注册和注销接口仅限在目标UI实例的UI线程调用，从非UI线程调用会导致进程终止；回调也在该UI实例的UI线程上同步触发。

支持监听的事件类别参见[事件类别与忽略类型](#事件类别与忽略类型)。

## 约束与限制

使用页面变化事件监听能力前，需要确认调用线程、绑定上下文、事件数据有效期，以及不同组件的上报差异。

### 调用线程与上下文

注册、注销和回调执行均与目标UI实例的UI线程及UI上下文绑定。

- 注册和注销接口必须在目标UI实例的UI线程调用；从非UI线程调用会导致进程终止。
- 回调在注册时指定UI上下文关联的UI线程上同步执行。回调内不要执行耗时操作，避免阻塞UI线程。
- 同一订阅只接收注册时传入UI上下文的事件；多窗口场景需为每个UI实例分别注册，并在回调中通过读取的上下文区分事件归属。
- 注册返回的订阅ID在其所属UI上下文内唯一，注销时须传入注册时的同一上下文和对应订阅ID。
- 页面或窗口销毁后，该UI上下文的全部订阅停止回调，请勿使用失效的UI上下文注册新订阅。

### 回调参数生命周期

事件回调的类型为[OH_ArkUI_NativeModule_UIContentChangeEventCallback](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcallback)。回调收到的参数对象将在回调函数退出后销毁，应当在回调内处理。保存回调收到的参数对象并在回调返回后继续使用，可能导致程序崩溃。

- 回调参数中的JSON对象生命周期由框架管理，框架会在回调返回后销毁该对象，通过[OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgetcontentchangeeventjson)取得该JSON的引用，请勿对其调用[OH_ArkUI_NativeModule_UIJsonWrapperDestroy](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrapperdestroy)，否则会造成重复销毁，导致崩溃。需要保留内容时，在回调内复制字符串数据。
- userData的生命周期由应用管理，框架仅原样回传，不访问也不释放。应用须保证userData在订阅存续期间有效；注销成功且无活跃回调使用后，才可释放。

### UI显著变化事件的上报规格

一般情况下，页面切换、滚动和浮层显隐等稳定状态变化会成对上报开始与结束事件。为兼顾性能与信息有效性，ArkUI对一些上报场景做了特殊处理，详见下文。

1. Swiper开启autoPlay时不上报事件。[Swiper](../reference/apis-arkui/arkui-ts/ts-container-swiper.md)开启[autoPlay](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#autoplay)期间，该Swiper的全部切换事件（SWIPER_START、SWIPER_END、SWIPER_CANCEL）不上报，以避免自动翻页造成高频回调。自动翻页、手势滑动、属性或控制器切换在此期间同样不上报。需要接收事件时，应关闭autoPlay，之后新的切换事件恢复正常上报。

2. scrollTo、scrollBy等自动化滚动默认上报，可配置参数过滤。开发者通过[scrollTo](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#scrollto)、[scrollBy](../reference/apis-arkui/arkui-ts/ts-container-scroll.md#scrollby9)、scrollToIndex、scrollToItemInGroup等接口实现自动化滚动时，这些滚动默认作为滚动事件上报，与手势滚动的判定规则一致。为避免自动化滚动高频触发回调，注册时可在ignoreMask中设置对应忽略位，其中IGNORE_SCROLLTO过滤滚动到指定位置类命令（scrollTo、scrollToIndex、scrollToItemInGroup等定位来源）触发的完整滚动事件，IGNORE_SCROLLBY过滤scrollBy位移类命令触发的完整滚动事件。忽略位按命令来源逐项生效，只过滤对应来源的整个事件（含动画和惯性滚动），不影响其他来源的滚动事件；未发生实际位移的命令不产生事件。

3. Toast事件默认上报，可专门过滤。[PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md)的Toast是瞬时消息，默认随OVERLAY类别上报显示完成（OVERLAY_SHOW）和消失完成（OVERLAY_HIDE）事件，每个Toast实例在自身完成点各上报一次，closeToast或新Toast替换旧Toast时旧实例各上报一次消失完成事件。不需要Toast事件时，在ignoreMask中设置IGNORE_TOAST过滤，仅影响Toast，不影响其他浮层。

4. 浮层事件仅上报本应用进程内的浮层实例。浮层是悬浮于页面内容之上、独立于页面路由结构呈现的界面层，典型组件包括[Dialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md)、[CustomDialog](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md)、[ActionSheet](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md)、[半模态转场](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md)（bindSheet）、[全屏模态转场](../reference/apis-arkui/arkui-ts/ts-universal-attributes-modal-transition.md)（bindContentCover）、[菜单控制](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md)（bindMenu）、[Popup](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md)气泡和[PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md)的Toast提示等，通常具有独立的显示与关闭动效，不随页面切换流转。UIExtension的跨进程系统弹窗、[Web](../reference/apis-arkweb/arkts-basic-components-web.md)组件的内部弹窗和[XComponent](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)的自绘制弹窗不上报。可上报的浮层及其overlayType取值见[事件详情JSON格式](#事件详情json格式)中的overlayType说明。

5. 结束事件以动效实际结束为准，不会在动效过程中上报。滚动结束（SCROLL_END）在滚动交互及其后续的惯性滚动均结束后上报，拖动和惯性滚动属于同一连续事件，不重复上报。Swiper切换结束（SWIPER_END）在切换动画完成后上报，页面切换结束（PAGE_CHANGE_END）在转场完成后上报。浮层仅在显示完成（OVERLAY_SHOW）和消失完成（OVERLAY_HIDE）时上报，无动画的显隐仍在实际完成时上报。每个组件的事件独立触发，互不等待，例如两个滚动节点先后开始滚动时，各自在自身动画停止时上报各自的结束事件，不等待所有节点动画停止。

6. 可能存在开始事件但没有结束事件的场景。切换进行到一半松手回弹、页面最终无变化的场景，不会上报正常完成的结束事件。Swiper、Tabs切换到其他页签的中途，松手回弹、回到起始索引时，上报SWIPER_CANCEL、TABS_CANCEL；CANCEL仅在设置withStart=true的订阅中上报，且该订阅须已收到本事件的开始事件。Navigation交互式转场（例如拖动返回）未达到提交条件松手回退时，只上报开始事件（PAGE_CHANGE_START），没有结束事件，也没有取消事件。上下文失效时，该上下文的全部订阅停止回调。如果某一组件正处于动效状态，在目标节点或其祖先下树、销毁时，会上报一次对应的结束事件作为收尾。

## 接口说明

本开发指导涉及的关键接口如下表所示，完整参数、枚举和错误码说明见[ui_info_collection.h](../reference/apis-arkui/capi-ui-info-collection-h.md)和[ui_json_wrapper.h](../reference/apis-arkui/capi-ui-json-wrapper-h.md)。

| 接口 | 功能描述 |
|---|---|
| [OH_ArkUI_NativeModule_RegisterUIContentChangeEvent](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_registeruicontentchangeevent) | 注册所选类别的事件订阅，输出订阅ID。 |
| [OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_unregisteruicontentchangeevent) | 注销仍然有效的订阅。 |
| [OH_ArkUI_NativeModule_UIContentChangeEventGetType](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgettype) | 在回调内读取事件类型。 |
| [OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgettimestamp) | 在回调内读取事件的单调时间戳，单位为纳秒。 |
| [OH_ArkUI_NativeModule_UIContentChangeEventGetContext](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgetcontext) | 在回调内读取事件所属的UI上下文。 |
| [OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgetcontentchangeeventjson) | 在回调内读取事件详情JSON。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperGetData](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetdata) | 读取只读JSON字符串。 |
| [OH_ArkUI_NativeModule_UIJsonWrapperGetSize](../reference/apis-arkui/capi-ui-json-wrapper-h.md#oh_arkui_nativemodule_uijsonwrappergetsize) | 读取JSON文本的UTF-8字节数。 |

### 事件类别与忽略类型

[OH_ArkUI_NativeModule_UIContentChangeEventCategory](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventcategory)定义事件类别，用于构造eventMask。

| 枚举值 | 说明 |
|---|---|
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_PAGE | 页面切换事件，包括Navigation、Router、Swiper和Tabs的切换事件。 |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_SCROLL | 滚动事件，不区分滚动子类型。 |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_OVERLAY | 浮层事件，例如模态、菜单或弹窗事件。 |
| OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_ALL | 所有受支持的事件类别。 |

[OH_ArkUI_NativeModule_UIContentChangeIgnoreType](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeignoretype)定义可忽略的事件类型，用于构造ignoreMask。

| 枚举值 | 说明 |
|---|---|
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLBY | 按指定偏移量滚动（scrollBy）的事件。 |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLTO | 滚动到指定位置（scrollTo）的事件。 |
| OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_TOAST | Toast提示事件。 |

类别与忽略位按位或组合的代码示例见[注册订阅](#注册订阅)。

### 推荐使用方案

按业务目标选择注册参数，控制回调频次和监听范围。

| 业务目标 | 推荐配置 | 说明 |
|---|---|---|
| 等待界面进入稳定状态后执行操作 | eventMask为业务所需类别，withStart=false，ignoreMask=0 | 只接收结束事件，回调次数最少。 |
| 统计切换或滚动事件时长 | withStart=true | 用结束事件与开始事件的时间戳差计算时长。 |
| 自动化滚动或批量定位场景 | 在上述基础上按来源设置IGNORE_SCROLLTO、IGNORE_SCROLLBY | 过滤程序滚动高频回调，保留手势滚动事件。 |
| 仅关注浮层且不关注Toast | eventMask为OVERLAY，ignoreMask含IGNORE_TOAST | Toast按需过滤，其他浮层正常上报。 |
| 区分多窗口事件 | 为每个UI上下文单独注册 | 回调内用GetContext结果区分归属。 |

### 事件类型

[OH_ArkUI_NativeModule_UIContentChangeEventType](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventtype)定义事件类型，通过GetType读取。开始和取消事件仅在withStart=true时上报。

页面、滚动与浮层事件的枚举值如下。

| 枚举值 | 数值 | 说明 |
|---|---|---|
| OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_START | 0 | 页面切换开始。 |
| OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_END | 1 | 页面切换结束。 |
| OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_START | 2 | 滚动开始。 |
| OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_END | 3 | 滚动交互及其后续的惯性滚动均已结束。 |
| OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_SHOW | 4 | 浮层显示完成。 |
| OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_HIDE | 5 | 浮层消失完成。 |

Swiper与Tabs事件的枚举值如下。

| 枚举值 | 数值 | 说明 |
|---|---|---|
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_START | 6 | Swiper切换开始。 |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_END | 7 | Swiper切换完成；如果存在过渡动画，则该动画也已完成。 |
| OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_CANCEL | 8 | Swiper切换中断，并回弹到起始索引。 |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_START | 9 | Tabs切换开始。 |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_END | 10 | Tabs切换结束；如果存在过渡动画，则该动画也已完成。 |
| OH_ARKUI_NATIVEMODULE_EVENT_TABS_CANCEL | 11 | Tabs切换开始后被取消，并回弹到切换开始时的索引。 |

页面切换事件（PAGE_CHANGE_START、PAGE_CHANGE_END）对应Navigation和Router的页面变化；Swiper、Tabs的切换分别使用SWIPER和TABS前缀的事件，同属PAGE类别。Navigation和Router的页面切换没有取消事件类型。事件类型的读取示例见[定义监听状态与回调函数](#定义监听状态与回调函数)。

### 事件详情JSON格式

在回调内调用[OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uicontentchangeeventgetcontentchangeeventjson)可获取事件详情。JSON输出的顶层包含schemaVersion字段，并包含事件类型、事件类别、触发节点、目标节点、浮层类型，以及根据事件类别决定是否包含的子树信息。

| 字段 | 类型 | 说明 |
|---|---|---|
| schemaVersion | number | 协议版本，当前为1。 |
| eventType | number | 事件类型，取值0～11，与GetType结果一致。 |
| category | string | 事件类别为page、scroll或overlay。Swiper和Tabs事件属于page。 |
| targetNode | object | 目标节点引用，包含节点ID和组件名，具体结构见下方JSON示例。页面事件标识目标页面，滚动事件标识发生滚动的节点，浮层事件标识浮层节点。 |
| triggerNode | object或null | 触发节点，即引起页面变化的节点，与targetNode结构相同。浮层事件存在可公开的触发节点时返回，否则为null；页面事件和滚动事件无法提供触发节点，为null。 |
| overlayType | string或null | 浮层类型，仅浮层事件返回，非浮层事件为null。各浮层的对应取值见下方取值表。 |
| subtree | object或null | 目标节点快照。正常完成（非节点下树或销毁时的收尾上报）的PAGE_CHANGE_END和OVERLAY_SHOW事件包含目标节点快照，其余事件为null。 |

节点引用中的id为节点ID的十进制字符串，是数据而非可调用句柄，不能传给节点操作接口；type为ArkUI组件名。节点快照仅包含id、type和children三个字段，children为按子节点顺序排列、结构相同的快照数组，叶子节点的children为空数组，不包含文本和属性数据。节点销毁后节点ID可能被复用，业务不应把节点ID当作长期唯一标识。

浮层事件overlayType的取值如下。

| overlayType | 对应浮层 |
|---|---|
| dialog | [Dialog](../reference/apis-arkui/arkui-ts/ts-methods-alert-dialog-box.md)、[半模态转场](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md)（bindSheet）、[全屏模态转场](../reference/apis-arkui/arkui-ts/ts-universal-attributes-modal-transition.md)（bindContentCover）。 |
| customDialog | [CustomDialog](../reference/apis-arkui/arkui-ts/ts-methods-custom-dialog-box.md)。 |
| actionSheet | [ActionSheet](../reference/apis-arkui/arkui-ts/ts-methods-action-sheet.md)。 |
| popup | [Popup](../reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md)、[AlphabetIndexer](../reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md)气泡。 |
| menu | [菜单控制](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md)（bindMenu）。 |
| toast | [PromptAction](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md)的Toast。 |
| overlay | [OverlayManager](../reference/apis-arkui/arkts-apis-uicontext-overlaymanager.md)普通内容和有序内容。 |

页面切换结束事件的JSON示例（数值仅用于说明格式，不是固定采集结果）。

```json
{
  "schemaVersion": 1,
  "eventType": 1,
  "category": "page",
  "targetNode": { "id": "66", "type": "NavDestination" },
  "triggerNode": null,
  "overlayType": null,
  "subtree": {
    "id": "66",
    "type": "NavDestination",
    "children": []
  }
}
```

浮层显示完成事件的JSON示例。

```json
{
  "schemaVersion": 1,
  "eventType": 4,
  "category": "overlay",
  "targetNode": { "id": "128", "type": "SheetPage" },
  "triggerNode": { "id": "42", "type": "Button" },
  "overlayType": "dialog",
  "subtree": {
    "id": "128",
    "type": "SheetPage",
    "children": [
      { "id": "129", "type": "Column", "children": [] }
    ]
  }
}
```

解析时按字段表检查类型；JSON文本中的成员顺序和空白不作约定。事件详情JSON的读取示例见[定义监听状态与回调函数](#定义监听状态与回调函数)。

### 返回值

注册接口返回以下错误码。

| 返回值 | 场景 | 处理方式 |
|---|---|---|
| ARKUI_ERROR_CODE_NO_ERROR | 注册成功，subscriptionId写入非零ID。 | 保存订阅ID用于注销。 |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID | uiContext为空或不再处于活跃状态。 | 在有效UI实例上重新获取上下文后注册。 |
| ARKUI_ERROR_CODE_CALLBACK_INVALID | callback为空。 | 补充有效回调后重新注册。 |
| ARKUI_ERROR_CODE_PARAM_INVALID | eventMask为0或含未知位、ignoreMask含未知位、subscriptionId输出指针为空。 | 修正参数后重新注册；失败时不创建订阅，也不改写subscriptionId。 |
| ARKUI_ERROR_CODE_CAPI_INIT_ERROR | Native模块尚未初始化。 | 检查运行环境后再注册。 |

注销接口返回以下错误码。

| 返回值 | 场景 | 处理方式 |
|---|---|---|
| ARKUI_ERROR_CODE_NO_ERROR | 注销成功，后续事件不再触发该订阅的回调。 | 注销后可在无活跃回调使用时释放userData。 |
| ARKUI_ERROR_CODE_UI_CONTEXT_INVALID | uiContext为空或不再处于活跃状态。 | 订阅已随上下文失效停止回调，不再重试。 |
| ARKUI_ERROR_CODE_PARAM_INVALID | subscriptionId为0、无法识别或对应订阅已被移除。 | 核对订阅ID和所属上下文，其他活动订阅不受影响。 |
| ARKUI_ERROR_CODE_CAPI_INIT_ERROR | Native模块尚未初始化。 | 检查运行环境。 |

上述四个读取接口在event指针或对应输出指针为空时返回ARKUI_ERROR_CODE_PARAM_INVALID，成功时返回ARKUI_ERROR_CODE_NO_ERROR。错误码取值见[ArkUI_ErrorCode](../reference/apis-arkui/capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)。非UI线程调用注册或注销导致进程终止，不属于可按错误码处理的失败。

## 开发步骤

以下步骤介绍如何基于示例工程实现完整的事件监听。注册订阅后接收页面切换、滚动和浮层事件的回调，在回调内读取事件数据、计算事件时长并转发到ArkTS页面展示，最后注销订阅。

整体开发流程如下。

- 步骤一：准备工程。
- 步骤二：定义监听状态与回调函数，在回调内读取事件数据并转发。
- 步骤三：注册订阅，开始监听并接收事件回调。
- 步骤四：注销订阅并释放业务数据。

### 准备工程

参考[基于NDK构建UI概述](ndk-build-ui-overview.md)和[接入ArkTS页面](ndk-access-the-arkts-page.md)准备一个包含ArkTS页面和Native C++模块的DevEco Studio工程。ArkTS页面用于配置订阅选项、触发各类事件并展示回调结果，Native模块实现事件监听逻辑，两者通过N-API桥接。

示例使用[OH_LOG_Print](../reference/apis-performance-analysis-kit/capi-log-h.md#oh_log_print)输出日志。示例工程包含ArkTS桥接，CMakeLists.txt中需链接libace_ndk.z.so、libace_napi.z.so和libhilog_ndk.z.so；示例代码中的SAMPLE_LOG_DOMAIN（0xF811）与SAMPLE_LOG_TAG（UiInfoCollection）为示例定义的日志域与标签常量，可通过hilog -T UiInfoCollection过滤示例日志。

<!-- @[ui_change_event_include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```cpp
// 本示例页面变化事件特性所需的头文件。
#include "arkui/ui_info_collection.h"
#include "arkui/ui_json_wrapper.h"
#include "hilog/log.h"
#include <cinttypes>
```

本示例Native模块的CMakeLists.txt配置如下。

<!-- @[ui_change_event_cmake](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/CMakeLists.txt) -->

```cmake
# CMake最低版本要求。
cmake_minimum_required(VERSION 3.5.0)
project(UiInfoCollectionAndInjection)

set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})

if(DEFINED PACKAGE_FIND_FILE)
    include(${PACKAGE_FIND_FILE})
endif()

include_directories(${NATIVERENDER_ROOT_PATH}
                    ${NATIVERENDER_ROOT_PATH}/include)

file(GLOB_RECURSE ENTRY_SOURCES CONFIGURE_DEPENDS
      "${NATIVERENDER_ROOT_PATH}/*.cpp"
  )

add_library(entry SHARED ${ENTRY_SOURCES})

find_library(libace-lib ace_ndk.z)

find_library(libnapi-lib ace_napi.z)

find_library(libhilog-lib hilog_ndk.z)

target_link_libraries(entry PUBLIC ${libace-lib} ${libnapi-lib} ${libhilog-lib})
```

Native侧调用须在目标UI实例的UI线程执行，调用所需的[ArkUI_ContextHandle](../reference/apis-arkui/capi-arkui-nativemodule-arkui-context8h.md)由ArkTS页面传入的[UIContext](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md)在N-API桥接中转换获得。示例页面通过getUIContext()取得UIContext并作为首个参数随桥接调用传入，桥接函数使用[OH_ArkUI_GetContextFromNapiValue](../reference/apis-arkui/capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue)完成转换；本示例缓存单一UI实例的句柄，避免每次调用重复获取，多实例场景的注意事项见注释。

<!-- @[ui_change_event_context](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```cpp
// 本示例复用其单一UI实例的上下文句柄，而不是每次调用都重新获取；
// 在多实例场景复用该做法前，请先阅读约束与限制说明。
std::mutex g_contextMutex;
ArkUI_ContextHandle g_cachedContext = nullptr;

ArkUI_ContextHandle GetContext(napi_env env, napi_value value)
{
    std::lock_guard<std::mutex> lock(g_contextMutex);
    if (g_cachedContext != nullptr) {
        return g_cachedContext;
    }
    ArkUI_ContextHandle context = nullptr;
    if (OH_ArkUI_GetContextFromNapiValue(env, value, &context) != ARKUI_ERROR_CODE_NO_ERROR ||
        context == nullptr) {
        napi_throw_type_error(env, nullptr, "Cannot obtain the ArkUI context of this UI instance");
        return nullptr;
    }
    g_cachedContext = context;
    return context;
}
```

### 定义监听状态与回调函数

先定义应用自己的监听状态并实现回调。userData指向该状态对象，框架只回传指针，由应用保证其有效。本示例的监听状态保存订阅ID、已收到的事件数，以及按事件族（页面、滚动、浮层、Swiper、Tabs）记录的起始时间戳（用于计算事件时长）。

<!-- @[ui_change_event_listener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```cpp
// 参与事件时长统计的事件族数量：页面、滚动、浮层、Swiper、Tabs。
constexpr int32_t CONTENT_CHANGE_FAMILY_COUNT = 5;

// 本示例的监听状态：订阅生效期间subscriptionId非零，事件计数在每次回调时更新，
// 各事件族的起始时间戳记录待配对的开始事件，用于计算事件时长。
struct ContentChangeListener {
    uint64_t subscriptionId = 0;
    uint32_t eventCount = 0;
    // 各事件族的起始时间戳；对应族没有待配对的开始事件时为0。
    uint64_t startTimestamps[CONTENT_CHANGE_FAMILY_COUNT] = {0};
};
```

回调日志中使用以下函数将事件类型枚举转为可读文本。

<!-- @[ui_change_event_name](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```cpp
// 把事件类型枚举格式化为日志可读文本。
const char* ContentChangeEventName(int32_t type)
{
    switch (type) {
        case OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_START:
            return "PAGE_CHANGE_START";
        case OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_END:
            return "PAGE_CHANGE_END";
        case OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_START:
            return "SCROLL_START";
        case OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_END:
            return "SCROLL_END";
        case OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_SHOW:
            return "OVERLAY_SHOW";
        case OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_HIDE:
            return "OVERLAY_HIDE";
        case OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_START:
            return "SWIPER_START";
        case OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_END:
            return "SWIPER_END";
        case OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_CANCEL:
            return "SWIPER_CANCEL";
        case OH_ARKUI_NATIVEMODULE_EVENT_TABS_START:
            return "TABS_START";
        case OH_ARKUI_NATIVEMODULE_EVENT_TABS_END:
            return "TABS_END";
        case OH_ARKUI_NATIVEMODULE_EVENT_TABS_CANCEL:
            return "TABS_CANCEL";
        default:
            return "UNKNOWN";
    }
}
```

回调结合开始事件和结束事件的时间戳计算事件时长。以下函数按事件族（页面、滚动、浮层、Swiper、Tabs）分别记录起始时间戳，开始事件开启计时窗口（浮层以OVERLAY_SHOW与OVERLAY_HIDE作为显示时长窗口），结束事件关闭窗口并返回时间戳差值，取消事件仅关闭窗口不计时。

<!-- @[ui_change_event_duration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```cpp
// 把事件类型映射到其统计族：0=页面，1=滚动，2=浮层，3=Swiper，4=Tabs。
// 开始与结束事件构成一个事件时长统计窗口。
int32_t ContentChangeEventFamily(int32_t type)
{
    if (type <= OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_END) {
        return 0;
    }
    if (type <= OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_END) {
        return 1;
    }
    if (type <= OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_HIDE) {
        return 2;
    }
    if (type <= OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_CANCEL) {
        return 3;
    }
    return 4;
}

// 在注册的事件回调中对每个上报事件调用：开始事件开启统计窗口，同族结束事件关闭窗口。
// 结束事件关闭已开启的窗口时返回该窗口的时长（纳秒）；取消事件只关闭待配对窗口，
// 不返回时长。
uint64_t MeasureContentChangeDuration(ContentChangeListener* listener, int32_t type, uint64_t timestamp)
{
    uint64_t& startedAt = listener->startTimestamps[ContentChangeEventFamily(type)];
    switch (type) {
        case OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_START:
        case OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_START:
        case OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_SHOW:
        case OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_START:
        case OH_ARKUI_NATIVEMODULE_EVENT_TABS_START:
            startedAt = timestamp;
            return 0;
        case OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_END:
        case OH_ARKUI_NATIVEMODULE_EVENT_SCROLL_END:
        case OH_ARKUI_NATIVEMODULE_EVENT_OVERLAY_HIDE:
        case OH_ARKUI_NATIVEMODULE_EVENT_SWIPER_END:
        case OH_ARKUI_NATIVEMODULE_EVENT_TABS_END:
            if (startedAt != 0 && timestamp >= startedAt) {
                const uint64_t duration = timestamp - startedAt;
                startedAt = 0;
                return duration;
            }
            return 0;
        default:
            startedAt = 0;
            return 0;
    }
}
```

以下回调读取事件类型、时间戳、所属上下文和详情JSON，更新事件计数、计算事件时长并输出日志。

<!-- @[ui_change_event_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```cpp
// 读取事件快照，写入hilog并把复制后的记录转交应用层。事件快照、借用的上下文句柄与
// JSON封装只在本次回调内有效：不得销毁该封装，也不得缓存指针供回调返回后使用。
void OnContentChangeEvent(const OH_ArkUI_NativeModule_UIContentChangeEvent* event, void* userData)
{
    auto* listener = static_cast<ContentChangeListener*>(userData);
    if (listener == nullptr) {
        return;
    }
    OH_ArkUI_NativeModule_UIContentChangeEventType type = OH_ARKUI_NATIVEMODULE_EVENT_PAGE_CHANGE_START;
    uint64_t timestamp = 0;
    ArkUI_ContextHandle context = nullptr;
    const OH_ArkUI_NativeModule_UIJsonWrapper* json = nullptr;
    if (OH_ArkUI_NativeModule_UIContentChangeEventGetType(event, &type) != ARKUI_ERROR_CODE_NO_ERROR ||
        OH_ArkUI_NativeModule_UIContentChangeEventGetTimestamp(event, &timestamp) != ARKUI_ERROR_CODE_NO_ERROR ||
        OH_ArkUI_NativeModule_UIContentChangeEventGetContext(event, &context) != ARKUI_ERROR_CODE_NO_ERROR ||
        OH_ArkUI_NativeModule_UIContentChangeEventGetContentChangeEventJson(event, &json) !=
            ARKUI_ERROR_CODE_NO_ERROR) {
        return;
    }
    ++listener->eventCount;
    const uint64_t duration = MeasureContentChangeDuration(listener, type, timestamp);
    // JSON文本需要在本次回调之后继续使用时，请在此处复制。
    const char* data = json == nullptr ? nullptr : OH_ArkUI_NativeModule_UIJsonWrapperGetData(json);
    const uint32_t size = json == nullptr ? 0 : OH_ArkUI_NativeModule_UIJsonWrapperGetSize(json);
    OH_LOG_Print(LOG_APP, LOG_INFO, SAMPLE_LOG_DOMAIN, SAMPLE_LOG_TAG,
        "event=%{public}s timestampNs=%{public}" PRIu64 " context=%{public}p jsonBytes=%{public}u "
        "json=%{public}s", ContentChangeEventName(type), timestamp, context, size,
        data == nullptr ? "" : data);
    // 把复制后的记录转交应用层；本示例转发给示例页面的ArkTS回调。
    ForwardContentChangeEvent(listener, type, timestamp, duration, data, size);
}
```

事件数据在回调返回后即失效，因此示例在回调内把事件数据复制为记录对象，转发给示例页面的ArkTS回调，并展示在事件列表中。业务实现中可将复制后的数据投递到自身的工作线程或任务队列，避免在回调内执行耗时等待。

配对不到开始事件时不产生时长。withStart=false的订阅收不到开始事件，事件时长为0；活动开始后才注册的订阅也收不到该事件的开始事件回调。

上述四个读取接口只会在参数为空时失败；回调内按需读取即可，同一回调内重复读取同一事件数据，结果不变。

### 注册订阅

调用注册接口后，应用开始接收所选类别的事件回调，注册成功时输出非零订阅ID用于后续注销。以下示例将示例页面的注册选项定义为布尔结构体，注册函数把各选项按位或组合为eventMask与ignoreMask，枚举取值见[事件类别与忽略类型](#事件类别与忽略类型)。

<!-- @[ui_change_event_register](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```cpp
// 示例页面的注册选项：每个布尔值选中一个受支持的事件类别或忽略来源，
// 掩码由下方公开枚举按位或组合。
struct ContentChangeRegistration {
    bool withStart = false;
    bool watchPage = false;
    bool watchScroll = false;
    bool watchOverlay = false;
    bool ignoreScrollBy = false;
    bool ignoreScrollTo = false;
    bool ignoreToast = false;
};

// 把选中的事件类别组合为eventMask参数。
uint32_t CombineEventMask(const ContentChangeRegistration& options)
{
    return (options.watchPage ? OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_PAGE : 0U) |
        (options.watchScroll ? OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_SCROLL : 0U) |
        (options.watchOverlay ? OH_ARKUI_NATIVEMODULE_EVENT_CATEGORY_OVERLAY : 0U);
}

// 把选中的忽略来源组合为ignoreMask参数。
uint32_t CombineIgnoreMask(const ContentChangeRegistration& options)
{
    return (options.ignoreScrollBy ? OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLBY : 0U) |
        (options.ignoreScrollTo ? OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_SCROLLTO : 0U) |
        (options.ignoreToast ? OH_ARKUI_NATIVEMODULE_CONTENTCHANGE_IGNORE_TOAST : 0U);
}

// 在目标UI上下文的UI线程上注册监听。eventMask必须至少包含一个类别位，
// 否则注册失败并返回ARKUI_ERROR_CODE_PARAM_INVALID。
ArkUI_ErrorCode StartContentChangeListening(ArkUI_ContextHandle context,
    ContentChangeListener* listener, const ContentChangeRegistration& options)
{
    if (context == nullptr || listener == nullptr) {
        return ARKUI_ERROR_CODE_PARAM_INVALID;
    }
    const uint32_t eventMask = CombineEventMask(options);
    const uint32_t ignoreMask = CombineIgnoreMask(options);
    if (eventMask == 0) {
        return ARKUI_ERROR_CODE_PARAM_INVALID;
    }
    return OH_ArkUI_NativeModule_RegisterUIContentChangeEvent(context, options.withStart, eventMask,
        ignoreMask, listener, OnContentChangeEvent, &listener->subscriptionId);
}
```

注册成功后subscriptionId为非零值，在传入的UI上下文内唯一。多窗口场景为每个UI上下文分别注册，并各自保存订阅ID。

### 注销订阅

不再监听时，在目标UI实例的UI线程调用注销接口。以下示例在注销成功后将订阅ID复位，避免重复注销同一订阅。支持在回调内注销当前订阅，当前回调正常结束后，该订阅不再被调用。

<!-- @[ui_change_event_unregister](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/UiInfoCollectionAndInjection/entry/src/main/cpp/napi_init.cpp) -->

```cpp
// 在目标UI上下文的UI线程上注销订阅。调用成功后，后续事件不再触发已移除的订阅；
// 释放监听状态前请先将订阅ID复位。
ArkUI_ErrorCode StopContentChangeListening(ArkUI_ContextHandle context, ContentChangeListener* listener)
{
    if (context == nullptr || listener == nullptr || listener->subscriptionId == 0) {
        return ARKUI_ERROR_CODE_PARAM_INVALID;
    }
    ArkUI_ErrorCode result = OH_ArkUI_NativeModule_UnRegisterUIContentChangeEvent(context,
        listener->subscriptionId);
    if (result == ARKUI_ERROR_CODE_NO_ERROR) {
        listener->subscriptionId = 0;
    }
    return result;
}
```

注销成功且无活跃回调使用时，可释放userData指向的业务数据；进程退出前应完成注销，避免依赖上下文失效时的隐式清理。

## 常见问题

以下按现象分类说明开发过程中的常见问题。

### 为什么收不到开始事件

收不到开始事件时，依次确认以下情况。

- withStart=false时不上报开始事件和取消事件，属预期行为。
- 活动开始后才注册的订阅不补发历史开始事件；该事件后续的结束事件仍可收到。
- Swiper开启autoPlay期间，该Swiper的开始事件同样不上报，参见[约束与限制](#约束与限制)。

### 为什么开始事件后没有结束事件

以下场景可能只收到开始事件而没有对应的结束事件。

- Swiper、Tabs切换到一半松手回弹时上报取消事件而不上报结束事件；withStart=true且已收到本事件的开始事件回调后，才能收到取消事件回调。
- Navigation交互式转场未提交松手回退时只上报开始事件，没有结束事件和取消事件。
- 目标节点已下树或销毁时，结束事件已在下树或销毁时刻上报过一次；迟到的完成信号不会再次上报。

业务侧不要假设开始事件与结束事件总是成对出现，状态机应以收到的事件类型为准推进。

### 为什么没有滚动回调

收不到滚动事件回调时，依次确认以下情况。

- scrollTo、scrollBy被ignoreMask对应位过滤时，相应来源的整个滚动周期不上报。
- 未发生实际位移的命令（例如滚动到当前偏移、越界钳制后等于当前偏移）不产生事件。
- 滚动结束事件等待惯性滚动结束后上报，快速连续滚动属于同一连续事件，中间不重复上报。

### 为什么没有浮层回调

收不到浮层事件回调时，依次确认以下情况。

- 浮层类型不在上报范围内，例如UIExtension跨进程系统弹窗、Web内部弹窗、XComponent自绘制弹窗不上报。
- Toast被IGNORE_TOAST过滤。
- 显示或关闭的动效尚未完成，或关闭意图被业务回调拦截而浮层仍可见。
- 浮层已显示后才注册的订阅不补发历史显示事件，实际关闭时仍可收到消失完成事件（OVERLAY_HIDE）。

### 为什么时间戳不能转换为日期

时间戳使用单调时钟记录事件所代表的开始、结束或取消时刻，单位为纳秒，不表示日历时间。不同设备的时钟基准不同，数值不能跨设备比较；同一设备上可用于计算两个事件的先后顺序和时间差。

### 回调数据失效问题

回调数据使用不当时，常见错误有以下几类。

- 在回调返回后使用event、上下文句柄、JSON对象或其字符串指针，属于引用失效后的悬空访问。需要保留数据时，在回调内复制。
- 对事件详情JSON调用销毁接口是错误用法，该对象由框架拥有。
- userData应在注销成功且无活跃回调使用后再释放；在回调内注销当前订阅时，须等当前回调返回后再释放。
