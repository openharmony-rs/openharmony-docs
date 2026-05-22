# ArkWeb术语解释

## A

### Abnormal Device Behavior；设备行为异常

模拟点击检测中的风险标签，表示设备连接状态、传感器状态等行为异常。

### Abnormal Device Integrity；设备完整性异常

模拟点击检测中的风险标签，表示设备完整性遭到破坏。

### AbnormalTap；异常点击

模拟点击检测中的风险标签，表示存在异常点击行为，如点击事件注入、自动化点击等。

### aboutToAppear

在创建自定义组件的新实例后，在执行其build函数前执行的回调函数。

### aboutToDisappear

自定义组件析构销毁时执行的函数，Web组件会被销毁。

### allowWindowOpenMethod

允许前端页面通过JavaScript函数调用的方式打开新窗口的接口。

### Audio thread

音频线程，应用进程中负责音频处理的线程。

## C

### ControllerHandler

控制器处理器，用于设置WebviewController的接口。

### crash

崩溃，渲染进程异常退出的一种原因。

### CustomDialog

自定义对话框，用于在新窗口中展示Web组件。

## D

### dataShare

数据共享，用于获取应用配置信息的能力。

### detachWeb

卸载Webview方法，用于将Web节点从组件树中移除。

### detectSimulatedClickRiskEnhanced

Web应用模拟点击检测接口，用于检测自动化点击、设备墙等作弊行为。

### 多进程模型

ArkWeb采用的多进程架构，分为应用进程、Web渲染进程、Web GPU进程、Web孵化进程和Foundation进程。

## E

### enterkeyhint

回车键提示属性，用于指定移动设备虚拟键盘上回车键的显示方式。

### expandSafeArea

扩展安全区域，用于设置Web组件不发生避让行为。

### ExtensionAbility

扩展能力，一种特殊的应用组件类型。

## F

### FCP；首次内容绘制

First Contentful Paint，首次绘制文本、图像、非空白Canvas或SVG的时间点。

### fileIo

文件IO，用于进行文件读写操作的接口。

### Foundation process

Foundation进程，系统唯一的进程，负责管理应用进程和Web渲染进程的绑定关系。

### frame

框架元素，用于展示HTML页面的元素。

### frameset

框架集，用于包含frame的HTML标签。

## G

### getRenderProcessMode

获取渲染子进程模式接口，用于查询当前的渲染子进程模式。

### GPU process

GPU进程，应用唯一的进程，负责光栅化、合成送显等与GPU交互的功能。

## I

### iframe

内嵌框架，HTML中用于嵌入另一个HTML文档的元素。

### inputmode

输入模式属性，用于配置输入法类型。

## J

### JIT；即时编译

Just-In-Time compilation，在运行时将代码编译为机器码的技术。

### js-error

JavaScript错误，在Web组件接口调用时抛出的异常。

### jsStack

JavaScript调用栈，渲染进程无响应时的调试信息。

### JWS

JSON Web Signature，基于JSON格式的Web签名标准，用于模拟点击检测结果的安全传输。

### 坚盾守护模式

提供给高安全需求用户的系统级别安全模式，通过限制设备基础功能增强安全性。

## K

### keyboard-return

键盘返回属性，用于指定系统软键盘的Enter键类型。

### KeyboardAvoidMode

键盘避让模式，用于设置Web页面的软键盘避让方式。

## L

### LCP；最大内容绘制

Largest Contentful Paint，绘制可视区域内最大图片、文本块或视频的时间点。

### 离线节点

通过BuilderNode创建的不立即挂载到组件树的Web组件节点。

## M

### main frame

主框架，网页的主要展示区域。

### makeNode

用于构建节点树、返回节点挂载在对应NodeContainer中的方法。

### MathML

数学标记语言，用于在网页中表示数学公式。

### MediaDevices.getUserMedia

媒体设备接口，用于请求访问流媒体设备如摄像头和麦克风。

### multiWindowAccess

多窗口访问权限，用于设置是否允许网页在新窗口打开。

