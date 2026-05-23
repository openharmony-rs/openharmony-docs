# ArkWeb术语解释

## 2

### 2in1设备

2in1 Device，支持触屏和键盘输入的二合一设备类型。

## A

### addIntelligentTrackingPreventionBypassingList

添加智能防跟踪绕过域名列表接口，用于设置绕过智能防跟踪功能的域名列表。

### allowGeolocation

允许地理位置接口，用于设置允许指定来源使用地理位置权限。

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

### ArrayBuffer

数组缓冲区，JavaScript中用于存储二进制数据的对象类型。

### asyncMethodList

异步方法列表，javaScriptProxy接口的可选参数，指定异步执行的方法。

## B

### buffer

缓冲区，用于存储二进制数据的内存区域。

### 本地离线资源

Local Offline Resource，存储在本地的离线网页资源。

## C

### CacheMode

缓存模式类型枚举，定义缓存策略的类型。

### cacheMode()

缓存模式接口，用于配置页面资源的缓存模式属性。

### Callback

回调函数，用于异步处理结果的函数类型。

### ChromeDriver

Selenium WebDriver与Web内核之间的中介驱动，将Selenium命令转换为Web内核能理解的协议。

### ChromeDriver Setup Tool；ChromeDriver设置工具

用于配置ChromeDriver路径和连接方式的工具类。

### clearAllCookiesSync

清除所有Cookie同步接口，用于清除所有内存中的Cookie。

### clearIntelligentTrackingPreventionBypassingList

清除智能防跟踪绕过域名列表接口，用于清除所有绕过域名列表。

### close

关闭接口，用于关闭消息端口释放资源。

### CMakeLists.txt

CMake配置文件，用于配置Native模块编译规则。

### configCookieSync

配置Cookie同步接口，用于设置指定URL的单个Cookie值。

### Cookie

Cookie数据，服务端生成并发送到客户端的数据。

### createWebMessagePorts

创建Web消息端口接口，用于创建消息端口实现两端通信。

### 持久化存储

Persistent Storage，数据写入本地永久保存的存储方式。

## D

### databaseAccess

数据库访问权限，设置是否允许使用Web SQL数据库。

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

### DeviceCompat

设备兼容字段，前向兼容字段，标识设备类型。

### DeviceType

设备类型字段，标识当前设备类型如手机、平板、PC。

### DOM Storage

DOM存储，包含Session Storage和Local Storage两类存储机制。

### Driver Setup Tool

驱动程序设置工具，用于配置ChromeDriver路径和连接方式。

## E

### enableIntelligentTrackingPrevention

启用智能防跟踪接口，用于开启或关闭智能防跟踪功能。

### ESObject

ES对象类型，用于接收前端页面传递的对象类型参数。

### existCookie

存在Cookie接口，用于查询是否存在Cookie数据。

## F

### fetchCookieSync

获取Cookie同步接口，用于获取指定URL对应的Cookie值。

### fileAccess()

文件访问接口，用于设置是否允许Web组件访问本地文件。

### Function

函数类型，用于传递回调函数的参数类型。

## G

### getAccessibleGeolocation

获取可访问地理位置接口，用于异步获取指定源的地理位置权限状态。

### getCustomUserAgent()

获取自定义用户代理接口，用于获取自定义的UserAgent字符串。

### getDefaultUserAgent

获取默认用户代理接口，用于获取系统默认的User-Agent字符串。

### getUserAgent()

获取用户代理接口，用于获取Web组件当前的UserAgent字符串。

### 跟踪型网站

Tracking Website，用于跟踪用户行为的第三方网站。

## H

### h5Port

H5端口，前端页面保存的消息端口对象。

### host

主机字段，URL中的域名部分。

### Hypium

HarmonyOS UI自动化测试框架，支持与Selenium集成进行Web应用测试。

### 混合内容策略

MixedContent Policy，控制HTTP和HTTPS混合内容的机制。

### 缓存模式

Cache Mode，Web组件加载资源的缓存策略。

## I

### incognitoMode

隐私模式参数，用于创建隐私模式的Web组件。

### initializeWebEngine

初始化Web引擎接口，用于初始化ArkWeb内核。

### isIncognitoMode()

是否隐私模式接口，用于判断当前Web组件是否是隐私模式。

### isIntelligentTrackingPreventionEnabled()

是否启用智能防跟踪接口，用于判断是否开启智能防跟踪功能。

## J

### javaScriptAccess()

JavaScript访问接口，用于设置是否允许执行JavaScript脚本。

### javaScriptOnDocumentStart

JavaScript文档开始接口，用于在文档加载开始时注入脚本。

### javaScriptProxy()

JavaScript代理接口，用于将对象注入到Web端。

### JavaScript运行时

JavaScript Runtime，执行JavaScript代码的环境。

