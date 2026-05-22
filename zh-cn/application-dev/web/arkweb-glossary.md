# ArkWeb术语
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

## A

### Abnormal Device Behavior；设备行为异常

模拟点击检测中的风险标签，表示设备连接状态、传感器状态等行为异常。

### Abnormal Device Integrity；设备完整性异常

模拟点击检测中的风险标签，表示设备完整性遭到破坏。

### AbnormalTap；异常点击

模拟点击检测中的风险标签，表示存在异常点击行为，如点击事件注入、自动化点击等。

### about:blank

空白页面，用于在离线Web组件不再被使用时加载，为下次复用做准备。

### aboutToAppear

在创建自定义组件的新实例后，在执行其build函数前执行的回调函数。

### aboutToDisappear

自定义组件析构销毁时执行的函数，Web组件会被销毁。

### aboutToResize

当布局大小发生变化时进行回调。

### AbsoluteOrientationSensor

绝对定向传感器，可获取表示设备绝对定位方向的四元数，包含X、Y、Z和W分量。

### Accelerometer

加速度传感器，可获取设备X、Y、Z轴方向的加速度数据。

### accept属性

HTML文件input元素的属性，定义文件input应该接受的文件类型。

### accessStep

WebviewController接口，判断当前页面是否可前进或后退指定步数。

### Active

活跃状态，开启渲染引擎的状态。

### addIntelligentTrackingPreventionBypassingList

添加智能防跟踪绕过域名列表接口，用于设置绕过智能防跟踪功能的域名列表。

### AlertDialog

ArkUI提供的警告对话框组件，用于显示包含可选信息的对话框。

### allowGeolocation

允许地理位置接口，用于设置允许指定来源使用地理位置权限。

### allowWindowOpenMethod

允许前端页面通过JavaScript函数调用的方式打开新窗口的接口。

### APPROXIMATELY_LOCATION

模糊定位权限，用于获取设备的大概位置信息。

### ArkUI手势

Web组件作为通用组件接收的ArkUI手势，作用于Web组件本身而非网页。

### ArkWeb_ComponentAPI

ArkWeb组件API，Native侧用于管理Web组件属性的函数指针结构体。

### ArkWeb_ControllerAPI

ArkWeb控制器API，Native侧用于控制Web组件的函数指针结构体。

### ArkWeb_JavaScriptValueAPI

ArkWeb JavaScript值API，Native侧用于创建和操作JavaScript值的函数指针结构体。

### ARKWEB_MEMBER_MISSING

ArkWeb成员缺失宏，用于校验函数结构体是否存在对应函数指针。

### ArkWeb_ProxyMethodWithResult

ArkWeb代理方法带返回值，支持返回值的Proxy方法结构体。

### ArkWeb_ProxyObjectWithResult

ArkWeb代理对象带返回值，支持返回值的Proxy对象结构体。

### ArkWeb_WebMessageAPI

ArkWeb Web消息API，Native侧用于创建和操作Web消息的函数指针结构体。

### ArkWeb_WebMessagePortAPI

ArkWeb Web消息端口API，Native侧用于管理消息端口的函数指针结构体。

### ArkWeb手势

ArkWeb组件接收触摸事件自动生成的手势，作用于网页上。

### ArkWeb简介

ArkWeb（方舟Web）提供了Web组件，用于在应用中显示Web页面内容。

### ArrayBuffer

数组缓冲区，JavaScript中用于存储二进制数据的对象类型。

### ASDF Webview

元服务内嵌网页渲染使用的官方Webview组件之一。

### Async Clipboard API

W3C异步剪贴板接口，提供给网页开发者读写系统剪贴板的方法。

### ASYNC_RENDER

异步渲染模式，Web组件作为图形surface节点独立送显的渲染模式。

### asyncMethodList

异步方法列表，javaScriptProxy接口的可选参数，指定异步执行的方法。

### AtomicServiceEnhancedWeb

元服务内嵌页面使用的增强型Web组件，提供更丰富的Web能力。

### Audio thread

音频线程，应用进程中负责音频处理的线程。

### autofocus

W3C标准属性，表示元素应在页面加载时或dialog显示时获焦。

### AVPlayer

音视频播放器，用于播放音频和视频媒体的组件。

### AVPlayerDemo

AVPlayer演示类，用于演示AVPlayer播放器功能的示例类。

### AVPlayerListener

AVPlayer监听接口，用于监听AVPlayer播放器状态变化的回调接口。

### 安全区域

Safe Area，屏幕中未被设备硬件或系统UI遮挡的区域。

### 按键走焦

通过Tab键、Shift+Tab键在组件之间转移焦点。

## B

### backgroundColor

背景颜色设置接口，用于设置组件的背景颜色属性。

### backgroundColor()

背景颜色设置接口，用于设置Web组件的背景颜色属性。

### backToTop

Web组件属性，开启后通过点击状态栏可将Web页面滚动到页面顶部。

### backward

WebviewController接口，返回上一个Web页面。

### bindContextMenu

ArkUI接口，将自定义菜单与Web组件绑定。

### bindSelectionMenu

Web组件接口，实现自定义菜单功能，支持长按图片、链接、文本触发菜单。

### Blank page

空白页面，用于在离线Web组件不再被使用时加载，为下次复用做准备。

### Breakpad

崩溃信息处理项目，用于编译minidump_stackwalk工具的项目源码。

### buffer

缓冲区，用于存储二进制数据的内存区域。

### BuilderNode

构建节点，用于动态构建UI组件的节点对象。

### bypassVsyncCondition

Web组件属性，用于加快Web组件首帧滚动绘制。

### 保存前端页面为PDF

Save Front-end Page as PDF，将Web页面内容保存为PDF文件的功能。

### 崩溃信息

Crash Information，记录进程崩溃原因、线程信息、寄存器信息等的数据。

### 崩溃原因

Crash Reason，导致进程异常终止的具体原因。

### 崩溃栈信息

Crash Stack Information，崩溃时的函数调用堆栈信息。

### 崩溃转储文件

Crash Dump File，记录进程崩溃时状态信息的二进制文件。

### 布局调整

Layout Adjustment，根据新的布局参数调整组件尺寸和位置的过程。

### 本地PDF文档

Local PDF Document，存储在应用本地资源目录中的PDF文档。

### 本地存储

Local Storage，Web浏览器提供的在客户端存储数据的机制。

### 本地离线资源

Local Offline Resource，存储在本地的离线网页资源。

### 白屏

White Screen，Web页面内容无法正常显示呈现空白状态的问题。

### 被动走焦

焦点因系统或其他操作而转移，无需开发者直接干预。

## C

### CacheMode

缓存模式类型枚举，定义缓存策略的类型。

### cacheMode()

缓存模式接口，用于配置页面资源的缓存模式属性。

### Callback

回调函数，用于异步处理结果的函数类型。

### Canvas

画布组件，用于自定义绘制的ArkUI组件，支持同层渲染。

### canvas节点

Canvas Node，图形画布节点，Web渲染跟随系统送显的图形节点。

### capture属性

HTML文件input元素的属性，指定使用哪个摄像头获取图片或视频数据。

### ChromeDriver

Selenium WebDriver与Web内核之间的中介驱动，将Selenium命令转换为Web内核能理解的协议。

### ChromeDriver Setup Tool；ChromeDriver设置工具

用于配置ChromeDriver路径和连接方式的工具类。

### Chromium版本

ArkWeb内核基于谷歌Chromium内核开发，不同系统版本对应不同Chromium版本。

### clearAllCookiesSync

清除所有Cookie同步接口，用于清除所有内存中的Cookie。

### clearIntelligentTrackingPreventionBypassingList

清除智能防跟踪绕过域名列表接口，用于清除所有绕过域名列表。

### Clipboard Event

W3C剪贴板事件接口，描述cut、copy和paste事件。

### ClipboardItem

W3C剪贴板对象，用于写入任意类型内容到系统剪贴板。

### close

关闭接口，用于关闭消息端口释放资源。

### CMakeLists.txt

CMake配置文件，用于配置Native模块编译规则。

### color-scheme

配色方案属性，CSS属性，用于声明网页支持的配色方案。

### configCookieSync

配置Cookie同步接口，用于设置指定URL的单个Cookie值。

### ConfirmDialog

ArkUI提供的确认对话框组件，用于验证用户是否接受某个操作。

### ControllerHandler

控制器处理器，用于设置WebviewController的接口。

### Cookie

Cookie数据，服务端生成并发送到客户端的数据。

### copyImage

WebContextMenuResult接口，复制网页中的图片到剪贴板。

### copyOptions

Web组件属性，指定Web组件上剪贴板复制的范围。

### CopyOptions.InApp

剪贴板复制范围选项，支持应用内复制。

### CopyOptions.LocalDevice

剪贴板复制范围选项，支持设备内复制，默认值。

### CopyOptions.None

剪贴板复制范围选项，不支持复制。

### copy事件

W3C剪贴板事件，用户执行复制操作时触发。

### CORS策略

CORS Policy，跨源资源共享策略，用于控制跨域请求的安全机制。

### crash

崩溃，渲染进程异常退出的一种原因。

### Crash address

崩溃地址，导致进程崩溃的内存地址。

### Crash reason

崩溃原因，导致进程crash的信号类型。

### Crashpad

Chromium内核提供的进程崩溃信息处理工具，用于记录进程崩溃信息。

### createImageAssetRequest

photoAccessHelper接口，创建图片资源请求。

### createNWeb

创建离线Web组件接口，用于初始化自定义Web组件。

### createPdf

创建PDF接口，用于将前端页面保存为PDF文件。

