---
kits: ["ArkWeb Kit / 方舟Web"]
description: "汇总ArkWeb指南配套示例代码，按页面加载、请求拦截、前端页面交互、多媒体、同层渲染、离线Web组件等场景归类ArkTS与C/C++示例，供开发者对照实践。"
keywords: [ArkWeb, 示例代码, Web组件, JSBridge, 网络请求拦截, 同层渲染, 画中画, 离线Web组件, 前进后退缓存]
doctype: guide
status: active
---

# ArkWeb Kit指南配套示例代码
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @sinat_22543221-->
<!--Designer: @hwt00888022-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

| 场景分类 | Sample名称 | 语言 | 场景介绍 |
| -------- | -------- | -------- | -------- |
| 进程管理 | [ProcessWeb](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ProcessWeb) | ArkTS | 使用Web组件多进程能力管理渲染进程，演示进程模式设置、进程异常退出监听与终止，以及设置与网页一致的组件背景色消除跳转闪烁。 |
| 基本属性与事件 | [SetBasicAttrsEvtsTwo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsTwo) | ArkTS | 使用Web组件属性与webview接口，演示User-Agent获取与自定义、Cookie与数据存储管理、缓存模式配置及运动方向传感器数据获取。 |
| 基本属性与事件 | [SetBasicAttrsEvtsOne](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsOne) | ArkTS | 使用darkMode等属性配置Web组件，演示深色模式适配、地理位置权限管理、隐私模式及在新窗口中打开页面。 |
| 渲染模式与布局 | [WebRenderLayout](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebRenderLayout) | ArkTS | 使用Web组件渲染模式与布局属性，演示异步、同步渲染模式设置及FIT_CONTENT模式下组件高度随网页内容自适应。 |
| 获取网页高度 | [ArkWebPageHeight](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebPageHeight) | ArkTS | 使用Web组件回调与JSBridge获取网页内容高度，演示静态页面在生命周期回调中获取与动态页面由前端通知获取两种方式。 |
| 前端页面函数互调 | [UseFrontendJSApp](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/UseFrontendJSApp) | ArkTS | 使用runJavaScript与registerJavaScriptProxy，演示应用与前端页面函数互调及createMsgPort消息端口通信。 |
| 嵌套滚动与软键盘 | [ManageWebPageInteracts](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageInteracts) | ArkTS | 使用Web组件嵌套滚动与键盘避让属性，演示Web与ArkUI可滚动容器的嵌套滚动及对接系统软键盘的避让适配。 |
| 页面内容滚动 | [WebScrollDemo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebScrollDemo) | ArkTS | 使用scrollTo、pageUp等接口控制Web页面滚动，演示ArkTS侧接口与前端JS侧window.scrollTo两种滚动控制方式。 |
| 焦点管理 | [WebFocusManagement](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebFocusManagement) | ArkTS | 使用requestFocus、onFocus等接口管理Web组件焦点，演示组件级聚焦失焦与W3C标准网页元素的焦点管理。 |
| 手势交互 | [WebGestureInteraction](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebGestureInteraction) | ArkTS | 使用Web组件手势能力，演示手势识别与拦截、禁用缩放手势及滑动返回上一页面等常见手势问题处理。 |
| 网页缩放管理 | [WebManagementZooming](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebManagementZooming) | ArkTS | 使用zoom等接口管理网页缩放，演示启停手势及键鼠缩放、监听缩放比例变化与控制页面缩放到指定比例。 |
| 网页弹框 | [ShowWebPageDialog](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ShowWebPageDialog) | ArkTS | 使用onAlert等事件定制网页弹框，演示alert、confirm、prompt三种弹框的应用侧自定义实现与用户确认输入处理。 |
| 网页拖拽交互 | [WebDragInteraction](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebDragInteraction) | ArkTS | 使用Web组件拖拽能力与ArkTS侧onDrop事件，演示网页元素长按拖放、拖拽数据格式处理及禁止拖拽配置。 |
| 安全与隐私 | [ManageWebCompSecPriv](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebCompSecPriv) | ArkTS | 使用onInterceptRequest与广告过滤等能力，演示本地资源跨域问题解决、智能防跟踪及广告过滤。 |
| 页面加载 | [LoadPages](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/LoadPages) | ArkTS | 使用Web组件加载页面，演示加载网络页面、本地页面及HTML富文本数据等多种页面加载方式。 |
| 页面跳转与导航 | [ManagePageRedirectNav](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/ManagePageRedirectNav) | ArkTS | 使用onLoadIntercept拦截链接与历史记录接口，演示应用内页面跳转、跳转其他应用及浏览记录前进后退导航。 |
| 自定义请求响应 | [CustomizePageResp](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/CustomizePageResp) | ArkTS | 使用onInterceptRequest拦截页面请求，演示自定义响应头与响应体构造及预编译JavaScript生成CodeCache加速执行。 |
| 加速页面访问 | [AcceleratePageAccess](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess) | ArkTS | 使用ArkWeb Predictor等加速能力，演示域名预解析预连接、页面预加载、预编译JavaScript及离线资源注入。 |
| 缓存与窗口迁移 | [NetReqInterceptCacheWinOps](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/NetReqInterceptCacheWinOps) | ArkTS | 使用WebviewController接口配置前进后退缓存，演示BFCache的开启配置及Web组件在不同窗口间的迁移。 |
| 文件上传下载 | [ManageWebPageFileIO](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ManageWebPageFileIO) | ArkTS | 使用onShowFileSelector与下载接口，演示自定义文件上传及下载任务的监听、主动发起与恢复。 |
| 网页多媒体 | [UsingWebMultimedia](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/UsingWebMultimedia) | ArkTS | 使用WebRTC与媒体接管能力，演示在Web中打开摄像头和麦克风及应用接管网页媒体播放并用本地播放器渲染视频。 |
| 画中画播放 | [ArkWebPictureInPicture](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebPictureInPicture) | ArkTS | 使用Picture-in-Picture Web API，演示在浮动窗口中持续播放网页视频，以及监听全屏事件控制组件显隐实现沉浸式播放。 |
| 视频全屏播放 | [ArkWebFullScreen](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebFullScreen) | ArkTS | 使用Web组件全屏事件，演示监听进入与退出全屏并自动切换横竖屏的沉浸式视频播放。 |
| 打印与PDF预览 | [ProcessWebPageCont](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ProcessWebPageCont) | ArkTS | 使用Web组件打印与预览能力，演示前端页面打印、PDF文档预览及网页中安全区域计算和避让适配。 |
| 保存页面为PDF | [ArkWebCreatePdf](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebCreatePdf) | ArkTS | 使用createPdf方法将前端页面保存为PDF，演示callback与Promise两种调用方式。 |
| 网页菜单 | [ArkWebMenu](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebMenu) | ArkTS | 使用Web组件菜单能力，演示文本选中菜单、上下文菜单及自定义菜单的实现与配置。 |
| 剪贴板交互 | [ArkWebClipboard](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebClipboard) | ArkTS | 使用Web组件剪贴板能力，演示通过菜单、快捷键及W3C剪贴板接口对网页内容执行剪切、复制和粘贴。 |
| 网页智能分词 | [ArkWebDataDetector](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebDataDetector) | ArkTS | 使用Web组件智能分词能力，演示自动识别网页中电话号码、网址等实体并提供高亮、预览等交互操作。 |
| 同层渲染 | [UseSameLayerRender](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/UseSameLayerRender) | ArkTS | 使用embed与object标签实现同层渲染，演示同层渲染输入框及XComponent+AVPlayer视频组件嵌入网页。 |
| 离线Web组件 | [UseOfflineWebComp](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/UseOfflineWebComp) | ArkTS | 使用离线Web组件能力，演示组件创建与挂载、页面预渲染、渲染进程预启动及组件复用与释放策略。 |
| 前端页面调试 | [ArkWebDebuggingWithDevtools](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebDebuggingWithDevtools) | ArkTS | 使用setWebDebuggingAccess开启调试开关，演示通过USB或无线连接在电脑上用DevTools调试前端页面及端口转发配置。 |
| 加载问题定位 | [WebWriteScreenIssue](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/WebWriteScreenIssue) | ArkTS | 使用ArkWeb问题定位方法，演示白屏问题与网页加载失败问题的定位思路与解决方法。 |
| 前端页面函数互调 | [NdkJsBridge](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebJsInteraction/NdkJsBridge) | ArkTS、C/C++ | 使用ArkWeb_ControllerAPI等Native接口实现JSBridge，演示C/C++侧应用与前端页面的双向通信。 |
| 前端页面函数互调 | [NdkJsBridgeEX](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebJsInteraction/NdkJsBridgeEX) | ArkTS、C/C++ | 使用registerJavaScriptProxyEx等扩展接口，演示代理对象注册、权限控制等JSBridge扩展用法。 |
| 页面数据通道 | [ArkWebJsBridge](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebJsBridge) | ArkTS、C/C++ | 使用PostWebMessage系列Native接口，演示C/C++侧建立应用与前端页面的数据通道并收发string与buffer消息。 |
| 网络请求拦截 | [ArkWebSchemeHandler](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebSchemeHandler) | ArkTS、C/C++ | 使用SchemeHandler拦截Web组件网络请求，演示HTTP(s)及自定义协议请求拦截并构造自定义响应头与响应体。 |
| 崩溃信息收集 | [ArkWebGetDmpFiles](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkWeb/ArkWebGetDmpFiles) | ArkTS、C/C++ | 使用Crashpad收集Web组件崩溃信息，演示渲染进程崩溃时dmp崩溃文件的获取、导出与查看，用于解析崩溃原因。 |