### JSBridge

JavaScript桥接，应用与Web页面之间进行JavaScript交互的机制。

### JSBridgeObject

JSBridge对象，Native侧实现JSBridge通信的业务类。

### JSON.stringify

JSON序列化方法，用于将对象转换为JSON字符串。

### 静态资源文件缓存

Static Resource File Cache，应用静态资源的缓存存储。

## K

### Key-Value

键值对，数据存储的基本格式。

### 扩展区

Extension Area，三方应用可以扩展的User-Agent字段区域。

### 跨域访问

Cross-origin Access，从一个源访问另一个源资源的行为。

## L

### libentry.so

Native模块库文件，编译生成的动态共享库。

### libohweb.so

ArkWeb Native库，提供Native接口的动态库。

### loadUrl()

加载URL接口，用于加载指定的网页地址。

### Local Storage

本地存储，保存在应用目录下的持久化数据。

### 拦截请求

Intercept Request，拦截Web资源请求并自定义响应的操作。

### 逻辑层

Logic Layer，小程序架构中负责业务逻辑处理的部分。

## M

### methodList

方法列表，javaScriptProxy接口的参数，指定要注册的方法。

### methodNameListForJsProxy

JS代理方法名称列表，用于标识对象中可被前端调用的方法。

### mimeType

MIME类型，标识文件内容类型的字符串。

### mimeTypeMap

MIME类型映射表，构造本地文件和MIME类型的映射表。

### Mobile

移动设备标识，User-Agent中表示移动设备的字段。

## N

### Native

原生，指直接访问应用沙箱的方式。

### Native JSBridge

Native JSBridge，使用Native接口实现JSBridge通信的方案。

### Native侧

Native Side，运行C++代码的一侧环境。

### Native侧初始化

Native Side Init，Native侧的初始化过程。

### Native侧注册

Native Side Register，在Native侧注册对象和回调。

### navigator.userAgent

导航器用户代理，浏览器提供的User-Agent字符串属性。

### ndkProxy

NDK代理对象，Native侧注册到前端页面的代理对象名。

### Node-API

Node API，用于ArkTS与C++交互的接口。

### None

无缓存模式，加载资源不使用缓存。

## O

### OH_ArkWeb_GetNativeAPI

获取ArkWeb Native API函数，用于获取Native侧API结构体。

### onControllerAttached()

控制器绑定回调，WebviewController与组件绑定时触发的回调。

### onInterceptRequest()

拦截请求回调，用于拦截Web资源请求并自定义响应。

### Online

在线缓存模式，加载资源不使用缓存全部从网络获取。

### Only

仅缓存模式，只从缓存中加载资源。

### onmessage

消息接收事件，消息端口接收到消息时触发的事件。

### onMessageEvent

消息事件回调，消息端口接收消息时触发的回调。

### OpenHarmony

开源鸿蒙，User-Agent中标识OpenHarmony系统的字段。

### OSName

操作系统名称，User-Agent中的基础操作系统名称字段。

### OSVersion

操作系统版本，User-Agent中的操作系统版本字段。

## P

### permission

权限参数，javaScriptProxy接口的可选参数，用于权限控制。

### port

端口，消息通信中用于发送和接收消息的通道。

### postMessage()

发送消息接口，用于向消息端口发送消息。

### postMessageEvent

发送消息事件接口，用于向消息端口发送消息事件。

### postWebMessage

发送Web消息接口，用于向HTML侧发送消息端口。

### privacy mode

隐私模式，不写入本地持久化存储的浏览模式。

### Promise

Promise对象，用于异步操作的承诺对象类型。

## Q

### 前端页面

Frontend Page，运行在Web组件中的H5页面。

## R

### rawfile

原始文件目录，应用资源目录下的原始文件存储位置。

### refresh()

刷新接口，用于重新加载当前页面。

### registerAsyncJavaScriptProxyEx

注册异步JavaScript代理扩展接口，支持异步方法返回值。

### registerJavaScriptProxy()

注册JavaScript代理接口，用于将对象注入到window对象中。

### registerJavaScriptProxyEx

注册JavaScript代理扩展接口，支持返回值的代理注册。

### removeCache()

清除缓存接口，用于清除已经缓存的资源。

### removeIntelligentTrackingPreventionBypassingList

移除智能防跟踪绕过域名列表接口，用于删除部分绕过域名。

### ROM

只读存储器，设备上预装的系统固件。

### runJavaScript()

执行JavaScript接口，用于调用前端页面的JavaScript函数。

### runJavaScriptExt()

执行JavaScript扩展接口，支持ArrayBuffer参数类型。

### 绕过域名列表

Bypass Domain List，绕过智能防跟踪功能的域名列表。

## S

### SameSite

同站属性，Cookie的安全属性用于控制跨站请求。

### saveCookieAsync