### createWebMessagePorts

创建Web消息端口接口，用于创建消息端口实现两端通信。

### createWebPrintDocumentAdapter

创建Web打印文档适配器接口，用于创建打印适配器并调起打印。

### CSS环境变量

CSS Environment Variable，浏览器或系统提供的环境变量，如safe-area-inset-*。

### CSS系统颜色

CSS System Color，Web组件内置的默认颜色，应用于未定义样式的元素。

### CustomContentDialog

ArkUI提供的自定义内容对话框组件，用于自定义弹框内容区。

### CustomDialog

自定义对话框，用于在新窗口中展示Web组件。

### cut事件

W3C剪贴板事件，用户执行剪切操作时触发。

### 传感器权限

Sensor Permission，用于访问设备传感器的权限。

### 持久化存储

Persistent Storage，数据写入本地永久保存的存储方式。

### 沉浸式全屏

一种视频全屏播放模式，视频扩展至整个系统屏幕显示，提供沉浸式的观看体验。

### 沉浸式效果

Immersive Effect，界面扩展至非安全区域最大化利用屏幕的效果。

### 触摸事件

Touch Event，用户触摸屏幕触发的交互事件。

## D

### darkMode()

深色模式设置接口，用于配置Web组件的深色模式状态。

### databaseAccess

数据库访问权限，设置是否允许使用Web SQL数据库。

### dataDetectorConfig

Web组件属性，配置智能分词识别类型和预览菜单功能。

### dataShare

数据共享，用于获取应用配置信息的能力。

### dataTransfer.setData

H5拖拽接口，设置拖拽数据。

### DatePicker

ArkUI日期选择器组件，与Web组件结合时会抢焦。

### Default

默认缓存模式，优先使用未过期的缓存。

### deleteAllData

删除所有数据接口，用于清除Web SQL当前使用的所有存储。

### deleteGeolocation

删除地理位置接口，用于清除指定来源的地理位置权限状态。

### deleteJavaScriptRegister

删除JavaScript注册接口，用于解除注册防止内存泄漏。

### destroyWebMessagePorts

销毁Web消息端口接口，用于释放消息端口内存。

### detachWeb

卸载Webview方法，用于将Web节点从组件树中移除。

### detectSimulatedClickRiskEnhanced

Web应用模拟点击检测接口，用于检测自动化点击、设备墙等作弊行为。

### DeviceCompat

设备兼容字段，前向兼容字段，标识设备类型。

### DeviceMotionEvent

设备运动事件，通过监听该事件可获取设备在X、Y、Z轴方向上的加速度数据和旋转速率数据。

### DeviceOrientationEvent

设备方向事件，通过监听该事件可获取设备绕X、Y、Z轴的角度。

### DeviceType

设备类型字段，标识当前设备类型如手机、平板、PC。

### DevTools

开发者工具，用于调试前端页面和监听Web错误的工具集。

### dispose

释放/销毁方法，用于销毁BuilderNode节点。

### dmp文件

崩溃转储文件，记录进程崩溃信息的二进制格式文件，后缀为dmp。

### DocumentSaveOptions

picker模块提供的文档保存选项对象。

### DocumentSelectOptions

picker模块提供的文档选择选项对象。

### DocumentViewPicker

picker模块提供的文档选择器。

### DOM Storage

DOM存储，包含Session Storage和Local Storage两类存储机制。

### DOMContentLoaded

DOM内容加载完成事件，HTML文档完全加载和解析完成后触发的事件。

### domStorageAccess

DOM存储访问权限，用于开启文档对象模型存储功能，使Web组件能够使用window.localStorage。

### DOM节点

DOM Node，文档对象模型中的节点元素。

### dragend事件

H5拖拽事件，拖拽结束时触发。

### draggable

HTML属性，设置元素是否可拖拽。

### dragover事件

H5拖拽事件，拖入目标区域时触发。

### dragstart事件

H5拖拽事件，拖拽开始时触发。

### Driver Setup Tool

驱动程序设置工具，用于配置ChromeDriver路径和连接方式。

### drop事件

H5拖拽事件，放置元素时触发。

### DSS

显示子系统，Display Subsystem，负责显示合成的系统组件。

### 动态组件

Dynamic Component，通过NodeController和BuilderNode创建的可动态挂载和移除的组件。

### 动态网页

Dynamic Web Page，内容动态加载和更新的网页类型。

### 地址

Address，可识别的实体类型之一，如地理位置。

### 多进程模型

ArkWeb采用的多进程架构，分为应用进程、Web渲染进程、Web GPU进程、Web孵化进程和Foundation进程。

### 导航栏

Navigation Bar，系统底部用于导航交互的UI区域。

### 打印框架

Print Framework，用于管理打印流程的系统框架。

### 打印适配器

Print Adapter，用于渲染Web页面内容并生成PDF文件信息的组件。

### 段错误

Segmentation Fault，内存访问权限错误导致的崩溃类型。

### 点击申请获焦

通过手势、鼠标或触摸板点击使组件获焦。

### 调用栈

Call Stack，函数调用的堆栈序列信息。

## E

### editMenuOptions

Web组件接口，对文本选中菜单进行自定义操作。

### EditMenuOptions

文本选中菜单自定义选项对象，包含onCreateMenu和onMenuItemClick方法。

### embed标签

Embed Tag，HTML嵌入标签，可用于同层渲染的H5标签。

### enableDataDetector

Web组件属性，设置是否启用智能分词功能。

### enableIntelligentTrackingPrevention

启用智能防跟踪接口，用于开启或关闭智能防跟踪功能。

### enableNativeEmbedMode

开启同层渲染模式接口，用于启用Web组件同层渲染功能。

### enableNativeMediaPlayer

开启接管网页媒体播放接口，用于开启应用接管网页中媒体播放的功能。

### enablePreviewMenu

智能分词配置项，设置是否启用分词长按预览功能。

### enableScrollInteraction

List组件属性，设置是否允许滚动交互。

### enableSelectedDataDetector

Web组件属性，单独配置文本选择AI菜单的启用情况。

### enterkeyhint

回车键提示属性，用于指定移动设备虚拟键盘上回车键的显示方式。

### enterpictureinpicture

进入画中画事件，当HTMLVideoElement成功进入画中画模式时触发的事件。

### env()

环境变量函数，CSS函数，用于获取浏览器或系统提供的环境变量。

### ESObject

ES对象类型，用于接收前端页面传递的对象类型参数。

### existCookie

存在Cookie接口，用于查询是否存在Cookie数据。

### exitPictureInPicture

退出画中画方法，用于退出画中画模式，视频将重新在原始标签页中显示。

### expandSafeArea

扩展安全区域，用于设置Web组件不发生避让行为。

### expandSafeArea()

扩展安全区域接口，用于设置组件扩展至非安全区域的属性。

### ExtensionAbility

扩展能力，一种特殊的应用组件类型。

### 二进制数据流

Binary Data Stream，PDF文件的二进制格式数据。

## F

### FCP；首次内容绘制

First Contentful Paint，首次绘制文本、图像、非空白Canvas或SVG的时间点。

### fetchCookieSync

获取Cookie同步接口，用于获取指定URL对应的Cookie值。

### fileAccess()

文件访问接口，用于设置是否允许Web组件访问本地文件。

### fileIo

文件IO，用于进行文件读写操作的接口。

### Files

H5拖拽数据格式，文件类型。

### filesDir

文件目录，应用沙箱中的文件存储目录。

### FileSelectorResult

文件选择器结果对象，用于处理文件上传结果。

### file协议

File Protocol，本地文件访问协议，用于访问本地文件资源。

### Fit Content；适应内容

Web布局模式，使Web内容自动适应容器大小，保持正确的显示比例。

### FIT_CONTENT

自适应内容模式，Web组件大小根据页面内容自适应变化的布局模式。

### FlingCancel

手势事件，取消抛滑时触发。

### FlingStart

手势事件，滚动过程中手指抬起且速度足够快时触发抛滑。

### focusable

Web组件属性，控制组件是否能够获取焦点。

### force

强制参数，用于强制回收所有离线Web组件，包括已绑定和未绑定的组件。

### forceDarkAccess()

强制深色模式接口，用于开启Web组件强制深色模式功能。

### forceEnableZoom

Web组件属性，控制网页强制缩放功能。

### Foundation process

Foundation进程，系统唯一的进程，负责管理应用进程和Web渲染进程的绑定关系。

### frame

框架元素，用于展示HTML页面的元素。

### FrameNode

帧节点，ArkUI中的基础节点类型，用于构建节点树。

### frameset

框架集，用于包含frame的HTML标签。

### Function

函数类型，用于传递回调函数的参数类型。

### 反编译

Decompilation，将机器码转换为可读源码的过程。

### 符号表

Symbol Table，用于调试和解析源码位置的符号信息表。

### 非安全区域

Unsafe Area，屏幕上被设备硬件或系统UI遮挡的区域。

## G

### geolocationAccess

地理位置访问权限，用于设置Web组件是否允许获取地理位置信息。

### GeolocationPermissions

地理位置权限管理类，用于管理网页的位置权限。

### Geolocation；地理位置

Web API，提供确定用户当前位置的能力。Web组件支持地理位置权限管理。

### GestureControl

手势控制模块，提供手势类型定义。

### GestureJudgeResult

手势判断结果，包含REJECT和CONTINUE两个值。

### GestureRecognizer

手势识别器，用于识别用户手势。

### GestureType.PAN_GESTURE

手势类型，滑动手势。

