# ArkWeb术语
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

## A

### ArkUI Gestures；ArkUI手势

Web组件作为通用组件接收的ArkUI手势，作用于Web组件本身而非网页。

### ArkWeb

ArkWeb（方舟Web）提供了Web组件，用于在应用中显示Web页面内容。

### ArkWeb Gestures；ArkWeb手势

ArkWeb组件接收触摸事件自动生成的手势，作用于网页上。

### Adaptive Page Content Layout；自适应页面内容布局

Web组件大小根据网页内容自适应的布局模式。

### Async Render Mode；异步渲染模式

Web组件作为图形surface节点独立送显的渲染模式。

## B

### Background Rendering；后台渲染

在后台预先渲染Web页面内容的过程。

### Black Screen；黑屏

Web页面内容无法正常显示呈现黑色状态的问题。

### Breakpad

崩溃信息处理项目，用于编译minidump_stackwalk工具的项目源码。

## C

### Canvas

画布组件，用于自定义绘制的ArkUI组件，支持同层渲染。

### Canvas Node；canvas节点

图形画布节点，Web渲染跟随系统送显的图形节点。

### Chromium Version；Chromium版本

ArkWeb内核基于谷歌Chromium内核开发，不同系统版本对应不同Chromium版本。

### Color Scheme；配色方案

网页支持的配色方式声明。

### CORS Policy；CORS策略

跨源资源共享策略，用于控制跨域请求的安全机制。

### Crashpad

Chromium内核提供的进程崩溃信息处理工具，用于记录进程崩溃信息。

### CSS Environment Variable；CSS环境变量

浏览器或系统提供的环境变量，如safe-area-inset-*。

### CSS System Color；CSS系统颜色

Web组件内置的默认颜色，应用于未定义样式的元素。

### color-scheme

配色方案属性，CSS属性，用于声明网页支持的配色方案。

## D

### DOMContentLoaded

DOM内容加载完成事件，HTML文档完全加载和解析完成后触发的事件。

### Dark Color Scheme；深色配色方案

适合低光环境的深色配色方案。

### Dark Mode；深色模式

降低屏幕亮度的显示模式，适合低光照环境。

### Data Detector；智能分词

自动识别页面中的电话号码、网址等信息并提供交互操作。

### DevTools

开发者工具，用于调试前端页面和监听Web错误的工具集。

### DOM Node；DOM节点

文档对象模型中的节点元素。

### DSS

显示子系统，Display Subsystem，负责显示合成的系统组件。

### Drag and Drop；拖放

Drag and Drop，将元素从一个位置拖到另一个位置并放置的操作。

### Dynamic Component；动态组件

通过NodeController和BuilderNode创建的可动态挂载和移除的组件。

### Dynamic Web Page；动态网页

内容动态加载和更新的网页类型。

### darkMode()

深色模式设置接口，用于配置Web组件的深色模式状态。

### domStorageAccess

DOM存储访问权限，用于开启文档对象模型存储功能，使Web组件能够使用window.localStorage。

### dragging；拖滑

手指未离开屏幕时的滚动行为。

### dump file；dmp文件

崩溃转储文件，记录进程崩溃信息的二进制格式文件，后缀为dmp。

## E

### Embed Tag；embed标签

HTML嵌入标签，可用于同层渲染的H5标签。

### Env()

环境变量函数，CSS函数，用于获取浏览器或系统提供的环境变量。

## F

### File Descriptor；文件描述符

用于传递PDF文件信息的文件标识符。

### Fit Content；适应内容

Web布局模式，使Web内容自动适应容器大小，保持正确的显示比例。

### Flash Screen；闪屏

页面内容快速闪烁或切换的显示异常。

### Fling；抛滑

手指离开屏幕时带有速度，离手后页面继续滚动。

### Focus Chain；焦点链

焦点在应用内组件之间转移的路径。

### Focus Transition；走焦

焦点在组件或元素之间转移的行为。

### Force Dark Mode；强制深色模式

强制转换网页元素为深色样式的模式。

### FrameNode