保存Cookie异步接口，用于强制将Cookie保存到磁盘。

### Scheme Handler

Scheme处理器，用于拦截和处理Web组件发起的特定协议网络请求。

### schemeMap

协议映射表，构造域名和本地文件的映射表。

### SDK

软件开发工具包，提供开发接口的软件包。

### Selenium

Web应用自动化测试框架，模拟用户在浏览器中的操作。

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

### setCustomUserAgent()

设置自定义用户代理接口，用于设置Web组件的UserAgent字符串。

### setLazyInitializeWebEngine()

设置懒加载Web引擎接口，用于跳过初始化ArkWeb内核。

### setMessageEventHandler()

设置消息事件处理接口，用于注册消息端口接收回调。

### setPathAllowingUniversalAccess()

设置路径允许通用访问接口，用于设置允许跨域访问的本地路径列表。

### setUserAgentForHosts()

设置特定网站用户代理接口，用于对特定网站设置自定义User-Agent。

### setWebDebuggingAccess()

设置Web调试访问接口，用于开启Web调试模式。

### Static Web Page

静态网页，内容固定不变的网页类型。

### 视图层

View Layer，小程序架构中负责界面渲染的部分。

## T

### Tablet

平板设备类型，User-Agent中标识平板设备的字段。

### testObjName

测试对象名，注册到前端页面的示例对象名。

### TextDecoder

文本解码器，用于将字节数组解码为字符串的对象。

### TextEncoder

文本编码器，用于将字符串编码为字节数组的对象。

### trackerHost

跟踪型主机，被拦截的跟踪型网站域名。

### tracking type website

跟踪型网站，用于跟踪用户行为的网站类型。

### 同步方法

Sync Method，同步执行的JSBridge方法。

## U

### UA

User-Agent，用户代理字符串，包含设备类型、操作系统及版本等信息。

### UA兼容性

UA Compatibility，User-Agent与网页适配的问题。

### UA扩展

UA Extension，在默认User-Agent末尾追加自定义字段。

### UA标识检测

UA Identifier Detection，网页对User-Agent标识的检测机制。

### UiDriver

Hypium提供的UI驱动，用于与设备上的应用界面交互。

### Uint8Array

无符号8位整数数组，用于存储字节数据的数组类型。

### UI线程

UI Thread，负责处理用户界面更新的线程。

### User-Agent

用户代理字符串，包含设备类型、操作系统等关键信息。

### userAgent

用户代理，标识浏览器类型和版本的字符串信息。

## V

### ValidCallback

有效回调，Native侧注册的示例生命周期回调。

### viewport

视口，网页的可视区域。

## W

### WebCookieManager

Web Cookie管理类，用于管理Cookie信息的类。

### WebDriver

Selenium的Web自动化驱动接口，通过ChromeDriver与Web内核通信。

### WebDriverSetupTool

WebDriver设置工具类，用于初始化和管理ChromeDriver连接。

### WebMessage

Web消息类，用于封装消息数据的类。

### WebMessagePort

Web消息端口类，用于发送和接收消息的端口类。

### websiteHost

网站主机，触发跟踪拦截的网站域名。

### WebSQL

Web SQL数据库，前端页面使用的SQL数据库。

### WebStorage

Web存储类，用于管理DOM Storage的类。

### webTag

Web标签，用于标识Web组件的唯一标识符。

### window.ndkProxy

窗口NDK代理，前端页面中访问Native代理对象的路径。

### window对象

Window Object，浏览器中的全局窗口对象。

### 无痕模式

Incognito Mode，不保留浏览记录和数据的浏览模式。

### 网络权限

Network Permission，应用访问网络所需的权限声明。

## X

### XMLHttpRequest

XMLHttpRequest对象，用于发送HTTP请求的JavaScript对象。

### 消息事件

Message Event，消息端口接收消息时触发的事件。

### 消息端口

Message Port，用于双向通信的消息通道。

### 消息通信

Message Communication，前端页面和应用侧之间的双向通信。

## Y

### 应用侧

App Side，运行应用原生代码的一侧环境。

### 异步方法

Async Method，异步执行的JSBridge方法。

### 隐私模式

Privacy Mode，不保留浏览数据的隐私浏览模式。

### 页面循环跳转

Page Loop Redirect，页面跳转逻辑陷入死循环的问题。

### 页面结束回调

网页加载完成时触发的回调。

## Z

### 智能防跟踪

Intelligent Tracking Prevention，自动拦截跟踪型网站的功能。

### 智能防跟踪结果回调

拦截跟踪型域名时触发的回调。

### 注册对象

Register Object，注入到前端页面的应用侧对象。

### 注册方法

Register Method，注入到前端页面的应用侧方法。

### 自定义User-Agent

Custom User-Agent，开发者自定义的用户代理字符串。