### Gesture；手势
用户通过触摸屏幕进行的交互动作，如点击、长按、滑动等。Web组件支持多种手势事件处理。

### getAcceptableFileTypes

文件选择器参数接口，获取可接受的文件类型。

### getAcceptType

文件选择器回调接口，返回accept属性值转换的文件扩展名数组。

### getAccessibleGeolocation

获取可访问地理位置接口，用于异步获取指定源的地理位置权限状态。

### getAccessibleResource

获取可访问资源接口，用于获取请求权限的资源类型。

### getCurrentPosition

获取当前位置方法，用于访问设备地理位置。

### getCustomUserAgent()

获取自定义用户代理接口，用于获取自定义的UserAgent字符串。

### getDefaultUserAgent

获取默认用户代理接口，用于获取系统默认的User-Agent字符串。

### getDescriptions

文件选择器参数接口，获取文件类型描述。

### getLinkUrl

WebContextMenuParam接口，获取上下文菜单点击位置的链接URL。

### getMimeTypes

文件选择器回调接口，返回accept属性值拆分后的字符串数组。

### getNWeb

获取离线Web组件接口，返回指定URL对应的NodeController。

### getPageHeight

获取页面高度接口，用于获取当前网页内容的实际高度。

### getPageOffset

WebviewController接口，获取Web组件的滚动偏移量。

### getPreviewHeight

WebContextMenuParam接口，获取预览窗口高度。

### getPreviewWidth

WebContextMenuParam接口，获取预览窗口宽度。

### getRenderProcessMode

获取渲染子进程模式接口，用于查询当前的渲染子进程模式。

### getSourceUrl

WebContextMenuParam接口，获取图片源URL。

### getSuggestedName

文件选择器参数接口，获取建议的文件名。

### getUserAgent

获取用户代理接口，用于获取Web组件当前的UserAgent字符串。

### getUserAgent()

获取用户代理接口，用于获取Web组件当前的UserAgent字符串。

### GPU process

GPU进程，应用唯一的进程，负责光栅化、合成送显等与GPU交互的功能。

### Gyroscope

陀螺仪传感器，可获取设备X、Y、Z轴方向的角速度数据。

### 广告拦截

Ad Blocking，拦截网页广告的功能。

### 滚动到底部事件回调

Scroll to Bottom Event Callback，用于监听PDF文档滚动到底部的事件回调函数。

### 滚动条

Scrollbar，网页内容超出容器时显示的滚动指示条。

### 跟踪型网站

Tracking Website，用于跟踪用户行为的第三方网站。

## H

### h5Port

H5端口，前端页面保存的消息端口对象。

### handleCancel

JsResult接口，处理弹框取消操作。

### handleConfirm

JsResult接口，处理弹框确认操作。

### handleFileList

FileSelectorResult接口，将选择的文件路径提交给ArkWeb。

### handlePromptConfirm

JsResult接口，处理提示框确认并返回输入值。

### HAP

HarmonyOS Ability Package，鸿蒙应用包。包含应用代码、资源和配置文件的部署单元。

### height

高度参数，用于设置PDF页面高度。

### Hidden

隐藏状态，离线Web组件创建后的初始状态，不会立即对用户呈现。

### Hilog日志

系统日志，记录系统运行信息的日志输出。

### host

主机字段，URL中的域名部分。

### HTMLVideoElement

HTML视频元素，HTML中用于嵌入视频内容的元素接口。

### HTML网页

HTML Web Page，使用HTML标记语言编写的网页文档。

### Hypium

HarmonyOS UI自动化测试框架，支持与Selenium集成进行Web应用测试。

### 后台定位

Background Location，在应用后台时获取设备位置信息的定位方式。

### 后台渲染

Background Rendering，在后台预先渲染Web页面内容的过程。

### 回调通知

Callback Notification，系统或组件通过回调方式发送的通知消息。

### 混合内容策略

MixedContent Policy，控制HTTP和HTTPS混合内容的机制。

### 缓存模式

Cache Mode，Web组件加载资源的缓存策略。

### 花屏

Screen Distortion，页面内容显示混乱或颜色异常的问题。

### 黑屏

Black Screen，Web页面内容无法正常显示呈现黑色状态的问题。

## I

### iframe

内嵌框架，HTML中用于嵌入另一个HTML文档的元素。

### IMAGE

WebElementType枚举值，图片类型元素。

### IMAGE_VIDEO_TYPE

PhotoViewMIMETypes枚举值，图片和视频类型。

### imageAccess

图片访问权限，设置是否允许自动加载图片资源的属性。

### Immersive Effect；沉浸式效果

一种UI设计方式，界面内容充满屏幕，提供更广阔的视觉体验。

### Inactive

不活跃状态，停止渲染引擎的状态。

### incognitoMode

隐私模式参数，用于创建隐私模式的Web组件。

### initializeWebEngine

初始化Web引擎接口，用于初始化ArkWeb内核。

### initialScale

Web组件属性，设置页面初始缩放比例。

### inputmode

输入模式属性，用于配置输入法类型。

### INTERNET

网络访问权限，用于访问网络资源。

### invoke

调用接口，用于处理位置权限请求的响应结果。

### isAcceptAllOptionExcluded

文件选择器参数接口，判断是否排除全部接受选项。

### isBound

是否绑定方法，用于检查离线Web组件是否被NodeContainer绑定。

### isIncognitoMode()

是否隐私模式接口，用于判断当前Web组件是否是隐私模式。

### isIntelligentTrackingPreventionEnabled()

是否启用智能防跟踪接口，用于判断是否开启智能防跟踪功能。

## J

### javaScriptAccess

JavaScript访问权限，设置是否允许执行JavaScript脚本的属性。

### javaScriptAccess()

JavaScript访问接口，用于设置是否允许执行JavaScript脚本。

### javaScriptOnDocumentStart

JavaScript文档开始接口，用于在文档加载开始时注入脚本。

### javaScriptProxy

JavaScript代理接口，用于注册JavaScript对象到Web页面中。

### javaScriptProxy()

JavaScript代理接口，用于将对象注入到Web端。

### JavaScript运行时

JavaScript Runtime，执行JavaScript代码的环境。

### JIT；即时编译

Just-In-Time compilation，在运行时将代码编译为机器码的技术。

### js-error

JavaScript错误，在Web组件接口调用时抛出的异常。

### JSBridge

JavaScript桥接，应用与Web页面之间进行JavaScript交互的机制。

### JSBridgeObject

JSBridge对象，Native侧实现JSBridge通信的业务类。

### JSON.stringify

JSON序列化方法，用于将对象转换为JSON字符串。

### JsResult

弹框结果对象，用于处理网页弹框的确认或取消操作。

### jsStack

JavaScript调用栈，渲染进程无响应时的调试信息。

### JWS

JSON Web Signature，基于JSON格式的Web签名标准，用于模拟点击检测结果的安全传输。

### 剪贴板

Clipboard，用于存储复制或剪切数据的系统组件。

### 加载成功/失败回调

Load Success/Failure Callback，用于监听PDF文档加载结果的回调函数。

### 加速度计

Accelerometer，用于测量设备加速度的传感器。

### 坚盾守护模式

提供给高安全需求用户的系统级别安全模式，通过限制设备基础功能增强安全性。

### 寄存器信息

Register Information，CPU寄存器在崩溃时的状态数据。

### 焦点

Focus，当前应用界面上唯一的一个可交互元素。

### 焦点链

Focus Chain，焦点在应用内组件之间转移的路径。

### 精准定位

Precise Location，获取设备精确位置信息的定位方式。

### 绝对定向

Absolute Orientation，获取设备绝对定位方向的传感器能力。

### 警告框

Alert Dialog，显示包含可选信息的对话框。

### 进程崩溃

Process Crash，进程因异常而终止运行的现象。

### 键盘缩放

通过Ctrl+'-'/'+'或Ctrl+鼠标滚轮进行页面缩放。

### 静态网页

Static Web Page，内容固定不变的网页类型。

### 静态资源文件缓存

Static Resource File Cache，应用静态资源的缓存存储。

## K

### Key-Value

键值对，数据存储的基本格式。

### keyboard-return

键盘返回属性，用于指定系统软键盘的Enter键类型。

### KeyboardAvoidMode

键盘避让模式，用于设置Web页面的软键盘避让方式。

### keyboardAvoidMode

键盘避让模式，设置Web组件如何响应键盘弹出避让的属性。

### KeyCode

按键码枚举，定义键盘按键对应的数值。

### 扩展区

Extension Area，三方应用可以扩展的User-Agent字段区域。

### 跨域

Cross-origin，不同源之间的资源访问行为。

### 跨域访问

Cross-origin Access，从一个源访问另一个源资源的行为。

## L

### layoutMode

布局模式接口，用于设置Web组件的布局方式。

### LCP；最大内容绘制

Largest Contentful Paint，绘制可视区域内最大图片、文本块或视频的时间点。

### leavepictureinpicture

退出画中画事件，当HTMLVideoElement成功退出画中画模式时触发的事件。

### libentry.so

Native模块库文件，编译生成的动态共享库。

### libohweb.so

ArkWeb Native库，提供Native接口的动态库。

### libweb_engine.so

Web引擎动态库，包含Web组件核心功能的共享对象文件。

### LLVM

编译器工具链，用于解析崩溃源码位置的工具集。

### llvm-addr2line

地址转行号工具，用于解析崩溃源码位置的LLVM工具链工具。

### loadUrl

加载URL方法，用于加载指定的Web页面。

### loadUrl()

加载URL接口，用于加载指定的网页地址。

### load事件

Load Event，网页的所有资源完全加载完成后触发的事件。