### MyNodeController

自定义节点控制器，用于控制和反馈对应NodeContainer上的节点行为。

## N

### nameddest

命名目标参数，用于指定PDF文档中的命名目标位置。

### NativeMessaging

原生消息通信，浏览器扩展与系统应用之间的消息交换机制。

### NavigationPolicy

导航策略，用于通知应用新窗口的打开方式。

### NodeContainer

自定义占位组件，用于与NodeController节点绑定实现动态组件页面显示。

### NodeController

节点控制器，用于控制和反馈对应NodeContainer上的节点行为。

### 内存溢出

Out of Memory，内存不足导致的进程异常退出原因。

## O

### onActivateContent

激活内容事件，当Web组件需要展示到前台时触发的回调。

### onConnectNative

连接原生事件，当浏览器扩展调用runtime.connectNative时触发的回调。

### onControllerAttached

控制器绑定事件，当Controller成功绑定到Web组件时触发的回调。

### onDisAppear

组件卸载消失事件，组件卸载时触发的回调。

### onDisconnectNative

断开原生连接事件，当浏览器扩展销毁runtime.port时触发的回调。

### onInterceptKeyboardAttach

拦截键盘绑定事件，在软键盘拉起前控制软键盘显示的回调。

### onInterceptRequest

拦截请求事件，当Web组件加载url之前触发，用于拦截url并返回响应数据。

### onLargestContentfulPaint

最大内容绘制事件，网页绘制页面最大内容的回调。

### onLoadIntercept

加载拦截事件，当Web组件加载url之前触发，用于判断是否阻止此次访问。

### onOverrideUrlLoading

覆盖URL加载事件，当URL将要加载到当前Web中时让宿主应用程序获得控制权。

### onPageBegin

页面开始事件，网页开始加载时触发的回调，且只在主frame触发。

### onPageVisible

页面可见事件，当HTTP响应的主体开始加载，新页面即将可见时触发的回调。

### onProgressChange

进度变化事件，告知开发者当前页面加载进度。

### onRenderExited

渲染退出事件，应用渲染进程异常退出时触发的回调。

### onRenderProcessNotResponding

渲染进程无响应事件，当Web组件无法处理输入事件时触发的回调。

### onRenderProcessResponding

渲染进程响应事件，当渲染进程恢复至正常运行状态时触发的回调。

### onWindowExit

窗口退出事件，当新窗口关闭时触发的回调。

### onWindowNew

新窗口事件，当有新窗口打开时触发的回调。

### onWindowNewExt

扩展新窗口事件，功能增强的新窗口事件回调。

### OOM；内存溢出

Out of Memory，内存不足导致的进程异常退出原因。

### OVERLAYS_CONTENT

覆盖内容模式，不调整任何视口大小，获焦input元素没有滚动到可视区域的行为。

## P

### pipe

管道，用于进程间通信的双向数据通道。

### ProcessCrashed

进程崩溃，渲染进程异常退出的一种原因。

### 平移模式

Offset模式下，应用窗口高度不变，ArkWeb组件根据自身避让模式进行避让。

## R

### rebuild

重新构建方法，用于触发makeNode刷新节点。

### RenderExitReason

渲染退出原因，用于标识渲染进程退出的具体原因。

### renderExitReason

渲染退出原因参数，表示渲染进程退出的具体原因。

### RESIZE_CONTENT

调整内容模式，调整可视视口和布局视口的大小。

### RESIZE_VISUAL

调整可视视口模式，仅调整可视视口大小而不调整布局视口大小。

### riskDecision

风险检测结果，包含fake（存在作弊风险）、likelyReal（真人可能性较高）、unknown（无法识别）三种状态。

### RTCDataChannel

实时通信数据通道，WebRTC API中用于建立双向数据通道的接口。

### runtime.connectNative

运行时连接原生接口，用于创建NativeMessaging连接。

### runtime.port

运行时端口，浏览器扩展与应用之间的通信端口。

### 软键盘

