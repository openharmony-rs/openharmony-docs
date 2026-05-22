# ArkWeb术语解释

## A

### ASYNC_RENDER

异步渲染模式，Web组件作为图形surface节点独立送显的渲染模式。

### 安全区域

Safe Area，屏幕中未被设备硬件或系统UI遮挡的区域。

## B

### backgroundColor()

背景颜色设置接口，用于设置Web组件的背景颜色属性。

### 白屏

White Screen，Web页面内容无法正常显示呈现空白状态的问题。

## C

### Canvas

画布组件，用于自定义绘制的ArkUI组件，支持同层渲染。

### canvas节点

Canvas Node，图形画布节点，Web渲染跟随系统送显的图形节点。

### color-scheme

配色方案属性，CSS属性，用于声明网页支持的配色方案。

### CORS策略

CORS Policy，跨源资源共享策略，用于控制跨域请求的安全机制。

### CSS环境变量

CSS Environment Variable，浏览器或系统提供的环境变量，如safe-area-inset-*。

### CSS系统颜色

CSS System Color，Web组件内置的默认颜色，应用于未定义样式的元素。

### 沉浸式效果

Immersive Effect，界面扩展至非安全区域最大化利用屏幕的效果。

### 触摸事件

Touch Event，用户触摸屏幕触发的交互事件。

## D

### darkMode()

深色模式设置接口，用于配置Web组件的深色模式状态。

### DevTools

开发者工具，用于调试前端页面和监听Web错误的工具集。

### DOMContentLoaded

DOM内容加载完成事件，HTML文档完全加载和解析完成后触发的事件。

### DOM节点

DOM Node，文档对象模型中的节点元素。

### DSS

显示子系统，Display Subsystem，负责显示合成的系统组件。

### 动态网页

Dynamic Web Page，内容动态加载和更新的网页类型。

### 导航栏

Navigation Bar，系统底部用于导航交互的UI区域。

## E

### embed标签

Embed Tag，HTML嵌入标签，可用于同层渲染的H5标签。

### enableNativeEmbedMode

开启同层渲染模式接口，用于启用Web组件同层渲染功能。

### env()

环境变量函数，CSS函数，用于获取浏览器或系统提供的环境变量。

### expandSafeArea()

扩展安全区域接口，用于设置组件扩展至非安全区域的属性。

## F

### file协议

File Protocol，本地文件访问协议，用于访问本地文件资源。

### Fit Content；适应内容

Web布局模式，使Web内容自动适应容器大小，保持正确的显示比例。

### FIT_CONTENT

自适应内容模式，Web组件大小根据页面内容自适应变化的布局模式。

### forceDarkAccess()

强制深色模式接口，用于开启Web组件强制深色模式功能。

### FrameNode

帧节点，ArkUI中的基础节点类型，用于构建节点树。

### 非安全区域

Unsafe Area，屏幕上被设备硬件或系统UI遮挡的区域。

## G

### getPageHeight

获取页面高度接口，用于获取当前网页内容的实际高度。

### getUserAgent

获取用户代理接口，用于获取Web组件当前的UserAgent字符串。

### 滚动条

Scrollbar，网页内容超出容器时显示的滚动指示条。

## H

### 花屏

Screen Distortion，页面内容显示混乱或颜色异常的问题。

### 黑屏

Black Screen，Web页面内容无法正常显示呈现黑色状态的问题。

## I

### imageAccess

图片访问权限，设置是否允许自动加载图片资源的属性。

### Immersive Effect；沉浸式效果

一种UI设计方式，界面内容充满屏幕，提供更广阔的视觉体验。

## J

### javaScriptAccess

JavaScript访问权限，设置是否允许执行JavaScript脚本的属性。

### javaScriptProxy

JavaScript代理接口，用于注册JavaScript对象到Web页面中。

### 静态网页

Static Web Page，内容固定不变的网页类型。

## K

### keyboardAvoidMode

键盘避让模式，设置Web组件如何响应键盘弹出避让的属性。

### 跨域

Cross-origin，不同源之间的资源访问行为。