### Local Storage

本地存储，保存在应用目录下的持久化数据。

### localStorage

本地存储，Web浏览器提供的本地存储机制，用于在客户端存储数据。

### LOCATION

精准定位权限，用于获取设备的精确位置信息。

### LOCATION_IN_BACKGROUND

后台定位权限，用于在应用后台时获取设备位置信息。

### LONG_PRESS

WebResponseType枚举值，长按响应类型。

### LongPress

手势事件，按下且不移动经过延迟后触发。

### 刘海屏

Notch Screen，顶部带有摄像头凹槽的异形屏幕。

### 拦截请求

Intercept Request，拦截Web资源请求并自定义响应的操作。

### 离线节点

通过BuilderNode创建的不立即挂载到组件树的Web组件节点。

### 路由策略

Routing Strategy，应用内页面导航和跳转的管理策略。

### 逻辑层

Logic Layer，小程序架构中负责业务逻辑处理的部分。

### 链接

Link，可识别的实体类型之一，如网址URL。

## M

### main frame

主框架，网页的主要展示区域。

### maintainVisibleContentPosition

List组件属性，保持可见内容位置不变。

### makeNode

用于构建节点树、返回节点挂载在对应NodeContainer中的方法。

### marginBottom

下边距参数，用于设置PDF页面下边距。

### marginLeft

左边距参数，用于设置PDF页面左边距。

### marginRight

右边距参数，用于设置PDF页面右边距。

### marginTop

上边距参数，用于设置PDF页面上边距。

### MathML

数学标记语言，用于在网页中表示数学公式。

### max-fling-speed-x

viewport meta标签属性，限制横向抛滑速度。

### max-fling-speed-y

viewport meta标签属性，限制纵向抛滑速度。

### maximum-scale

viewport meta标签属性，设置页面最大缩放比例。

### maxSelectNumber

PhotoSelectOptions属性，设置最大选择数量。

### MediaDevices.getUserMedia

媒体设备接口，用于请求访问流媒体设备如摄像头和麦克风。

### MediaInfo

媒体信息，包含媒体资源相关信息的对象，用于在托管网页媒体播放时传递媒体信息。

### MediaStreamConstraints

媒体流约束对象，用于说明请求的媒体类型，包含video和audio两个成员。

### Memory overhead

内存开销，每个Web组件大约占用200MB内存和计算资源。

### Menu

ArkUI菜单组件，以垂直列表形式显示菜单项。

### MenuBuilder

菜单构建器，用于创建上下文菜单的ArkUI组件。与Web组件绑定可实现自定义右键菜单功能。

### MenuItem

ArkUI菜单项组件，展示菜单中具体的菜单项。

### MenuType.PREVIEW_MENU

菜单类型，预览菜单。

### MenuType.SELECTION_MENU

菜单类型，选择菜单。

### metaviewport

元视口属性，用于设置网页视口的meta标签属性。

### methodList

方法列表，javaScriptProxy接口的参数，指定要注册的方法。

### methodNameListForJsProxy

JS代理方法名称列表，用于标识对象中可被前端调用的方法。

### mimeType

MIME类型，标识文件内容类型的字符串。

### mimeTypeMap

MIME类型映射表，构造本地文件和MIME类型的映射表。

### minidump_stackwalk

小型转储栈遍历工具，用于解析dmp文件获取崩溃信息的工具。

### minimum-scale

viewport meta标签属性，设置页面最小缩放比例。

### MixedContent策略

MixedContent Policy，混合内容策略，用于控制HTTP和HTTPS混合内容的机制。

### Mobile

移动设备标识，User-Agent中表示移动设备的字段。

### multiple属性

HTML文件input属性，允许用户选择多个文件。

### multiWindowAccess

多窗口访问权限，用于设置是否允许网页在新窗口打开。

### MyNodeController

自定义节点控制器，用于控制和反馈对应NodeContainer上的节点行为。

### 命名目标

Named Destination，PDF文档中预定义的目标位置，可用于直接导航到指定位置。

### 媒体播放托管

Media Playback Hosting，Web组件的媒体播放由应用侧托管。

### 模糊定位

Approximate Location，获取设备大概位置信息的定位方式。

## N

### nameddest

命名目标参数，用于指定PDF文档中的命名目标位置。

### Native

原生，指直接访问应用沙箱的方式。

### Native JSBridge

Native JSBridge，使用Native接口实现JSBridge通信的方案。

### NativeEmbedStatus

同层嵌入状态，同层渲染标签的生命周期状态类型。

### NativeMediaPlayer

本地媒体播放器，应用提供的用于接管网页媒体播放的本地播放器实例。

### NativeMediaPlayerBridge

本地媒体播放器桥接接口，本地播放器需要实现的接口，以便ArkWeb内核对本地播放器进行播控操作。

### NativeMediaPlayerHandler

本地媒体播放器处理器，由ArkWeb内核传递给应用的对象，用于将本地播放器的状态信息通知给ArkWeb内核。

### NativeMessaging

原生消息通信，浏览器扩展与系统应用之间的消息交换机制。

### Native侧

Native Side，运行C++代码的一侧环境。

### Native侧初始化

Native Side Init，Native侧的初始化过程。

### Native侧注册

Native Side Register，在Native侧注册对象和回调。

### Native访问

原生代码（Native Code）对应用沙箱数据的访问能力，通过Crashpad相关接口实现。

### NavDestination

导航目标组件，用于页面导航。

### Navigation

导航组件，用于管理页面导航和路由的UI组件。

### NavigationPolicy

导航策略，用于通知应用新窗口的打开方式。

### navigator.clipboard.read

W3C剪贴板接口，从系统剪贴板读取任意类型内容。

### navigator.clipboard.readText

W3C剪贴板接口，从系统剪贴板读取文本。

### navigator.clipboard.write

W3C剪贴板接口，将任意类型内容写入系统剪贴板。

### navigator.clipboard.writeText

W3C剪贴板接口，将文本写入系统剪贴板。

### navigator.geolocation

导航器地理位置接口，用于访问设备地理位置信息。

### navigator.mediaDevices.getUserMedia

获取用户媒体设备接口，W3C标准协议接口，用于打开摄像头和麦克风。

### navigator.userAgent

导航器用户代理，浏览器提供的User-Agent字符串属性。

### navpanes

导航窗格参数，用于控制PDF预览时侧边导航窗格的显示状态，1表示打开，0表示关闭。

### NdkGestureSetting

原生（NDK）手势设置接口，用于配置和管理设备手势识别功能。

### ndkProxy

NDK代理对象，Native侧注册到前端页面的代理对象名。

### Nested Scrolling；嵌套滑动

Web组件与父容器之间协调滚动行为的机制，支持同步滚动和惯性处理。

### nestedScroll

Web组件属性，设置嵌套滚动的模式。

### NestedScrollMode

嵌套滚动模式枚举，包含PARENT_FIRST和SELF_FIRST等值。

### Node-API

Node API，用于ArkTS与C++交互的接口。

### NodeContainer

自定义占位组件，用于与NodeController节点绑定实现动态组件页面显示。

### NodeController

节点控制器，用于控制和反馈对应NodeContainer上的节点行为。

### nodeMap

节点映射表，用于保存所需要的NodeController。

### NodeRenderType

节点渲染类型，定义节点渲染方式的类型枚举。

### None

无缓存模式，加载资源不使用缓存。

### 内存占用

Memory Usage，Web组件占用的内存资源，每个组件大约200MB。

### 内存压力阈值

Memory Pressure Threshold，系统内存达到临界值的警戒状态。

### 内存泄漏

Memory Leak，内存资源未正确释放导致的内存消耗持续增长问题。

### 内存溢出

Out of Memory，内存不足导致的进程异常退出原因。

## O

### object标签

Object Tag，HTML对象标签，可用于同层渲染的H5标签。

### Offline Web Component；离线Web组件

Offline Web Component，创建后不会立即挂载到组件树中的Web组件，状态为Hidden和Inactive。

### OH_ArkWeb_GetNativeAPI

获取ArkWeb Native API函数，用于获取Native侧API结构体。

### onActivateContent

激活内容事件，当Web组件需要展示到前台时触发的回调。

### onActive

开启渲染方法，用于开启渲染引擎进行渲染。

### onAlert

Web组件事件，监听网页alert方法。

### onAppear

菜单显示回调，菜单弹出时触发。

### onBackground

应用退到后台回调，在此回调中可释放离线Web组件。

### onBackPress

应用侧回调，用户按返回键时触发。

### onBind

绑定回调，用于跟踪离线Web组件的绑定状态。

### onBlur

应用侧通用失焦回调接口，组件失焦时触发。

### onClientAuthenticationRequest

客户端认证请求回调，服务器请求客户端证书时触发的回调。

### onConfirm

Web组件事件，监听网页confirm方法。

### onConnectNative

连接原生事件，当浏览器扩展调用runtime.connectNative时触发的回调。

### onContextMenuShow

Web组件事件，上下文菜单弹出时触发。

### onControllerAttached

控制器绑定事件，当Controller成功绑定到Web组件时触发的回调。

### onControllerAttached()

控制器绑定回调，WebviewController与组件绑定时触发的回调。

### onCreateMenu

文本选中菜单回调，自定义菜单项。

### onCreateNativeMediaPlayer

创建本地播放器回调，当网页中有媒体需要播放时触发的回调函数。

### onDisappear

菜单消失回调，菜单关闭时触发。

### onDisAppear

组件卸载消失事件，组件卸载时触发的回调。

### onDisconnectNative