帧节点，ArkUI中的基础节点类型，用于构建节点树。

### file协议

File Protocol，本地文件访问协议，用于访问本地文件资源。

## G

### Gesture；手势

用户通过触摸屏幕进行的交互动作，如点击、长按、滑动等。Web组件支持多种手势事件处理。

### Gesture Blocking；手势拦截

拦截Web组件的手势事件。

### Gesture Conflict Handling；手势冲突处理

处理ArkUI手势与ArkWeb手势的冲突。

### Gesture Recognition；手势识别

识别用户触摸屏交互产生的手势。

## H

### HAP

HarmonyOS Ability Package，鸿蒙应用包。包含应用代码、资源和配置文件的部署单元。

### Hole Area；挖孔区

屏幕上摄像头或传感器开孔区域。

## I

### Immersive Effect；沉浸式效果

界面扩展至非安全区域最大化利用屏幕的效果。

### Irregular Screen；异形屏幕

具有特殊形状的屏幕，如刘海屏、挖孔屏等。

## J

### JSBridge

JavaScript桥接，应用与Web页面之间进行JavaScript交互的机制。

## L

### Light Color Scheme；浅色配色方案

适合正常光照环境的浅色配色方案。

### Light Mode；浅色模式

标准亮度的显示模式。

### Local PDF Document；本地PDF文档

存储在应用本地资源目录中的PDF文档。

## M

### Media Playback Hosting；媒体播放托管

Web组件的媒体播放由应用侧托管。

### Memory Leak；内存泄漏

内存资源未正确释放导致的内存消耗持续增长问题。

### Memory Pressure Threshold；内存压力阈值

系统内存达到临界值的警戒状态。

### Mixed Content Policy；MixedContent策略

混合内容策略，用于控制HTTP和HTTPS混合内容的机制。

## N

### Named Destination；命名目标

PDF文档中预定义的目标位置，可用于直接导航到指定位置。

### NativeEmbedStatus

同层嵌入状态，同层渲染标签的生命周期状态类型。

### NavDestination

导航目标组件，用于页面导航，是Navigation路由的一部分。

### Navigation

导航组件，用于管理页面导航和路由的UI组件。

### Navigation Bar；导航栏

系统底部用于导航交互的UI区域。

### Network Hosting；网络托管

Web组件的网络请求由应用侧托管。

### Network PDF Document；网络PDF文档

通过网络URL访问的PDF文档。

### NodeRenderType

节点渲染类型，定义节点渲染方式的类型枚举。

### Notch Screen；刘海屏

顶部带有摄像头凹槽的异形屏幕。

## O

### origin

源，表示请求权限的网页来源。只有当协议、域名和端口都匹配时，两个对象才具有相同的源。

## P

### PDF Document in Application Sandbox；应用沙箱内PDF文档

存储在应用沙箱目录内的PDF文档。

### Page Flickering；页面闪烁

页面加载或跳转时出现的短暂视觉闪烁现象。

### Pre-render Web page；预渲染Web页面

在Web页面启动或跳转的场景下，预先在后台创建Web组件，加载数据并完成渲染，从而实现快速显示。

### Pre-start render process；预启动渲染进程

在未进入Web页面时，提前创建空Web组件，启动Web的渲染进程，为后续使用做好准备。

### Print Adapter；打印适配器

用于渲染Web页面内容并生成PDF文件信息的组件。

### prefers-color-scheme

偏好配色方案，CSS媒体查询功能，用于检测系统主题颜色。

## R

### Render Mode；渲染模式

Web组件内容的渲染方式。

### Render Process Start Failed；渲染进程启动失败

渲染进程无法成功启动的状态。

### RenderMode

渲染模式类型，定义Web组件渲染方式的类型枚举。

### RenderProcessMode

渲染进程模式类型，定义Web渲染进程运行方式的类型枚举。

### Resource Protocol；resource协议

应用资源访问协议，用于访问应用内资源文件。

### Responsive Layout；响应式布局

页面布局技术，使Web页面能够根据不同设备屏幕尺寸自动调整排版。