移动设备上的虚拟键盘，用于输入文字。

### 软键盘避让

Web页面为避开软键盘显示区域而进行的布局调整。

## S

### SafeAreaType.KEYBOARD

键盘安全区域类型，用于扩展安全区域避开软键盘。

### Secure Shield Mode；安全模式

设备安全特性，查询设备安全模式能力用于确定设备的安全防护级别。

### Service Worker

服务工作线程，实现离线缓存、网络请求拦截和推送通知的机制。

### setKeyboardAvoidMode

设置键盘避让模式接口，用于设置UIContext的软键盘避让模式。

### setWebController

设置Web控制器接口，用于将新窗口对应WebviewController返回给Web内核。

### sharedRenderProcessToken

共享渲染进程令牌，标识当前Web组件所指定的共享渲染进程的token。

### showTextInput

显示文本输入接口，用于设置软键盘自动弹出功能。

### Signature；签名

JWS的一部分，使用证书对Header和Payload计算的数字签名。

### SpeechRecognition

语音识别，Web Speech API中用于语音识别的能力。

### SpeechSynthesis

语音合成，Web Speech API中用于语音合成的能力。

### stopNativeConnection

停止原生连接接口，用于主动断开一条NativeMessaging连接。

## T

### Tags

模拟点击关键特征标签列表，用于描述检测到的具体作弊行为类型。

### terminateRenderProcess

终止渲染进程接口，用于主动关闭渲染进程。

### terminateSelf

终止自身接口，用于WebNativeMessagingExtensionAbility主动退出。

### type属性

类型属性，定义了input元素的类型。

## U

### UIAbility

用户界面能力，用于展示图形界面的应用组件。

### UIContext

UI上下文，用于保存和管理UI相关上下文信息的对象。

## V

### Video thread

视频线程，应用进程中负责视频处理的线程。

### virtualKeyboard

虚拟键盘，移动设备上的软键盘。

## W

### WebAssembly

Web汇编，用于在Web上运行C/C++等低级语言编译代码的技术。

### WebExtensions runtime API

Web扩展运行时API，用于浏览器扩展与系统应用交换消息。

### WebGL

Web图形库，提供3D图形绘制能力的JavaScript API。

### WebGPU process

Web GPU进程，负责光栅化、合成送显等与GPU交互的功能。

### WebKeyboardAvoidMode

Web键盘避让模式，用于设置ArkWeb组件的键盘避让模式。

### WebKeyboardController

Web键盘控制器，用于控制自定义软键盘的输入、删除、关闭等行为。

### WebNativeMessagingExtensionAbility

Web原生消息扩展能力，为浏览器扩展提供后台服务能力的组件。

### WebNativeMessagingExtensionContext

Web原生消息扩展上下文，提供WebNativeMessagingExtensionAbility的上下文环境。

### WebNativeMessagingExtensionManager

Web原生消息扩展管理器，负责建立和管理NativeMessaging连接。

### WebOptions

Web选项，用于配置Web组件初始化参数的对象。

### WebviewController

Web视图控制器，用于控制Web组件行为的控制器对象。

### Web孵化进程

Web孵化进程，系统唯一的进程，负责孵化Web渲染进程与Web GPU进程。

### Web渲染进程

Web Render Process，负责运行Web渲染进程引擎和ArkWeb执行引擎的进程。

### window.open

窗口打开方法，JavaScript中用于打开新窗口的方法。

## X

### 性能指标

网页加载过程中需要关注的重要指标，如FCP、FMP、LCP等。

### 新窗口

网页通过JavaScript或用户操作打开的额外浏览窗口。

## Z

### zoomIn

放大接口，用于放大网页显示。

### zoomOut

缩小接口，用于缩小网页显示。

### 自定义占位节点

用于控制Web节点挂载与移除的占位组件。

### 自定义节点

开发者通过BuilderNode创建的可自定义控制的节点。

### 自定义软键盘

应用程序完全自定义的软键盘，替代系统软键盘。