断开原生连接事件，当浏览器扩展销毁runtime.port时触发的回调。

### onDragEnd

拖拽事件，由Web发起的拖拽元素结束拖拽时触发。

### onDragEnter

拖拽事件，拖拽元素进入Web区域时触发。

### onDragLeave

拖拽事件，拖拽元素离开Web区域时触发。

### onDragMove

拖拽事件，拖拽元素在Web区域移动时触发。

### onDragStart

拖拽事件，拖拽开始时触发。

### onDrop

拖拽事件，拖拽元素落入Web区域时触发。

### onErrorReceive

错误接收回调，资源加载失败时触发的回调。

### onFirstContentfulPaint

首次内容绘制回调，首次绘制有意义内容时触发的回调。

### onFirstMeaningfulPaint

首次有意义绘制回调，首次绘制有意义内容时触发的回调。

### onFocus

应用侧通用获焦回调接口，组件获焦时触发。

### onForeground

应用回到前台回调，在此回调中可恢复离线Web组件。

### onFullScreenEnter

进入全屏事件回调，当Web组件进入全屏模式时触发的回调函数。

### onFullScreenExit

退出全屏事件回调，当Web组件退出全屏模式时触发的回调函数。

### onGeolocationShow

地理位置显示事件，当网页请求位置权限时触发的回调。

### onGestureRecognizerJudgeBegin

手势识别器判断回调，识别器即将成功时触发。

### onHttpAuthRequest

HTTP认证请求回调，服务器返回407需要认证时触发的回调。

### onHttpErrorReceive

HTTP错误接收回调，服务器返回HTTP错误码时触发的回调。

### onInactive

停止渲染方法，用于在预渲染完成后停止渲染。

### onInterceptKeyboardAttach

拦截键盘绑定事件，在软键盘拉起前控制软键盘显示的回调。

### onInterceptRequest

拦截请求事件，当Web组件加载url之前触发，用于拦截url并返回响应数据。

### onInterceptRequest()

拦截请求回调，用于拦截Web资源请求并自定义响应。

### onKeyPreIme

Web组件事件，拦截键盘输入。

### onLargestContentfulPaint

最大内容绘制事件，网页绘制页面最大内容的回调。

### Online

在线缓存模式，加载资源不使用缓存全部从网络获取。

### onlineImageAccess

在线图片访问权限，设置是否允许从网络加载图片资源的属性。

### onLoadIntercept

加载拦截事件，当Web组件加载url之前触发，用于判断是否阻止此次访问。

### Only

仅缓存模式，只从缓存中加载资源。

### onMenuItemClick

文本选中菜单回调，处理菜单项点击事件。

### onmessage

消息接收事件，消息端口接收到消息时触发的事件。

### onMessageEvent

消息事件回调，消息端口接收消息时触发的回调。

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

### onOverrideUrlLoading

覆盖URL加载事件，当URL将要加载到当前Web中时让宿主应用程序获得控制权。

### onPageBegin

页面开始事件，网页开始加载时触发的回调，且只在主frame触发。

### onPageEnd

页面结束回调，网页加载完成时触发的回调。

### onPageVisible

页面可见事件，当HTTP响应的主体开始加载，新页面即将可见时触发的回调。

### OnPdfLoadEvent

PDF加载事件信息，包含PDF文档加载的URL和加载结果信息。

### onPdfLoadEvent

PDF加载事件回调，用于监听PDF文档加载成功或失败的事件。

### onPdfScrollAtBottom

PDF滚动到底部事件回调，用于监听PDF文档滚动到底部的事件。

### OnPdfScrollEvent

PDF滚动事件信息，包含PDF文档滚动事件的URL信息。

### onPermissionRequest

权限请求事件，当Web组件接收到权限请求时触发的回调。

### onProgressChange

进度变化事件，告知开发者当前页面加载进度。

### onPrompt

Web组件事件，监听网页prompt方法。

### onRenderExited

渲染退出事件，应用渲染进程异常退出时触发的回调。

### onRenderProcessNotResponding

渲染进程无响应事件，当Web组件无法处理输入事件时触发的回调。

### onRenderProcessResponding

渲染进程响应事件，当渲染进程恢复至正常运行状态时触发的回调。

### onScaleChange

Web组件事件，监听页面缩放比例变化。

### onScrollFrameBegin

Scroll组件事件，滚动帧开始时触发。

### onShowFileSelector

Web组件事件，处理前端页面文件上传请求。

### onSslErrorEvent

SSL错误事件回调，证书错误时触发的回调。

### onUnbind

解绑回调，用于跟踪离线Web组件的解绑状态。

### onWillHide

将要隐藏回调，在NavDestination中用于让当前Web组件加载空白页并取消与当前UI的关联。

### onWindowExit

窗口退出事件，当新窗口关闭时触发的回调。

### onWindowNew

新窗口事件，当有新窗口打开时触发的回调。

### onWindowNewExt

扩展新窗口事件，功能增强的新窗口事件回调。

### OOM；内存溢出

Out of Memory，内存不足导致的进程异常退出原因。

### OpenHarmony

开源鸿蒙，User-Agent中标识OpenHarmony系统的字段。

### origin

源参数，表示请求权限的网页来源。

### OSName

操作系统名称，User-Agent中的基础操作系统名称字段。

### OSVersion

操作系统版本，User-Agent中的操作系统版本字段。

### OVERLAYS_CONTENT

覆盖内容模式，不调整任何视口大小，获焦input元素没有滚动到可视区域的行为。

### overlay属性类型组件

ArkUI组件类型，默认抢焦，如Menu、DatePicker、TimePicker、弹窗等。

### overScrollMode

过滚动模式，设置Web组件滚动到边缘时的行为模式。

### OverScrollMode

过滚动模式类型，定义Web组件过滚动行为的类型枚举。

## P

### pageDown

WebviewController接口，将Web组件内容向下滚动半个视口或到底部。

### pageUp

WebviewController接口，将Web组件内容向上滚动半个视口或到顶部。

### PARENT_FIRST

NestedScrollMode枚举值，父组件优先滚动。

### Password Safe；密码保险箱

ArkWeb提供的隐私保护功能，可安全存储和自动填充用户密码。

### PASTE

TextMenuItemId枚举值，粘贴菜单项。

### paste

WebContextMenuResult接口，从剪贴板粘贴内容到网页。

### pasteAndMatchStyle

WebContextMenuResult接口，粘贴并匹配样式。

### paste事件

W3C剪贴板事件，用户执行粘贴操作时触发。

### PDF page

页码参数，使用整数指定PDF文档中的页码，文档第一页的pagenum值为1。

### PDF toolbar

工具栏参数，用于控制PDF预览时顶部工具栏的显示状态，1表示打开，0表示关闭。

### pdfArrayBuffer

PDF数组缓冲区方法，用于获取PDF二进制数据流。

### pdfbackgroundcolor

PDF背景色参数，用于指定PDF文档预览时的背景色，color为标准的六位十六进制RGB值。

### PdfConfiguration

PDF配置对象，用于设置PDF页面的各种参数。

### PdfData

PDF数据对象，用于存储生成的PDF二进制数据。

### PDF加载成功/失败回调

Load Success/Failure Callback，用于监听PDF文档加载结果的回调函数。

### PDF工具栏

Toolbar，PDF预览页面顶部的操作工具区域，包含各种操作按钮。

### PDF生成

PDF Generation，将Web页面内容转换为PDF文件的过程。

### PDF配置

PDF Configuration，用于设置PDF页面参数的配置对象。

### PDF页码

Page Number，PDF文档中页面的编号，用于指定跳转到特定页面。

### PDF预览

PDF Preview，在Web组件中预览PDF文档的功能。

### PDF；便携式文档格式

Portable Document Format，一种用于呈现文档的文件格式，独立于应用软件、硬件和操作系统。

### Peer-to-Peer；点对点

一种网络连接方式，允许在无需中间媒介的情况下建立浏览器之间的直接连接。

### permission

权限参数，javaScriptProxy接口的可选参数，用于权限控制。

### PermissionRequest

权限请求对象，用于处理Web组件的权限请求。

### photoAccessHelper

媒体库模块，提供图片和视频访问接口。

### PhotoSelectOptions

photoAccessHelper提供的图片选择选项对象。

### PhotoViewMIMETypes

photoAccessHelper提供的图片视图MIME类型枚举。

### PhotoViewPicker

photoAccessHelper提供的图片选择器。

### PickerMediaType

cameraPicker提供的媒体类型枚举。

### PickerProfile

cameraPicker提供的选择器配置对象。

### Picture-in-Picture；画中画

一种在浮动窗口中播放视频的功能，使用户在浏览其他网页或与其他应用交互时可继续观看视频。

### pictureInPictureElement

画中画元素，返回当前处于画中画模式的HTMLVideoElement元素，如果没有则返回null。

### pictureInPictureEnabled

画中画功能是否启用，用于检查浏览器是否支持画中画功能。

### PinchBegin

手势事件，捏合开始时触发。

### PinchEnd

手势事件，捏合结束时触发。

### PinchGesture

ArkUI捏合手势，双指或多指捏合触发。

### PinchUpdate

手势事件，捏合过程中触发。

### pipe

管道，用于进程间通信的双向数据通道。

### port

端口，消息通信中用于发送和接收消息的通道。

### postMessage()

发送消息接口，用于向消息端口发送消息。

### postMessageEvent

发送消息事件接口，用于向消息端口发送消息事件。

### postWebMessage

发送Web消息接口，用于向HTML侧发送消息端口。

### Pre-render Web page；预渲染Web页面