### registerNativeEmbedRule

注册同层嵌入规则接口，用于指定同层渲染的标签类型。

## S

### Safe Area；安全区域

屏幕中未被设备硬件或系统UI遮挡的区域。

### Safe Area Insets；安全区域

屏幕显示内容的安全边界区域，避免被系统UI元素遮挡。

### SafeAreaEdge

安全区域边缘类型，定义安全区域扩展方向的类型枚举。

### SafeAreaType

安全区域类型，定义安全区域扩展类型的类型枚举。

### Same-layer Component；同层组件

与H5标签同步渲染的ArkUI组件。

### Same-layer Render；同层渲染

将H5标签与ArkUI组件同步渲染的技术。

### Same-layer Tag；同层标签

H5页面中用于同层渲染的embed或object标签。

### Scheme Handler

Scheme处理器，用于拦截和处理Web组件发起的特定协议网络请求。

### Screen Distortion；花屏

页面内容显示混乱或颜色异常的问题。

### Search Bar；搜索栏

用于输入搜索关键词的UI组件。

### SINGLE

单进程模式，WebView渲染进程采用单进程加载的模式。

### Static Web Page；静态网页

内容固定不变的网页类型。

### Status Bar；状态栏

设备顶部显示系统状态的区域，点击可返回页面顶部。

### Subsystem

子系统，OpenHarmony架构中的功能模块划分单元。

### Surface Node；surface节点

图形表面节点，用于独立送显的图形节点。

### Sync Render Mode；同步渲染模式

Web组件作为图形canvas节点跟随系统送显的渲染模式。

### System Navigation Bar；系统导航栏

系统提供的底部导航栏UI区域。

### System Unsafe Area；系统非安全区域

状态栏、挖孔区和导航栏等系统UI区域。

### SYNC_RENDER

同步渲染模式，Web组件作为图形canvas节点跟随系统送显的渲染模式。

### soft keyboard；软键盘

移动设备上的虚拟键盘，用于输入文字。

### Soft Keyboard Avoidance；软键盘避让

Web页面为避开软键盘显示区域而进行的布局调整。

### safe-area-inset-*

安全区域嵌入变量，CSS环境变量，定义安全区域与视口边缘的距离。

## T

### TextInput

文本输入组件，用于文本输入的ArkUI组件，支持同层渲染。

### Texture Export Mode；纹理导出模式

组件内容通过纹理导出进行渲染的模式。

### Theme Mode；主题模式

系统提供的浅色或深色显示主题。

### Touch Event；触摸事件

用户触摸屏幕触发的交互事件。

## U

### Unsafe Area；非安全区域

屏幕上被设备硬件或系统UI遮挡的区域。

### UserAgent

用户代理，标识浏览器类型和版本的字符串信息。

## V

### Video

视频组件，用于播放视频的ArkUI组件，支持同层渲染。

### ViewTree

视图树，组件挂载的目标组件树。

### Visual Flickering；视觉闪烁

页面内容切换时产生的视觉闪烁现象。

### vh

视口高度单位，Viewport Height，相对于视口高度的CSS单位。

### viewport-fit

视口适配属性，meta标签属性，用于设置网页在可视窗口中的布局方式。

## W

### Web Dark Mode；Web深色模式类型

定义Web组件深色模式状态的类型枚举。

### Web Layout Mode；Web布局模式类型

定义Web组件布局方式的类型枚举。

### Web Page Content Height；网页内容高度

网页实际内容的高度值。

### Web Render Process

Web渲染进程，用于渲染Web内容的进程。

### WebResourceResponse

Web资源响应类，用于构造自定义资源响应的数据结构。

### Waterfall Page；瀑布流页面

采用瀑布流布局的网页类型。

### WebNativeMessagingExtensionAbility

Web原生消息扩展能力，为浏览器扩展提供后台服务能力的组件。

### White Screen；白屏

Web页面内容无法正常显示呈现空白状态的问题。

## X

### XComponent

X组件，用于自定义渲染的ArkUI组件，支持同层渲染。