## L

### layoutMode

布局模式接口，用于设置Web组件的布局方式。

### load事件

Load Event，网页的所有资源完全加载完成后触发的事件。

### 刘海屏

Notch Screen，顶部带有摄像头凹槽的异形屏幕。

## M

### metaviewport

元视口属性，用于设置网页视口的meta标签属性。

### MixedContent策略

MixedContent Policy，混合内容策略，用于控制HTTP和HTTPS混合内容的机制。

## N

### NativeEmbedStatus

同层嵌入状态，同层渲染标签的生命周期状态类型。

### NodeRenderType

节点渲染类型，定义节点渲染方式的类型枚举。

### 内存压力阈值

Memory Pressure Threshold，系统内存达到临界值的警戒状态。

### 内存泄漏

Memory Leak，内存资源未正确释放导致的内存消耗持续增长问题。

## O

### object标签

Object Tag，HTML对象标签，可用于同层渲染的H5标签。

### onClientAuthenticationRequest

客户端认证请求回调，服务器请求客户端证书时触发的回调。

### onErrorReceive

错误接收回调，资源加载失败时触发的回调。

### onFirstContentfulPaint

首次内容绘制回调，首次绘制有意义内容时触发的回调。

### onFirstMeaningfulPaint

首次有意义绘制回调，首次绘制有意义内容时触发的回调。

### onHttpAuthRequest

HTTP认证请求回调，服务器返回407需要认证时触发的回调。

### onHttpErrorReceive

HTTP错误接收回调，服务器返回HTTP错误码时触发的回调。

### onlineImageAccess

在线图片访问权限，设置是否允许从网络加载图片资源的属性。

### onNativeEmbedGestureEvent

同层嵌入手势事件回调，同层渲染区域触摸事件触发的回调。

### onNativeEmbedLifecycleChange

同层嵌入生命周期回调，同层标签生命周期变化时触发的回调。

### onNativeEmbedMouseEvent

同层嵌入鼠标事件回调，同层渲染区域鼠标事件触发的回调。

### onNativeEmbedObjectParamChange

同层嵌入对象参数变化回调，object标签内param元素变化时触发的回调。

### onNativeEmbedVisibilityChange

同层嵌入可见性变化回调，同层标签可见状态变化时触发的回调。

### onPageEnd

页面结束回调，网页加载完成时触发的回调。

### onSslErrorEvent

SSL错误事件回调，证书错误时触发的回调。

### overScrollMode

过滚动模式，设置Web组件滚动到边缘时的行为模式。

### OverScrollMode

过滚动模式类型，定义Web组件过滚动行为的类型枚举。

## P

### prefers-color-scheme

偏好配色方案，CSS媒体查询功能，用于检测系统主题颜色。

### 瀑布流页面

Waterfall Page，采用瀑布流布局的网页类型。

### 配色方案

Color Scheme，网页支持的配色方式声明。

## Q

### 强制深色模式

Force Dark Mode，强制转换网页元素为深色样式的模式。

### 浅色模式

Light Mode，标准亮度的显示模式。

### 浅色配色方案

Light Color Scheme，适合正常光环境的浅色配色方案。

## R

### registerNativeEmbedRule

注册同层嵌入规则接口，用于指定同层渲染的标签类型。

### RenderMode

渲染模式类型，定义Web组件渲染方式的类型枚举。

### RenderProcessMode

渲染进程模式类型，定义Web渲染进程运行方式的类型枚举。

### resource协议

Resource Protocol，应用资源访问协议，用于访问应用内资源文件。

### Responsive Layout；响应式布局

页面布局技术，使Web页面能够根据不同设备屏幕尺寸自动调整排版。

## S

### Safe Area Insets；安全区域

屏幕显示内容的安全边界区域，避免被系统UI元素遮挡。

### safe-area-inset-*

安全区域嵌入变量，CSS环境变量，定义安全区域与视口边缘的距离。

### SafeAreaEdge

安全区域边缘类型，定义安全区域扩展方向的类型枚举。

### SafeAreaType