在Web页面启动或跳转的场景下，预先在后台创建Web组件，加载数据并完成渲染，从而实现快速显示。

### Pre-start render process；预启动渲染进程

在未进入Web页面时，提前创建空Web组件，启动Web的渲染进程，为后续使用做好准备。

### prefers-color-scheme

偏好配色方案，CSS媒体查询功能，用于检测系统主题颜色。

### preventDefault

H5接口，阻止事件默认行为。

### PRINT

打印权限，用于使用打印功能。

### print.html

打印HTML页面文件。

### print.print

打印接口，用于调起打印功能。

### privacy mode

隐私模式，不写入本地持久化存储的浏览模式。

### Process uptime

进程运行时间，进程从启动到崩溃的时间长度。

### ProcessCrashed

进程崩溃，渲染进程异常退出的一种原因。

### Promise

Promise对象，用于异步操作的承诺对象类型。

### 偏移地址

Offset Address，相对于基地址的内存地址偏移量。

### 平移模式

Offset模式下，应用窗口高度不变，ArkWeb组件根据自身避让模式进行避让。

### 抛滑

Fling，手指离开屏幕时带有速度，离手后页面继续滚动。

### 瀑布流页面

Waterfall Page，采用瀑布流布局的网页类型。

### 配色方案

Color Scheme，网页支持的配色方式声明。

## Q

### QR Code；二维码

一种二维条形码，通过特定几何图形记录信息。Web菜单支持识别页面中的二维码图片。

### 前端页面

Frontend Page，运行在Web组件中的H5页面。

### 前端页面打印

Front-end Page Printing，将Web页面内容进行打印的功能。

### 强制深色模式

Force Dark Mode，强制转换网页元素为深色样式的模式。

### 浅色模式

Light Mode，标准亮度的显示模式。

### 浅色配色方案

Light Color Scheme，适合正常光环境的浅色配色方案。

## R

### rawfile

原始文件目录，应用资源目录下的原始文件存储位置。

### read

W3C剪贴板接口，从系统剪贴板读取任意类型内容。

### READ_PASTEBOARD权限

应用访问剪贴板内容所需的权限。

### readText

W3C剪贴板接口，从系统剪贴板读取文本。

### rebuild

重新构建方法，用于触发makeNode刷新节点。

### recycledNWebs

已释放的离线组件集合，用于保存已释放的离线组件URL信息。

### recycleNWeb

回收离线Web组件接口，用于释放不再需要的离线Web组件。

### recycleNWebs

回收所有离线Web组件接口，用于释放所有离线Web组件。

### refresh()

刷新接口，用于重新加载当前页面。

### registerAsyncJavaScriptProxyEx

注册异步JavaScript代理扩展接口，支持异步方法返回值。

### registerJavaScriptProxy()

注册JavaScript代理接口，用于将对象注入到window对象中。

### registerJavaScriptProxyEx

注册JavaScript代理扩展接口，支持返回值的代理注册。

### registerNativeEmbedRule

注册同层嵌入规则接口，用于指定同层渲染的标签类型。

### RelativeOrientationSensor

相对定向传感器，可获取表示设备相对定位方向的四元数，包含X、Y、Z和W分量。

### removeCache()

清除缓存接口，用于清除已经缓存的资源。

### removeIntelligentTrackingPreventionBypassingList

移除智能防跟踪绕过域名列表接口，用于删除部分绕过域名。

### RenderExitReason

渲染退出原因，用于标识渲染进程退出的具体原因。

### renderExitReason

渲染退出原因参数，表示渲染进程退出的具体原因。

### RenderMode

渲染模式类型，定义Web组件渲染方式的类型枚举。

### RenderMode.SYNC_RENDER

渲染模式，同步渲染。

### RenderProcessMode

渲染进程模式类型，定义Web渲染进程运行方式的类型枚举。

### requestFocus

WebviewController接口，组件主动申请获焦。

### requestPictureInPicture

请求进入画中画方法，HTMLVideoElement接口提供的方法，用于请求进入画中画模式。

### RESIZE_CONTENT

调整内容模式，调整可视视口和布局视口的大小。

### RESIZE_VISUAL

调整可视视口模式，仅调整可视视口大小而不调整布局视口大小。

### resource://

资源路径，用于访问应用本地资源文件的路径协议。

### resource协议

Resource Protocol，应用资源访问协议，用于访问应用内资源文件。

### Responsive Layout；响应式布局

页面布局技术，使Web页面能够根据不同设备屏幕尺寸自动调整排版。

### restoreNWebs

恢复离线Web组件接口，用于恢复之前释放的离线Web组件。

### riskDecision

风险检测结果，包含fake（存在作弊风险）、likelyReal（真人可能性较高）、unknown（无法识别）三种状态。

### ROM

只读存储器，设备上预装的系统固件。

### RTCDataChannel

实时通信数据通道，WebRTC API中用于建立双向数据通道的接口。

### runJavaScript()

执行JavaScript接口，用于调用前端页面的JavaScript函数。

### runJavaScriptExt

WebviewController接口，执行JavaScript脚本并支持ArrayBuffer参数。

### runJavaScriptExt()

执行JavaScript扩展接口，支持ArrayBuffer参数类型。

### runtime.connectNative

运行时连接原生接口，用于创建NativeMessaging连接。

### runtime.port

运行时端口，浏览器扩展与应用之间的通信端口。

### 绕过域名列表

Bypass Domain List，绕过智能防跟踪功能的域名列表。

### 软键盘

移动设备上的虚拟键盘，用于输入文字。

### 软键盘避让

Web页面为避开软键盘显示区域而进行的布局调整。

## S

### Safe Area Insets；安全区域

屏幕显示内容的安全边界区域，避免被系统UI元素遮挡。

### safe-area-inset-*

安全区域嵌入变量，CSS环境变量，定义安全区域与视口边缘的距离。

### SafeAreaEdge

安全区域边缘类型，定义安全区域扩展方向的类型枚举。

### SafeAreaType

安全区域类型，定义安全区域扩展类型的类型枚举。

### SafeAreaType.KEYBOARD

键盘安全区域类型，用于扩展安全区域避开软键盘。

### SameSite

同站属性，Cookie的安全属性用于控制跨站请求。

### SandboxedHandler

沙箱处理程序，Crashpad中处理崩溃的沙箱化处理器。

### SandBox；沙箱

应用运行的隔离环境，限制应用对系统资源和个人数据的访问权限，保障系统安全。

### SaveButton

ArkUI安全组件，用于保存文件。

### SaveButtonOnClickResult

保存按钮点击结果，包含SUCCESS等值。

### SaveButtonOptions

保存按钮配置选项对象。

### saveCookieAsync

保存Cookie异步接口，用于强制将Cookie保存到磁盘。

### SaveDescription

保存按钮描述枚举，如SAVE_IMAGE。

### SaveIconStyle

保存按钮图标样式枚举。

### scale方法

Web组件方法，调整Web组件的缩放比例。

### Scheme Handler

Scheme处理器，用于拦截和处理Web组件发起的特定协议网络请求。

### schemeMap

协议映射表，构造域名和本地文件的映射表。

### ScrollBegin

手势事件，滚动开始时触发。

### scrollBy

WebviewController接口，将页面滚动指定的偏移量。

### ScrollEnd

手势事件，滚动结束时触发。

### scrollTo

WebviewController接口，将页面滚动到指定的绝对位置。

### ScrollType.EVENT

滚动类型枚举值，事件滚动。

### ScrollUpdate

手势事件，滚动时触发，包括抛滑和拖滑。

### SDK

软件开发工具包，提供开发接口的软件包。

### Secure Shield Mode；安全模式

设备安全特性，查询设备安全模式能力用于确定设备的安全防护级别。

### SEGV_MAPERR

段错误映射错误，表示内存映射错误的段错误类型。

### selectAll

WebContextMenuResult接口，选中全部内容。

### selection-api

W3C选区API，用于操作文本选区。

### selectionchange

H5事件，选区变更时触发。

### SelectionMenuOptionsExt

自定义菜单选项扩展对象，包含preview、menuType等配置。

### Selenium

Web应用自动化测试框架，模拟用户在浏览器中的操作。

### SELF_FIRST

NestedScrollMode枚举值，子组件优先滚动。

### Service Worker

服务工作线程，实现离线缓存、网络请求拦截和推送通知的机制。

### session cookie

会话Cookie，仅在会话期间有效的临时Cookie。

### Session Storage

会话存储，DOM Storage中的临时存储机制。

### set_chromedriver_exe_path

指定ChromeDriver可执行文件路径的方法。

### set_chromedriver_exe_search_path

指定ChromeDriver搜索文件夹路径的方法，系统会在下层文件夹中寻找对应版本文件。

### setAppCustomUserAgent()

设置应用自定义用户代理接口，用于设置应用级自定义User-Agent。

### setCustomUserAgent

设置自定义用户代理接口，用于设置Web组件的UserAgent字符串。

### setCustomUserAgent()

设置自定义用户代理接口，用于设置Web组件的UserAgent字符串。

### setKeyboardAvoidMode

设置键盘避让模式接口，用于设置UIContext的软键盘避让模式。

### setLazyInitializeWebEngine()

设置懒加载Web引擎接口，用于跳过初始化ArkWeb内核。

### setMessageEventHandler()

设置消息事件处理接口，用于注册消息端口接收回调。

### setPathAllowingUniversalAccess

设置路径允许通用访问接口，用于设置允许跨域访问的本地路径列表。

### setPathAllowingUniversalAccess()

设置路径允许通用访问接口，用于设置允许跨域访问的本地路径列表。

