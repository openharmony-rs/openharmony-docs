---
kits: ["ArkWeb Kit / 方舟Web"]
description: "汇总ArkWeb指南配套示例代码，按页面加载、请求拦截、多媒体、同层渲染、离线Web组件等场景归类ArkTS与C/C++示例，多数场景提供ArkTS静态范式工程。"
keywords: [ArkWeb, 示例代码, Web组件, 函数互调, 网络请求拦截, 同层渲染, 画中画, 离线Web组件, 静态范式]
doctype: guide
status: active
---

# ArkWeb指南配套示例代码
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @sinat_22543221-->
<!--Designer: @hwt00888022-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

| 场景分类 | Sample名称 | 语言 | 场景介绍 |
| -------- | -------- | -------- | -------- |
| 进程管理 | [ProcessWeb](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ProcessWeb) | ArkTS | 使用Web组件多进程能力管理渲染进程，演示进程模式设置、进程异常退出监听与终止，以及设置与网页一致的组件背景色消除跳转闪烁。 |
| 进程管理 | [ProcessWeb](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ProcessWeb) | ArkTS | 使用Web组件多进程能力管理渲染进程，以ArkTS静态范式演示进程模式设置、进程异常退出监听与终止及组件背景色设置。 |
| 组件生命周期 | [LifecycleWebComp](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/LifecycleWebComp) | ArkTS | 使用Web组件生命周期回调，演示组件创建、页面加载开始与结束等生命周期事件的监听与处理时序。 |
| 组件生命周期 | [LifecycleWebComp](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/LifecycleWebComp) | ArkTS | 使用Web组件生命周期回调，以ArkTS静态范式演示组件创建、页面加载开始与结束等生命周期事件的处理。 |
| 基本属性与事件 | [SetBasicAttrsEvtsTwo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsTwo) | ArkTS | 使用Web组件属性与webview接口，演示User-Agent获取与自定义、Cookie与数据存储管理、缓存模式配置及运动方向传感器数据获取。 |
| 基本属性与事件 | [SetBasicAttrsEvtsTwo](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/SetBasicAttrsEvts/SetBasicAttrsEvtsTwo) | ArkTS | 使用Web组件属性与webview接口，以ArkTS静态范式演示User-Agent获取与自定义、Cookie与数据存储管理及缓存模式配置。 |
| 基本属性与事件 | [SetBasicAttrsEvtsOne](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsOne) | ArkTS | 使用darkMode等属性配置Web组件，演示深色模式适配、地理位置权限管理、隐私模式及在新窗口中打开页面。 |
| 深色模式适配 | [webSetDarkMode](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/webSetDarkMode) | ArkTS | 使用darkMode与forceDarkAccess接口，以ArkTS静态范式演示前端页面深色模式配置、背景色设置及自动跟随系统深浅色。 |
| 基本属性与事件 | [SetBasicAttrsEvtsOne](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/SetBasicAttrsEvts/SetBasicAttrsEvtsOne) | ArkTS | 使用multiWindowAccess与incognito属性配置Web组件，以ArkTS静态范式演示在新窗口中打开页面及隐私模式下的数据管理。 |
| 位置权限管理 | [GeolocationPermissions](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/GeolocationPermissions) | ArkTS | 使用onGeolocationShow接口，以ArkTS静态范式演示对指定网站地理位置权限的授予、查询与撤销。 |
| 传感器监测 | [WebSensor](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebSensor) | ArkTS | 使用W3C标准协议传感器接口，以ArkTS静态范式演示在网页中获取加速度、陀螺仪等运动和方向数据并更新页面。 |
| 渲染模式与布局 | [WebRenderLayout](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebRenderLayout) | ArkTS | 使用Web组件渲染模式与布局属性，演示异步、同步渲染模式设置及FIT_CONTENT模式下组件高度随网页内容自适应。 |
| 渲染模式与布局 | [webRenderMode](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/webRenderMode) | ArkTS | 使用renderMode属性，以ArkTS静态范式演示Web组件同步与异步渲染模式的设置。 |
| 跳转闪烁优化 | [BackGroundColor](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/BackGroundColor) | ArkTS | 使用backgroundColor属性设置与网页一致的背景色，以ArkTS静态范式演示消除Web页面跳转时的视觉闪烁。 |
| 嵌套滚动与软键盘 | [ManageWebPageInteracts](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageInteracts) | ArkTS | 使用Web组件嵌套滚动与键盘避让属性，演示Web与ArkUI可滚动容器的嵌套滚动及对接系统软键盘的避让适配。 |
| 嵌套滚动与软键盘 | [ManageWebPageInteracts](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ManageWebPageInteracts) | ArkTS | 使用Web组件嵌套滚动与键盘避让属性，以ArkTS静态范式演示嵌套滚动、点击状态栏回顶及软键盘避让适配。 |
| 页面内容滚动 | [WebScrollDemo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebScrollDemo) | ArkTS | 使用scrollTo、pageUp等接口控制Web页面滚动，演示ArkTS侧接口与前端JS侧window.scrollTo两种滚动控制方式。 |
| 打印与PDF预览 | [ProcessWebPageCont](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ProcessWebPageCont) | ArkTS | 使用Web组件打印与预览能力，演示前端页面打印、PDF文档预览及网页中安全区域计算和避让适配。 |
| 安全区域适配 | [webSafeAreaInsets](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/webSafeAreaInsets) | ArkTS | 使用expandSafeArea与窗口全屏布局属性，以ArkTS静态范式演示网页中安全区域计算和避让适配。 |
| 焦点管理 | [WebFocusManagement](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebFocusManagement) | ArkTS | 使用requestFocus、onFocus等接口管理Web组件焦点，演示组件级聚焦失焦与W3C标准网页元素的焦点管理。 |
| 焦点管理 | [WebFocusManagement](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebFocusManagement) | ArkTS | 使用requestFocus、onFocus等接口，以ArkTS静态范式演示组件级聚焦失焦与W3C标准网页元素的焦点管理。 |
| 手势交互 | [WebGestureInteraction](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebGestureInteraction) | ArkTS | 使用Web组件手势能力，演示手势识别与拦截、禁用缩放手势及滑动返回上一页面等常见手势问题处理。 |
| 手势交互 | [WebGestureInteraction](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebGestureInteraction) | ArkTS | 使用Web组件手势能力，以ArkTS静态范式演示手势识别与拦截、禁用缩放手势及滑动返回上一页面。 |
| 网页缩放管理 | [WebManagementZooming](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebManagementZooming) | ArkTS | 使用zoom等接口管理网页缩放，演示启停手势及键鼠缩放、监听缩放比例变化与控制页面缩放到指定比例。 |
| 网页缩放管理 | [WebManagementZooming](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebManagementZooming) | ArkTS | 使用zoom等接口管理网页缩放，以ArkTS静态范式演示手势及键鼠缩放控制、缩放比例监听与指定比例缩放。 |
| 网页弹框 | [ShowWebPageDialog](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ShowWebPageDialog) | ArkTS | 使用onAlert等事件定制网页弹框，演示alert、confirm、prompt三种弹框的应用侧自定义实现与用户确认输入处理。 |
| 网页弹框 | [ShowWebPageDialog](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ShowWebPageDialog) | ArkTS | 使用onAlert等事件定制网页弹框，以ArkTS静态范式演示alert、confirm、prompt三种弹框的自定义实现。 |
| 网页拖拽交互 | [WebDragInteraction](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebDragInteraction) | ArkTS | 使用Web组件拖拽能力与ArkTS侧onDrop事件，演示网页元素长按拖放、拖拽数据格式处理及禁止拖拽配置。 |
| 网页拖拽交互 | [WebDragInteraction](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebDragInteraction) | ArkTS | 使用Web组件拖拽能力与ArkTS侧onDrop事件，以ArkTS静态范式演示网页元素长按拖放及禁止拖拽配置。 |
| 安全与隐私 | [ManageWebCompSecPriv](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebCompSecPriv) | ArkTS | 使用onInterceptRequest与广告过滤等能力，演示本地资源跨域问题解决、智能防跟踪及广告过滤。 |
| 安全与隐私 | [ManageWebCompSecPriv](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ManageWebCompSecPriv) | ArkTS | 使用onInterceptRequest与广告过滤等能力，以ArkTS静态范式演示本地资源跨域问题解决、智能防跟踪及广告过滤。 |
| 页面加载 | [LoadPages](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/LoadPages) | ArkTS | 使用Web组件加载页面，演示加载网络页面、本地页面及HTML富文本数据等多种页面加载方式。 |
| 页面跳转与导航 | [ManagePageRedirectNav](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/ManagePageRedirectNav) | ArkTS | 使用onLoadIntercept拦截链接与历史记录接口，演示应用内页面跳转、跳转其他应用及浏览记录前进后退导航。 |
| 自定义请求响应 | [CustomizePageResp](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/CustomizePageResp) | ArkTS | 使用onInterceptRequest拦截页面请求，演示自定义响应头与响应体构造及预编译JavaScript生成CodeCache加速执行。 |
| 自定义请求响应 | [CustomizePageResp](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ManageWebPageLoadBrowse/CustomizePageResp) | ArkTS | 使用onInterceptRequest拦截页面请求，以ArkTS静态范式演示自定义响应头与响应体构造及预编译JavaScript缓存。 |
| 加速页面访问 | [AcceleratePageAccess](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess) | ArkTS | 使用ArkWeb Predictor等加速能力，演示域名预解析预连接、页面预加载、预编译JavaScript及离线资源注入。 |
| 加速页面访问 | [AcceleratePageAccess](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ManageWebPageLoadBrowse/AcceleratePageAccess) | ArkTS | 使用ArkWeb Predictor等加速能力，以ArkTS静态范式演示预解析预连接、页面预加载、预编译JavaScript及离线资源注入。 |
| 缓存与窗口迁移 | [NetReqInterceptCacheWinOps](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/NetReqInterceptCacheWinOps) | ArkTS | 使用WebviewController接口配置前进后退缓存，演示BFCache的开启配置及Web组件在不同窗口间的迁移。 |
| 窗口迁移 | [NetReqInterceptCacheWinOps](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ManageWebPageLoadBrowse/NetReqInterceptCacheWinOps) | ArkTS | 使用WebviewController接口，以ArkTS静态范式演示Web组件在不同窗口间的迁移。 |
| 文件上传下载 | [ManageWebPageFileIO](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageFileIO) | ArkTS | 使用onShowFileSelector与下载接口，演示自定义文件上传及下载任务的监听、主动发起与恢复。 |
| 文件上传下载 | [ManageWebPageFileIO](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ManageWebPageFileIO) | ArkTS | 使用onShowFileSelector与下载接口，以ArkTS静态范式演示自定义文件上传（含相机拍照）及下载任务的发起与恢复。 |
| 网页多媒体 | [WebRTC](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebRTC) | ArkTS | 使用onPermissionRequest处理权限请求，以ArkTS静态范式演示在Web中打开摄像头和麦克风。 |
| 网页多媒体 | [UsingWebMultimedia](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/UsingWebMultimedia) | ArkTS | 使用WebRTC与媒体接管能力，演示在Web中打开摄像头和麦克风及应用接管网页媒体播放并用本地播放器渲染视频。 |
| 网页多媒体 | [AppTakeOversWebMedia](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/AppTakeOversWebMedia) | ArkTS | 使用应用接管网页媒体播放能力，以ArkTS静态范式演示应用侧播放器接管网页媒体播放并渲染视频。 |
| 画中画播放 | [ArkWebPictureInPicture](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebPictureInPicture) | ArkTS | 使用Picture-in-Picture Web API，演示在浮动窗口中持续播放网页视频，以及监听全屏事件控制组件显隐实现沉浸式播放。 |
| 画中画播放 | [WebPictureInPicture](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebPictureInPicture) | ArkTS | 使用Picture-in-Picture Web API，以ArkTS静态范式演示在浮动窗口中持续播放网页视频。 |
| 视频全屏播放 | [ArkWebFullScreen](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebFullScreen) | ArkTS | 使用Web组件全屏事件，演示监听进入与退出全屏并自动切换横竖屏的沉浸式视频播放。 |
| 视频全屏播放 | [ArkWebFullScreen](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ArkWebFullScreen) | ArkTS | 使用Web组件全屏事件，以ArkTS静态范式演示监听进入与退出全屏并自动切换横竖屏的沉浸式播放。 |
| 视频全屏播放 | [WebFullScreen](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebFullScreen) | ArkTS | 使用onFullScreenEnter与onFullScreenExit事件，以ArkTS静态范式演示视频进入与退出沉浸式全屏播放。 |
| 网页打印 | [WebPrint](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebPrint) | ArkTS | 使用Web组件打印能力，以ArkTS静态范式演示应用接口与W3C标准协议接口两种方式打印前端页面。 |
| 保存页面为PDF | [ArkWebCreatePdf](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebCreatePdf) | ArkTS | 使用createPdf方法将前端页面保存为PDF，演示callback与Promise两种调用方式。 |
| 保存页面为PDF | [CreatePdf](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/CreatePdf) | ArkTS | 使用createPdf方法将前端页面保存为PDF，以ArkTS静态范式演示callback与Promise两种调用方式。 |
| PDF文档预览 | [WebPreviewPdf](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebPreviewPdf) | ArkTS | 使用Web组件PDF文档预览能力，以ArkTS静态范式演示加载网络、沙箱及本地PDF文档并监听PDF加载事件。 |
| 网页菜单 | [ArkWebMenu](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebMenu) | ArkTS | 使用Web组件菜单能力，演示文本选中菜单、上下文菜单及自定义菜单的实现与配置。 |
| 网页菜单 | [ArkWebMenu](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ArkWebMenu) | ArkTS | 使用Web组件菜单能力，以ArkTS静态范式演示文本选中菜单、上下文菜单及自定义菜单的实现与配置。 |
| 剪贴板交互 | [ArkWebClipboard](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebClipboard) | ArkTS | 使用Web组件剪贴板能力，演示通过菜单、快捷键及W3C剪贴板接口对网页内容执行剪切、复制和粘贴。 |
| 剪贴板交互 | [ArkWebClipboard](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ArkWebClipboard) | ArkTS | 使用Web组件剪贴板能力，以ArkTS静态范式演示通过菜单、快捷键及W3C剪贴板接口对网页内容执行剪切、复制和粘贴。 |
| 网页智能分词 | [ArkWebDataDetector](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebDataDetector) | ArkTS | 使用Web组件智能分词能力，演示自动识别网页中电话号码、网址等实体并提供高亮、预览等交互操作。 |
| 网页智能分词 | [ArkWebDataDetector](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ArkWebDataDetector) | ArkTS | 使用Web组件智能分词能力，以ArkTS静态范式演示自动识别网页中电话号码、网址等实体并提供交互操作。 |
| 同层渲染 | [UseSameLayerRender](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/UseSameLayerRender) | ArkTS | 使用embed与object标签实现同层渲染，演示同层渲染输入框及XComponent+AVPlayer视频组件嵌入网页。 |
| 同层渲染 | [webSameLayer](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/webSameLayer) | ArkTS | 使用embed与object标签实现同层渲染，以ArkTS静态范式演示原生输入框及视频组件嵌入网页与渲染对齐。 |
| 离线Web组件 | [UseOfflineWebComp](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/UseOfflineWebComp) | ArkTS | 使用离线Web组件能力，演示组件创建与挂载、页面预渲染、渲染进程预启动及组件复用与释放策略。 |
| 离线Web组件 | [UseOfflineWebComp](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/UseOfflineWebComp) | ArkTS | 使用离线Web组件能力，以ArkTS静态范式演示组件创建与挂载、页面预渲染、渲染进程预启动及组件复用与释放。 |
| 浏览器扩展通信 | [ExtensionApp](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb/WebExtension/ExtensionApp) | ArkTS | 使用WebNativeMessagingExtensionAbility组件，演示作为接收方应用接收浏览器扩展发送的消息并回复。 |
| 浏览器扩展通信 | [ExtensionBrowser](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb/WebExtension/ExtensionBrowser) | ArkTS | 使用WebNativeMessagingExtensionManager，演示浏览器侧连接应用侧扩展能力并发送消息及获取manifest数据。 |
| 浏览器扩展通信 | [ExtensionApp](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebExtension/ExtensionApp) | ArkTS | 使用WebNativeMessagingExtensionAbility组件，以ArkTS静态范式演示作为接收方应用接收浏览器扩展消息并回复。 |
| 浏览器扩展通信 | [ExtensionBrowser](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/WebExtension/ExtensionBrowser) | ArkTS | 使用WebNativeMessagingExtensionManager，以ArkTS静态范式演示浏览器侧连接应用侧扩展能力并发送消息。 |
| 前端页面调试 | [ArkWebDebuggingWithDevtools](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebDebuggingWithDevtools) | ArkTS | 使用setWebDebuggingAccess开启调试开关，演示通过USB或无线连接在电脑上用DevTools调试前端页面及端口转发配置。 |
| 前端页面调试 | [ArkWebDebuggingWithDevtools](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ArkWebDebuggingWithDevtools) | ArkTS | 使用setWebDebuggingAccess开启调试开关，以ArkTS静态范式演示USB或无线连接下用DevTools调试前端页面。 |
| 加载问题定位 | [WebWriteScreenIssue](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebWriteScreenIssue) | ArkTS | 使用ArkWeb问题定位方法，演示白屏问题与网页加载失败问题的定位思路与解决方法。 |
| 前端页面函数互调 | [UseFrontendJSApp](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/UseFrontendJSApp) | ArkTS、C/C++ | 使用runJavaScript、registerJavaScriptProxy及NDK接口，演示应用与前端页面函数互调、消息端口通信及C/C++侧相互调用。 |
| 前端页面函数互调 | [UseFrontendJSApp](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/UseFrontendJSApp) | ArkTS、C/C++ | 使用registerJavaScriptProxy与NDK接口，以ArkTS静态范式演示前端页面调用应用侧函数及C/C++侧应用与前端页面双向通信。 |
| 页面数据通道 | [ArkWebJsBridge](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebJsBridge) | ArkTS、C/C++ | 使用PostWebMessage系列Native接口，演示C/C++侧建立应用与前端页面的数据通道并收发string与buffer消息。 |
| 页面数据通道 | [ArkWebJsBridge](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ArkWebJsBridge) | ArkTS、C/C++ | 使用PostWebMessage系列Native接口，以ArkTS静态范式演示C/C++侧建立应用与前端页面数据通道并收发消息。 |
| 网络请求拦截 | [ArkWebSchemeHandler](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebSchemeHandler) | ArkTS、C/C++ | 使用SchemeHandler拦截Web组件网络请求，演示HTTP(s)及自定义协议请求拦截并构造自定义响应头与响应体。 |
| 网络请求拦截 | [ArkWebSchemeHandler](https://gitcode.com/openharmony/applications_app_samples/tree/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkWeb-Sta/ArkWebSchemeHandler) | ArkTS、C/C++ | 使用SchemeHandler拦截Web组件网络请求，以ArkTS静态范式演示HTTP(s)及自定义协议请求拦截与自定义响应构造。 |
| 崩溃信息收集 | [ArkWebGetDmpFiles](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebGetDmpFiles) | ArkTS、C/C++ | 使用Crashpad收集Web组件崩溃信息，演示渲染进程崩溃时dmp崩溃文件的获取、导出与查看，用于解析崩溃原因。 |