安全区域类型，定义安全区域扩展类型的类型枚举。

### setCustomUserAgent

设置自定义用户代理接口，用于设置Web组件的UserAgent字符串。

### setPathAllowingUniversalAccess

设置路径允许通用访问接口，用于设置允许跨域访问的本地路径列表。

### setRenderProcessMode

设置渲染进程模式接口，用于设置WebView渲染进程运行方式。

### setWindowLayoutFullScreen

设置窗口全屏布局接口，用于设置应用窗口为全屏布局。

### SINGLE

单进程模式，WebView渲染进程采用单进程加载的模式。

### surface节点

Surface Node，图形表面节点，用于独立送显的图形节点。

### SYNC_RENDER

同步渲染模式，Web组件作为图形canvas节点跟随系统送显的渲染模式。

### 搜索栏

Search Bar，用于输入搜索关键词的UI组件。

### 深色模式

Dark Mode，降低屏幕亮度的显示模式，适合低光环境。

### 深色配色方案

Dark Color Scheme，适合低光环境的深色配色方案。

### 闪屏

Flash Screen，页面内容快速闪烁或切换的显示异常。

## T

### TextInput

文本输入组件，用于文本输入的ArkUI组件，支持同层渲染。

### 同层标签

Same-layer Tag，H5页面中用于同层渲染的embed或object标签。

### 同层渲染

Same-layer Render，将H5标签与ArkUI组件同步渲染的技术。

### 同层组件

Same-layer Component，与H5标签同步渲染的ArkUI组件。

### 同步渲染模式

Sync Render Mode，Web组件作为图形canvas节点跟随系统送显的渲染模式。

## U

### UserAgent

用户代理，标识浏览器类型和版本的字符串信息。

## V

### vh

视口高度单位，Viewport Height，相对于视口高度的CSS单位。

### Video

视频组件，用于播放视频的ArkUI组件，支持同层渲染。

### viewport-fit

视口适配属性，meta标签属性，用于设置网页在可视窗口中的布局方式。

## W

### WebDarkMode

Web深色模式类型，定义Web组件深色模式状态的类型枚举。

### WebLayoutMode

Web布局模式类型，定义Web组件布局方式的类型枚举。

### WebResourceResponse

Web资源响应类，用于构造自定义资源响应的数据结构。

### Web适配

使Web页面在不同设备上都能获得良好显示效果的技术方案。

### 挖孔区

Hole Area，屏幕上摄像头或传感器开孔区域。

### 物理像素

Physical Pixel，屏幕实际显示的最小像素单位。

### 纹理导出模式

Texture Export Mode，组件内容通过纹理导出进行渲染的模式。

### 网络超时

Network Timeout，网络请求超过规定时间未响应的状态。

### 网页内容高度

Web Page Content Height，网页实际内容的高度值。

### 网页背景色

Web Page Background Color，HTML网页元素的背景颜色属性。

## X

### XComponent

X组件，用于自定义渲染的ArkUI组件，支持同层渲染。

### 渲染模式

Render Mode，Web组件内容的渲染方式。

### 渲染进程启动失败

Render Process Start Failed，渲染进程无法成功启动的状态。

### 系统导航栏

System Navigation Bar，系统提供的底部导航栏UI区域。

### 系统非安全区域

System Unsafe Area，状态栏、挖孔区和导航栏等系统UI区域。

## Y

### 异形屏幕

Irregular Screen，具有特殊形状的屏幕，如刘海屏、挖孔屏等。

### 异步渲染模式

Async Render Mode，Web组件作为图形surface节点独立送显的渲染模式。

### 页面白屏

Page White Screen，页面加载后内容无法显示呈现白色的状态。

### 页面闪烁

Page Flickering，页面加载或跳转时出现的短暂视觉闪烁现象。

## Z

### 主题模式

Theme Mode，系统提供的浅色或深色显示主题。

### 自适应页面内容布局

Adaptive Page Content Layout，Web组件大小根据网页内容自适应的布局模式。

### 资源加载失败

Resource Load Failed，网页资源无法成功加载的状态。