### setRenderProcessMode

设置渲染进程模式接口，用于设置WebView渲染进程运行方式。

### setScrollable

WebviewController接口，设置Web是否禁用触摸滚动。

### setUserAgentForHosts()

设置特定网站用户代理接口，用于对特定网站设置自定义User-Agent。

### setWebController

设置Web控制器接口，用于将新窗口对应WebviewController返回给Web内核。

### setWebDebuggingAccess()

设置Web调试访问接口，用于开启Web调试模式。

### setWindowLayoutFullScreen

设置窗口全屏布局接口，用于设置应用窗口为全屏布局。

### sharedRenderProcessToken

共享渲染进程令牌，标识当前Web组件所指定的共享渲染进程的token。

### shouldPrintBackground

打印背景参数，用于设置是否打印背景。

### showTextInput

显示文本输入接口，用于设置软键盘自动弹出功能。

### Signature；签名

JWS的一部分，使用证书对Header和Payload计算的数字签名。

### SIGSEGV

段错误信号，表示内存访问错误的信号类型。

### SINGLE

单进程模式，WebView渲染进程采用单进程加载的模式。

### Single Render Process Mode

单渲染进程模式，全局共享一个Web渲染进程的模式。

### Size

尺寸对象，用于表示布局的宽度和高度。

### SpeechRecognition

语音识别，Web Speech API中用于语音识别的能力。

### SpeechSynthesis

语音合成，Web Speech API中用于语音合成的能力。

### src

源参数，WebOptions的第一个参数，用于指定Web组件加载的内容地址。

### Static Web Page

静态网页，内容固定不变的网页类型。

### stopNativeConnection

停止原生连接接口，用于主动断开一条NativeMessaging连接。

### Subsystem

子系统，OpenHarmony架构中的功能模块划分单元。

### Surface

绘制表面，用于渲染媒体画面的绘制表面。

### SurfaceId

绘制表面ID，用于标识Surface的唯一标识符。

### surface节点

Surface Node，图形表面节点，用于独立送显的图形节点。

### SYNC_RENDER

同步渲染模式，Web组件作为图形canvas节点跟随系统送显的渲染模式。

### 上下文菜单

Context Menu，用户通过右键点击或长按触发的快捷菜单。

### 属性变更

Attribute Change，组件属性变更导致焦点转移。

### 手势冲突处理

Gesture Conflict Handling，处理ArkUI手势与ArkWeb手势的冲突。

### 手势拦截

Gesture Blocking，拦截Web组件的手势事件。

### 手势识别

Gesture Recognition，识别用户触摸屏交互产生的手势。

### 搜索栏

Search Bar，用于输入搜索关键词的UI组件。

### 时间

Time，可识别的实体类型之一，如日期时间。

### 沙箱目录

Sandbox Directory，应用沙箱中用于存储文件的目录路径。

### 深色模式

Dark Mode，降低屏幕亮度的显示模式，适合低光环境。

### 深色配色方案

Dark Color Scheme，适合低光环境的深色配色方案。

### 缩放系数

Zoom Factor，用于控制PDF文档预览时缩放比例的参数值。

### 视图层

View Layer，小程序架构中负责界面渲染的部分。

### 视觉闪烁

Visual Flickering，页面内容切换时产生的视觉闪烁现象。

### 设备方向事件

Device Orientation Event，用于监听设备方向变化的事件。

### 设备运动事件

Device Motion Event，用于监听设备运动状态变化的事件。

### 闪屏

Flash Screen，页面内容快速闪烁或切换的显示异常。

### 鼠标滚轮缩放

通过Ctrl+鼠标滚轮进行页面缩放。

## T

### tabindex

W3C标准属性，定义Web组件内元素的焦点顺序。

### Tablet

平板设备类型，User-Agent中标识平板设备的字段。

### Tags

模拟点击关键特征标签列表，用于描述检测到的具体作弊行为类型。

### terminateRenderProcess

终止渲染进程接口，用于主动关闭渲染进程。

### terminateSelf

终止自身接口，用于WebNativeMessagingExtensionAbility主动退出。

### testObjName

测试对象名，注册到前端页面的示例对象名。

### text/html

H5拖拽数据格式，HTML类型。

### text/plain

H5拖拽数据格式，文本类型。

### text/uri-list

H5拖拽数据格式，链接类型。

### TextDataDetectorConfig

智能分词配置对象，包含enablePreviewMenu和types等属性。

### TextDataDetectorType

智能分词识别类型枚举，包含电话、链接、邮箱、地址、时间等。

### TextDecoder

文本解码器，用于将字节数组解码为字符串的对象。

### TextEncoder

文本编码器，用于将字符串编码为字节数组的对象。

### TextInput

文本输入组件，用于文本输入的ArkUI组件，支持同层渲染。

### TextMenuItem

文本菜单项对象，定义菜单项名称、图标、ID等内容。

### TextMenuItemId

文本菜单项ID枚举，包含CUT、COPY、PASTE等值。

### TextRange

文本范围对象，表示选中文本的范围。

### Thread

线程，进程中的执行单元。

### TimePicker

ArkUI时间选择器组件，与Web组件结合时会抢焦。

### Touch Events

W3C触摸事件标准，描述触摸屏交互事件。

### TouchCancel

触摸事件，取消触摸时发送给Web组件。

### trackerHost

跟踪型主机，被拦截的跟踪型网站域名。

### tracking type website

跟踪型网站，用于跟踪用户行为的网站类型。

### TYPE_SENSOR

传感器类型，表示请求的权限资源类型为传感器。

### type属性

类型属性，定义了input元素的类型。

### 同层标签

Same-layer Tag，H5页面中用于同层渲染的embed或object标签。

### 同层渲染

Same-layer Render，将H5标签与ArkUI组件同步渲染的技术。

### 同层组件

Same-layer Component，与H5标签同步渲染的ArkUI组件。

### 同步方法

Sync Method，同步执行的JSBridge方法。

### 同步渲染模式

Sync Render Mode，Web组件作为图形canvas节点跟随系统送显的渲染模式。

### 拖拽功能

Drag功能，在网页中实现元素的拖放交互。

### 拖放

Drag and Drop，将元素从一个位置拖到另一个位置并放置的操作。

### 拖滑

手指未离开屏幕时的滚动行为。

### 陀螺仪

Gyroscope，用于测量设备角速度的传感器。

## U

### UA

User-Agent，用户代理字符串，包含设备类型、操作系统及版本等信息。

### UA兼容性

UA Compatibility，User-Agent与网页适配的问题。

### UA扩展

UA Extension，在默认User-Agent末尾追加自定义字段。

### UA标识检测

UA Identifier Detection，网页对User-Agent标识的检测机制。

### UI Events

W3C用户界面事件标准，描述键盘、鼠标等交互事件。

### UIAbility

用户界面能力，用于展示图形界面的应用组件。

### UIContext

UI上下文，用于保存和管理UI相关上下文信息的对象。

### UiDriver

Hypium提供的UI驱动，用于与设备上的应用界面交互。

### Uint8Array

无符号8位整数数组，用于存储字节数据的数组类型。

### UI线程

UI Thread，负责处理用户界面更新的线程。

### User-Agent

用户代理字符串，包含设备类型、操作系统等关键信息。

### user-scalable

viewport meta标签属性，设置是否允许用户缩放。

### user-select

CSS样式属性，设置文本是否可选中。

### userAgent

用户代理，标识浏览器类型和版本的字符串信息。

### UserAgent

用户代理，标识浏览器类型和版本的字符串信息。

### user前置摄像头

capture属性值，表示使用前置摄像头。

### UTF-8编码

字符编码格式，智能分词识别要求文本不超过255字节。

## V

### ValidCallback

有效回调，Native侧注册的示例生命周期回调。

### vh

视口高度单位，Viewport Height，相对于视口高度的CSS单位。

### Video

视频组件，用于播放视频的ArkUI组件，支持同层渲染。

### Video thread

视频线程，应用进程中负责视频处理的线程。

### VideoController

视频控制器，用于控制视频播放的控制器对象。

### viewport

视口，网页的可视区域。

### viewport meta标签

HTML meta标签，用于设置网页视口和缩放相关属性。

### viewport-fit

视口适配属性，meta标签属性，用于设置网页在可视窗口中的布局方式。

### ViewTree

视图树，组件挂载的目标组件树。

### virtualKeyboard

虚拟键盘，移动设备上的软键盘。

### visibility

可见性，ArkUI提供的组件通用属性，用于控制组件的显隐状态。

### visualViewport.scale

网页属性，表示当前视口的缩放比例。

## W

### Web Render Process

Web渲染进程，用于渲染Web内容的进程。

### WebAssembly

Web汇编，用于在Web上运行C/C++等低级语言编译代码的技术。

### WebBypassVsyncCondition.SCROLLBY_FROM_ZERO_OFFSET

绕过Vsync条件，从零偏移开始scrollBy。

### WebContextMenuParam

上下文菜单参数对象，包含点击位置对应HTML元素信息和位置信息。

### WebContextMenuResult

上下文菜单结果对象，提供常见的菜单能力如复制、粘贴等。

### WebCookieManager

Web Cookie管理类，用于管理Cookie信息的类。

### WebDarkMode

Web深色模式类型，定义Web组件深色模式状态的类型枚举。

### WebDriver

Selenium的Web自动化驱动接口，通过ChromeDriver与Web内核通信。

### WebDriverSetupTool

WebDriver设置工具类，用于初始化和管理ChromeDriver连接。

### WebElementType

Web元素类型枚举，包含IMAGE、LINK、TEXT等值。

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

### WebLayoutMode

Web布局模式类型，定义Web组件布局方式的类型枚举。

### WebLayoutMode.FIT_CONTENT

Web布局模式，全量展开模式。

### WebMediaPlayer

Web媒体播放器，ArkWeb内核创建的用于播放网页中媒体资源的播放器。

### WebMessage

Web消息类，用于封装消息数据的类。

### WebMessagePort

Web消息端口类，用于发送和接收消息的端口类。

### WebNativeMessagingExtensionAbility

Web原生消息扩展能力，为浏览器扩展提供后台服务能力的组件。

### WebNativeMessagingExtensionContext

Web原生消息扩展上下文，提供WebNativeMessagingExtensionAbility的上下文环境。

### WebNativeMessagingExtensionManager

Web原生消息扩展管理器，负责建立和管理NativeMessaging连接。

### WebOptions

Web选项，用于配置Web组件初始化参数的对象。

### WebPrintDocumentAdapter

Web打印文档适配器，用于渲染Web页面内容并生成PDF文件信息。

### WebResourceResponse

Web资源响应类，用于构造自定义资源响应的数据结构。

### WebResponseType

Web响应类型枚举，包含LONG_PRESS等值。

### WebRTC；Web实时通信

Web Real-Time Communications，一项实时通讯技术，允许网络应用在无需中间媒介的情况下建立浏览器之间的点对点连接，实现视频流、音频流或其他数据的传输。

### websiteHost

网站主机，触发跟踪拦截的网站域名。

### WebSQL

Web SQL数据库，前端页面使用的SQL数据库。

### WebStorage

Web存储类，用于管理DOM Storage的类。

### webTag

Web标签，用于标识Web组件的唯一标识符。

### WebviewController

Web视图控制器，用于控制Web组件行为的控制器对象。

### Web孵化进程

Web孵化进程，系统唯一的进程，负责孵化Web渲染进程与Web GPU进程。

### Web渲染进程

Web Render Process，负责运行Web渲染进程引擎和ArkWeb执行引擎的进程。

### Web组件

Web Component，用于在应用中加载和显示网页内容的组件。

### Web组件背景色

Web Component Background Color，Web组件默认显示的背景颜色。

### Web适配

使Web页面在不同设备上都能获得良好显示效果的技术方案。

### White screen

白屏，Web组件显示空白的问题，可能由多种原因导致。

### width

宽度参数，用于设置PDF页面宽度。

### window.alert

JavaScript接口，显示警告框。

### window.confirm

JavaScript接口，显示确认框。

### window.getSelection

JavaScript接口，获取当前选区。

### window.innerHeight

JavaScript属性，获取窗口内部高度。

### window.ndkProxy

窗口NDK代理，前端页面中访问Native代理对象的路径。

### window.open

窗口打开方法，JavaScript中用于打开新窗口的方法。

### window.print()

窗口打印方法，用于打印当前页面或弹出打印对话框。

### window.prompt

JavaScript接口，显示提示框。

### window对象

Window Object，浏览器中的全局窗口对象。

### write

W3C剪贴板接口，将任意类型内容写入系统剪贴板。

### writeText

W3C剪贴板接口，将文本写入系统剪贴板。

### 位置权限

Location Permission，用于获取设备位置信息的权限。

### 挖孔区

Hole Area，屏幕上摄像头或传感器开孔区域。

### 文件描述符

File Descriptor，用于传递PDF文件信息的文件标识符。

### 文本选中菜单

Text Selection Menu，用户选中文本时动态显示的上下文交互组件。

### 无痕模式

Incognito Mode，不保留浏览记录和数据的浏览模式。

### 无痕浏览模式

Incognito Mode，不保留浏览记录和数据的浏览模式。

### 物理像素

Physical Pixel，屏幕实际显示的最小像素单位。

### 纹理导出模式

Texture Export Mode，组件内容通过纹理导出进行渲染的模式。

### 网络PDF文档

Network PDF Document，通过网络URL访问的PDF文档。

### 网络托管

Network Hosting，Web组件的网络请求由应用侧托管。

### 网络权限

Network Permission，应用访问网络所需的权限声明。

### 网络超时

Network Timeout，网络请求超过规定时间未响应的状态。

### 网页内元素焦点

Web Element Focus，当前网页界面上唯一的一个可交互元素。

### 网页内容

Web Page Content，网页中显示的文本、图像等可见元素。

### 网页内容高度

Web Page Content Height，网页实际内容的高度值。

### 网页背景色

Web Page Background Color，HTML网页元素的背景颜色属性。

## X

### XComponent

X组件，用于自定义渲染的ArkUI组件，支持同层渲染。

### XMLHttpRequest

XMLHttpRequest对象，用于发送HTTP请求的JavaScript对象。

### XMLHttpRequest对象

用于发送HTTP请求的JavaScript对象。

### 性能优化

Performance Optimization，通过预启动渲染进程和预渲染Web页面提升Web组件加载速度的技术手段。

### 性能指标

网页加载过程中需要关注的重要指标，如FCP、FMP、LCP等。

### 新窗口

网页通过JavaScript或用户操作打开的额外浏览窗口。

### 显示与隐藏

组件的可见性控制，通过设置组件属性visibility的不同值，控制组件的显隐状态。

### 消息事件

Message Event，消息端口接收消息时触发的事件。

### 消息端口

Message Port，用于双向通信的消息通道。

### 消息通信

Message Communication，前端页面和应用侧之间的双向通信。

### 渲染模式

Render Mode，Web组件内容的渲染方式。

### 渲染进程

Render Process，用于渲染Web内容的专用进程。

### 渲染进程启动失败

Render Process Start Failed，渲染进程无法成功启动的状态。

### 相对定向

Relative Orientation，获取设备相对定位方向的传感器能力。

### 系统导航栏

System Navigation Bar，系统提供的底部导航栏UI区域。

### 系统非安全区域

System Unsafe Area，状态栏、挖孔区和导航栏等系统UI区域。

### 线程信息

Thread Information，线程状态、调用栈等相关信息。

## Y

### 应用侧

App Side，运行应用原生代码的一侧环境。

### 应用沙箱内PDF文档

PDF Document in Application Sandbox，存储在应用沙箱目录内的PDF文档。

### 异形屏幕

Irregular Screen，具有特殊形状的屏幕，如刘海屏、挖孔屏等。

### 异步方法

Async Method，异步执行的JSBridge方法。

### 异步渲染模式

Async Render Mode，Web组件作为图形surface节点独立送显的渲染模式。

### 用户代理

User-Agent，标识浏览器类型和版本的字符串信息。

### 运动和方向传感器

Motion and Orientation Sensor，用于监测设备运动状态和方向变化的传感器。## 其他

### 邮箱

邮箱，可识别的实体类型之一，如电子邮件地址。

### 隐私模式

Privacy Mode，不保留浏览数据的隐私浏览模式。

### 页面循环跳转

Page Loop Redirect，页面跳转逻辑陷入死循环的问题。

### 页面白屏

Page White Screen，页面加载后内容无法显示呈现白色的状态。

### 页面结束回调

网页加载完成时触发的回调。

### 页面闪烁

Page Flickering，页面加载或跳转时出现的短暂视觉闪烁现象。

### 预渲染

Pre-rendering，在后台预先渲染Web页面内容的技术。

## Z

### zoom

缩放参数，用于设置PDF文档预览时的缩放和滚动系数，使用浮点或整数值表示。

### zoomAccess

Web组件属性，控制是否可以缩放。

### zoomControlAccess

Web组件属性，设置是否允许通过组合按键进行缩放。

### zoomIn

放大接口，用于放大网页显示。

### zoomOut

缩小接口，用于缩小网页显示。

### 主动走焦

开发者或用户主观行为导致的焦点移动，如requestFocus申请焦点、按键走焦、点击申请焦点等。

### 主题模式

Theme Mode，系统提供的浅色或深色显示主题。

### 智能分词

Data Detector，自动识别页面中的电话号码、网址等信息并提供交互操作。

### 智能防跟踪

Intelligent Tracking Prevention，自动拦截跟踪型网站的功能。

### 智能防跟踪结果回调

拦截跟踪型域名时触发的回调。

### 注册对象

Register Object，注入到前端页面的应用侧对象。

### 注册方法

Register Method，注入到前端页面的应用侧方法。

### 状态栏

Status Bar，设备顶部显示系统状态的区域，点击可返回页面顶部。

### 组件树

Component Tree，UI组件的层级结构树，Web组件可动态挂载或移除。

### 组件焦点

Component Focus，当前应用界面上唯一的一个可交互组件。

### 组件移除

Component Removal，焦点所在的组件被移除时触发焦点转移。

### 自定义User-Agent

Custom User-Agent，开发者自定义的用户代理字符串。

### 自定义占位节点

用于控制Web节点挂载与移除的占位组件。

### 自定义节点

开发者通过BuilderNode创建的可自定义控制的节点。

### 自定义菜单

Custom Menu，开发者自定义触发时机与视觉呈现的菜单。

### 自定义软键盘

应用程序完全自定义的软键盘，替代系统软键盘。

### 自适应页面内容布局

Adaptive Page Content Layout，Web组件大小根据网页内容自适应的布局模式。

### 资源加载失败

Resource Load Failed，网页资源无法成功加载的状态。

### 走焦

Focus Transition，焦点在组件或元素之间转移的行为。

## 其他

### 2in1设备

2in1 Device，支持触屏和键盘输入的二合一设备类型。

### @media print

打印媒体查询，用于控制打印时的CSS样式。
