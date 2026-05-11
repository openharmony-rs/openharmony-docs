# Enums
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

> **说明：**
>
> 本模块首批接口从API version 9开始支持，后续版本的新增接口，则采用上角标单独标记接口的起始版本。

## WebHitTestType

[getLastHitTest](./arkts-apis-webview-WebviewController.md#getlasthittest18)接口用于指示光标节点。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称          | 值 | 说明                                      |
| ------------- | -- |----------------------------------------- |
| EditText      | 0 |可编辑的区域。                            |
| Email         | 1 |电子邮件地址。                            |
| HttpAnchor    | 2 |超链接，其中src为http。                     |
| HttpAnchorImg | 3 |带有超链接的图片，其中src为http + HTML::img。 |
| Img           | 4 |HTML::img标签。                           |
| Map           | 5 |地理地址。                                |
| Phone         | 6 |电话号码。                                |
| Unknown       | 7 |未知内容。                                |

## SecureDnsMode<sup>10+</sup>

Web组件使用HTTPDNS的模式。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称          | 值 | 说明                                      |
| ------------- | -- |----------------------------------------- |
| OFF                                  | 0 |不使用HTTPDNS， 可以用于撤销之前使用的HTTPDNS配置。|
| AUTO                                 | 1 |自动模式，用于解析的设定DNS服务器不可用时，可自动回落至系统DNS。|
| SECURE_ONLY                          | 2 |强制使用设定的HTTPDNS服务器进行域名解析。|

## SecurityLevel<sup>11+</sup>

当前网页的安全级别。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称          | 值 | 说明                                      |
| ------------- | -- |----------------------------------------- |
| NONE          | 0 |页面既不绝对安全，也不是不安全，即是中立。例如，部分scheme非http/https的URL。|
| SECURE        | 1 |页面安全，页面使用的是HTTPS协议，且使用了信任的证书。|
| WARNING       | 2 |页面不安全。例如，使用HTTP协议或使用HTTPS协议但使用旧版TLS版本。|
| DANGEROUS     | 3 |页面不安全。尝试HTTPS并失败、页面未通过身份验证、页面上包含不安全活动内容的HTTPS、恶意软件、网络钓鱼或任何其他可能危险的严重安全问题。 |

## MediaPlaybackState<sup>12+</sup>

当前网页的播控状态。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称    | 值   | 说明               |
| ------- | ---- | ------------------ |
| NONE    | 0    | 页面无音视频启播。 |
| PLAYING | 1    | 页面音视频播放中。 |
| PAUSED  | 2    | 页面音视频暂停。   |
| STOPPED | 3    | 页面音视频停止。   |

## PressureLevel<sup>14+</sup>

内存压力等级。在应用主动清理Web组件占用的缓存时，Web内核会根据内存压力等级，进行缓存释放。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
| ------------------------------- | - | ---------- |
| MEMORY_PRESSURE_LEVEL_MODERATE | 1 | 中等内存压力等级。这个等级下，Web内核会尝试释放重新分配开销较小且不需要立即使用的缓存。 |
| MEMORY_PRESSURE_LEVEL_CRITICAL | 2 | 严重内存压力等级。这个等级下，Web内核会尝试释放所有可能的内存缓存。 |

## WebMessageType<sup>10+</sup>

[WebMessagePort](./arkts-apis-webview-WebMessagePort.md)接口所支持的数据类型。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称         | 值 | 说明                            |
| ------------ | -- |------------------------------- |
| NOT_SUPPORT  | 0 |不支持的数据类型。|
| STRING       | 1 |字符串类型。|
| NUMBER       | 2 |数值类型。|
| BOOLEAN      | 3 |布尔类型。|
| ARRAY_BUFFER | 4 |原始二进制数据缓冲区。|
| ARRAY        | 5 |数组类型。|
| ERROR        | 6 |错误类型。|

## JsMessageType<sup>10+</sup>

[runJavaScriptExt](./arkts-apis-webview-WebviewController.md#runjavascriptext10)接口脚本执行后返回的结果的类型。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称         | 值 | 说明                              |
| ------------ | -- |--------------------------------- |
| NOT_SUPPORT  | 0 |不支持的数据类型。|
| STRING       | 1 |字符串类型。|
| NUMBER       | 2 |数值类型。|
| BOOLEAN      | 3 |布尔类型。|
| ARRAY_BUFFER | 4 |原始二进制数据缓冲区。|
| ARRAY        | 5 |数组类型。|

## RenderProcessMode<sup>12+</sup>

ArkWeb渲染子进程模式类型。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称          | 值 | 说明                                      |
| ------------- | -- |----------------------------------------- |
| SINGLE        | 0 |ArkWeb单渲染子进程模式。该模式下，多个Web复用一个渲染子进程。|
| MULTIPLE      | 1 |ArkWeb多渲染子进程模式。该模式下，每个Web一个渲染子进程。|

## OfflineResourceType<sup>12+</sup>

[OfflineResourceMap](./arkts-apis-webview-i.md#offlineresourcemap12)对象对应的本地离线资源的接口类型。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称         | 值 | 说明                              |
| ------------ | -- |--------------------------------- |
| IMAGE  | 0 | 图片类型的资源。 |
| CSS       | 1 | CSS类型的资源。|
| CLASSIC_JS       | 2 | 通过<script src="" /\>标签加载的JavaScript资源。|
| MODULE_JS      | 3 |通过<script src="" type="module" /\>标签加载的JavaScript资源。|

## ScrollType<sup>12+</sup>

Scroll滚动类型，用于[setScrollable](./arkts-apis-webview-WebviewController.md#setscrollable12)。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称         | 值 | 说明                              |
| ------------ | -- |--------------------------------- |
| EVENT  | 0 | 滚动事件，表示通过触摸屏、触摸板、鼠标滚轮生成的网页滚动。|

## WebDownloadState<sup>11+</sup>

下载任务的状态。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称          | 值 | 说明                                      |
| ------------- | -- |----------------------------------------- |
| IN_PROGRESS                                  | 0 |下载任务正在进行中。|
| COMPLETED                                 | 1 |下载任务已经完成。|
| CANCELED                          | 2 |下载任务已经被取消。|
| INTERRUPTED                          | 3 |下载任务被中断。|
| PENDING                          | 4 |下载任务等待开始。|
| PAUSED                          | 5 |下载任务已经被暂停。|
| UNKNOWN                          | 6 |下载任务未知状态。|

## WebDownloadErrorCode<sup>11+</sup>

下载任务的错误码。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称          | 值 | 说明                                      |
| ------------- | -- |----------------------------------------- |
| ERROR_UNKNOWN                                  | 0 |未知错误。可能原因：系统内部异常或未知错误。解决方法：建议查看系统日志获取更多信息，或联系技术支持。|
| FILE_FAILED | 1 |  常规文件操作失败。可能原因：文件系统错误、权限不足或磁盘损坏。解决方法：检查文件路径和权限，确保磁盘空间充足。|
| FILE_ACCESS_DENIED | 2 | 没有权限访问文件。可能原因：应用缺少文件访问权限或文件被其他进程占用。解决方法：请检查应用权限配置，确保已申请必要的文件访问权限。|
| FILE_NO_SPACE | 3 | 磁盘没有足够的空间。可能原因：磁盘空间不足或分区已满。解决方法：清理不必要的文件，释放磁盘空间。|
| FILE_NAME_TOO_LONG | 5 | 文件名过长。可能原因：文件名超过系统最大长度限制。解决方法：请缩短文件名或更改文件路径。|
| FILE_TOO_LARGE | 6 | 文件太大。可能原因：文件大小超过系统或应用的限制。解决方法：请检查文件大小，考虑分片处理或选择其他方式传输。|
| FILE_TRANSIENT_ERROR | 10 |  出现了一些临时问题，例如内存不足、文件正在使用以及同时打开的文件过多。可能原因：系统资源不足或文件被占用。解决方法：释放系统资源，关闭不必要的文件，稍后重试。|
| FILE_BLOCKED | 11 |  由于某些本地策略，文件被阻止访问。可能原因：安全策略或权限限制阻止了文件访问。解决方法：请检查本地安全策略和权限配置，确保允许访问该文件。|
+| FILE_TOO_SHORT | 13 |  当尝试恢复下载时，发现文件长度不足，可能文件已不存在。可能原因：下载文件已损坏或被删除。解决方法：请重新开始下载任务。|
+| FILE_HASH_MISMATCH | 14 |  哈希值不匹配。可能原因：文件在传输过程中被篡改或下载不完整。解决方法：请重新下载文件，确保网络连接稳定。|
| FILE_SAME_AS_SOURCE | 15 |  文件已存在。可能原因：目标位置已存在同名文件。解决方法：请更改文件名或选择覆盖选项。|
| NETWORK_FAILED | 20 |  一般网络错误。可能原因：网络连接异常或服务器无响应。解决方法：请检查网络连接状态，稍后重试。|
| NETWORK_TIMEOUT | 21 | 网络超时。可能原因：网络响应时间过长或网络不稳定。解决方法：请检查网络连接，或增加超时时间设置。|
+| NETWORK_DISCONNECTED | 22 | 网络连接断开。可能原因：网络连接中断或设备断网。解决方法：请检查网络连接，确保网络正常后重试。|
| NETWORK_SERVER_DOWN | 23 |  服务器关闭。可能原因：目标服务器暂时不可用或维护中。解决方法：请稍后重试或联系服务提供商。|
+| NETWORK_INVALID_REQUEST | 24 |  无效的网络请求，可能重定向到不支持的协议或无效的URL。可能原因：URL格式错误或不支持的协议。解决方法：请检查URL格式和协议，确保请求参数正确。|
+| SERVER_FAILED | 30 | 服务器返回一般性错误。可能原因：服务器内部错误或服务异常。解决方法：请稍后重试或联系服务器管理员。|
| SERVER_NO_RANGE | 31 |  服务器不支持范围请求。可能原因：服务器不支持断点续传功能。解决方法：请尝试完整下载文件。|
| SERVER_BAD_CONTENT | 33 |   服务器没有请求的数据。可能原因：请求的资源已被删除或不存在。解决方法：请检查请求URL，确保资源存在。|
| SERVER_UNAUTHORIZED | 34 |  服务器不允许下载该文件。可能原因：缺少认证信息或权限不足。解决方法：请检查认证信息，确保有足够的权限。|
| SERVER_CERT_PROBLEM | 35 |  服务器证书错误。可能原因：SSL证书过期或无效。解决方法：请检查服务器证书配置，确保证书有效。|
| SERVER_FORBIDDEN | 36 |  服务器访问被禁止。可能原因：访问权限不足或IP被限制。解决方法：请联系管理员获取访问权限。|
| SERVER_UNREACHABLE | 37 |  无法访问服务器。可能原因：服务器地址错误或网络不可达。解决方法：请检查服务器地址和网络连接。|
| SERVER_CONTENT_LENGTH_MISMATCH | 38 |  接收到的数据与内容长度不匹配。可能原因：数据传输不完整或被截断。解决方法：请重新下载文件。|
| SERVER_CROSS_ORIGIN_REDIRECT | 39 | 发生意外的跨站重定向。可能原因：服务器配置了不安全的重定向策略。解决方法：请检查服务器配置，确保重定向安全。|
| USER_CANCELED | 40 | 用户取消了下载。|
| USER_SHUTDOWN | 41 | 用户关闭了应用。|
+| CRASH | 50 | 应用发生崩溃。可能原因：应用内部错误或系统异常导致进程崩溃。解决方法：请查看崩溃日志，修复问题后重试。|

## WebResourceType<sup>12+</sup>

资源请求的资源类型。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称         | 值 | 说明                              |
| ------------ | -- |--------------------------------- |
| MAIN_FRAME | 0 | 顶层页面。 |
| SUB_FRAME | 1 | Frame或Iframe。 |
| STYLE_SHEET | 2 | CSS样式表。 |
| SCRIPT | 3 | 外部脚本。 |
| IMAGE | 4 | 图片（jpg/gif/png/以及其他）。 |
| FONT_RESOURCE | 5 | 字体。 |
| SUB_RESOURCE | 6 | 其他子资源。如果实际类型未知，则是默认类型。 |
| OBJECT | 7 | 插件的Object（或embed）标签，或者插件请求的资源。 |
| MEDIA | 8 | 媒体资源。 |
| WORKER | 9 | 专用工作线程的主资源。 |
| SHARED_WORKER | 10 | 共享工作线程的主资源。 |
| PREFETCH | 11 | 明确的预取请求。 |
| FAVICON | 12 | 网站图标。 |
| XHR | 13 | XMLHttpRequest。 |
| PING | 14 | <a ping\>/sendBeacon的Ping请求。 |
| SERVICE_WORKER | 15 | service worker的主资源。 |
| CSP_REPORT | 16 | 内容安全策略违规报告。 |
| PLUGIN_RESOURCE | 17 | 插件请求的资源。 |
| NAVIGATION_PRELOAD_MAIN_FRAME | 19 | 触发service worker预热的主frame跳转请求。 |
| NAVIGATION_PRELOAD_SUB_FRAME | 20 | 触发service worker预热的子frame跳转请求。 |

## PlaybackStatus<sup>12+</sup>

[handleStatusChanged](./arkts-apis-webview-NativeMediaPlayerHandler.md#handlestatuschanged12) 接口参数， 用于表示播放器的播放状态。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
|------|----|------|
| PAUSED  | 0 | 播放状态为暂停状态，表示媒体已暂停。 |
| PLAYING | 1 | 播放状态为播放状态，表示媒体正在播放。 |

## NetworkState<sup>12+</sup>

播放器的网络状态。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
|------|----|------|
| EMPTY         | 0 | 播放器还没有开始下载数据。 |
| IDLE          | 1 | 播放器网络状态空闲，比如媒体分片下载完成，下一个分片还没有开始下载。 |
| LOADING       | 2 | 播放器正在下载媒体数据。 |
| NETWORK_ERROR | 3 | 发生了网络错误。 |

## ReadyState<sup>12+</sup>

播放器的缓存状态。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
|------|----|------|
| HAVE_NOTHING      | 0 | 没有缓存。 |
| HAVE_METADATA     | 1 | 只缓存了媒体元数据。 |
| HAVE_CURRENT_DATA | 2 | 只缓存到当前的播放进度。 |
| HAVE_FUTURE_DATA  | 3 | 缓存时长超过了当前的播放进度, 但是仍有可能导致卡顿。 |
| HAVE_ENOUGH_DATA  | 4 | 缓存了足够的数据，保证播放流畅。 |

## MediaError<sup>12+</sup>

播放器的错误类型。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
|------|----|------|
| NETWORK_ERROR | 1 | 网络错误。 |
| FORMAT_ERROR  | 2 | 媒体格式错误。 |
| DECODE_ERROR  | 3 | 解码错误。 |

## SuspendType<sup>12+</sup>

表示播放器的挂起类型。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
|------|----|------|
| ENTER_BACK_FORWARD_CACHE | 0 | 页面进入BFCache。 |
| ENTER_BACKGROUND         | 1 | 页面进入后台。 |
| AUTO_CLEANUP             | 2 | 系统自动清理。 |

## MediaType<sup>12+</sup>

表示媒体类型。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
|------|----|------|
| VIDEO | 0 | 视频。 |
| AUDIO | 1 | 音频。 |

## SourceType<sup>12+</sup>

表示媒体源的类型。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
|------|----|------|
| URL | 0 | 媒体源的类型是URL。 |
| MSE | 1 | 媒体源的类型是blob。 |

## Preload<sup>12+</sup>

播放器预加载媒体数据。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
|------|----|------|
| NONE     | 0 | 不预加载。 |
| METADATA | 1 | 只预加载媒体的元数据。 |
| AUTO     | 2 | 预加载足够多的媒体数据，以保证能流畅地播放。 |

## ProxySchemeFilter<sup>15+</sup>

使用代理的请求的scheme信息。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称          | 值 | 说明                                      |
| ------------- | -- |----------------------------------------- |
| MATCH_ALL_SCHEMES | 0 |所有的scheme都会使用代理。|
| MATCH_HTTP        | 1 |HTTP请求会使用代理。|
| MATCH_HTTPS       | 2 |HTTPS请求会使用代理。|

## WebDestroyMode<sup>20+</sup>

Web组件的销毁模式，当Web组件销毁时，销毁模式会影响Web内核的资源释放时机，例如JavaScript运行上下文、渲染上下文等等。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
| ------------------------------- | - | ---------- |
| NORMAL_MODE | 0 | 普通模式，由系统决定Web组件资源的销毁时机。 |
| FAST_MODE   | 1 | 快速模式，当Web组件触发销毁时，立即销毁相关的内部资源。 |

## ScrollbarMode<sup>23+</sup>

Web页面场景下，全局滚动条模式。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
| ------------------------------- | - | ---------- |
| OVERLAY_LAYOUT_SCROLLBAR  | 0 | 非常驻滚动条，可以拖拽。 |
| FORCE_DISPLAY_SCROLLBAR    | 1 | 常驻滚动条。 |
| OVERLAY_VISUAL_SCROLLBAR    | 2 | 非常驻滚动条，不可以拖拽。<br/>**起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |

## WebBlanklessErrorCode<sup>20+</sup>

无白屏加载的异常错误码。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
| ------------------------------- | - | ---------- |
| SUCCESS | 0 | 成功。 |
| ERR_UNKNOWN   | -1 | 未知错误，内部状态错误等。可能原因：系统内部异常。解决方法：建议查看系统日志获取更多信息，或联系技术支持。|
| ERR_INVALID_PARAM   | -2 | 参数不合法。可能原因：参数类型、范围或格式不正确。解决方法：请检查接口参数，确保参数符合要求。|
| ERR_CONTROLLER_NOT_INITED   | -3 | WebViewController未绑定组件。可能原因：Web组件未正确初始化或绑定。解决方法：请确保在调用接口前，WebViewController已正确绑定到Web组件。|
| ERR_KEY_NOT_MATCH   | -4 | 未匹配到key值，对于[setBlanklessLoadingWithKey](./arkts-apis-webview-WebviewController.md#setblanklessloadingwithkey20)需与[getBlanklessInfoWithKey](./arkts-apis-webview-WebviewController.md#getblanklessinfowithkey20)配套使用并且key值一致，否则返回该错误码。 |
| ERR_SIGNIFICANT_CHANGE   | -5 | 当相似度较低时，系统会判定为跳变太大，[setBlanklessLoadingWithKey](./arkts-apis-webview-WebviewController.md#setblanklessloadingwithkey20)接口不会成功启用插帧。 |
| ERR_DURATION_OUT_OF_RANGE<sup>23+</sup>   | -6 | 在[BlanklessLoadingParam](./arkts-apis-webview-i.md#blanklessloadingparam23)设置的插帧持续时间超出范围。<br>**模型约束：** 此接口仅可在Stage模型下使用。 |
| ERR_EXPIRATION_TIME_OUT_OF_RANGE<sup>23+</sup>   | -7 | 在[BlanklessLoadingParam](./arkts-apis-webview-i.md#blanklessloadingparam23)设置的历史帧失效时间超出范围。<br>**模型约束：** 此接口仅可在Stage模型下使用。 |

## BlanklessFrameInterpolationState <sup>23+</sup>

白屏插帧状态，表示无白屏加载插帧功能的状态。插帧是指在页面加载时，通过在两个实际帧之间插入计算生成的过渡帧，减少用户感知的白屏等待时间，提升视觉体验。

**系统能力：** SystemCapability.Web.Webview.Core

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 值 | 说明 |
| ------------------------------- | - | ---------- |
| FRAME_INTERPOLATION_SUCCEEDED | 0 | 插帧成功。 |
| FRAME_INTERPOLATION_FAILED   | 1 | 插帧失败。 |
| FRAME_INTERPOLATION_REMOVED   | 2 | 插帧移除。 |

## ArkWebEngineVersion<sup>20+</sup>

ArkWeb内核版本，请参考[M114内核在OpenHarmony 6.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_6.0.md)，[M132内核在OpenHarmony 7.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_7.0.md)。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称          | 值 | 说明                                      |
| ------------- | -- |----------------------------------------- |
| SYSTEM_DEFAULT   | 0     | 系统默认内核，OpenHarmony 6.0版本默认为M132，OpenHarmony 7.0版本默认为M144。|
| M114             | 1     | OpenHarmony 6.0版本的遗留内核。开发者可选择此遗留内核，若系统版本上不存在此内核则设置无效。|
| M132             | 2     | OpenHarmony 6.0版本的常青内核（OpenHarmony 7.0版本的遗留内核），M132为OpenHarmony 6.0版本的默认内核。若系统版本上不存在此内核则设置无效。|
| M144             | 3     | OpenHarmony 7.0版本的常青内核，M144为OpenHarmony 7.0版本的默认内核。若系统版本上不存在此内核则设置无效。<br/>**起始版本：** 26.0.0 |
| ARKWEB_EVERGREEN<sup>23+</sup> | 99999 | 常青内核，系统的最新内核。开发者可选择在每个系统版本上都使用最新的内核，OpenHarmony开发套件（基于API 23）及之后所有系统版本都生效。 |

**表1** 常青内核与遗留内核含义说明

| 内核类型 | 英文 | 说明 |
| ----------- | -------- | -------- |
| 常青内核     | EVERGREEN WebCore | 当前系统的最新Web内核，系统基于此内核进行完整的功能实现，推荐应用使用。|
| 遗留内核     | LEGACY WebCore    | 复用上一版本的内核，只做安全补丁及舆情问题修复，仅作为兼容性回滚使用，且遗留内核的支持有时间限制。 |


## SiteIsolationMode<sup>21+</sup>

站点隔离机制将不同源的网站隔离在不同的渲染进程中，减少跨域攻击面。例如，PC上原有进程模型是每一个Tab对应一个Render进程，站点隔离打开后，让不同源的Iframe运行在独立的Render进程中。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
| ------------------------------- | - | ---------- |
| PARTIAL | 0 | 部分站点隔离，即在同一个Render进程内加载新站点。 |
| STRICT  | 1 | 严格站点隔离，跨站点的Iframe将切换到新的渲染进程。 |


## WebSoftKeyboardBehaviorMode<sup>22+</sup>

Web软键盘自动控制模式。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
| ------------------------------- | - | ---------- |
| DEFAULT | 0 | 当Web组件失去焦点或获得焦点、状态切换为inactive或active时，系统均会尝试触发软键盘自动隐藏或拉起（默认值）。 |
| DISABLE_AUTO_KEYBOARD_ON_ACTIVE | 1 | Web组件在inactive或active状态切换时，系统不再尝试触发软键盘自动隐藏或拉起。 |

## WebHttpCookieSameSitePolicy<sup>23+</sup>

控制cookie在跨站请求中的发送行为。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称 | 值 | 说明 |
| ---- | -- |----------------------------------------- |
| NONE | 0 | 允许在跨站请求中携带cookie，但必须同时设置secure属性。 |
| LAX | 1 | 允许特定的跨站请求携带cookie，如某些get请求的导航场景。 |
| STRICT | 2 | 禁止在跨站请求中携带cookie。 |

## UserAgentFormFactor<sup>24+</sup>

用户设备形态。

**系统能力：** SystemCapability.Web.Webview.Core

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称         | 值 | 说明                              |
| ------------ | -- |--------------------------------- |
| AUTOMOTIVE  | 'Automotive' |车机，字符串类型。|
| DESKTOP       | 'Desktop' |PC，字符串类型。|
| MOBILE       | 'Mobile' |手机，字符串类型。|
| EINK      | 'EInk' |墨水屏，字符串类型。|
| TABLET | 'Tablet' |平板，字符串类型。|
| WATCH        | 'Watch' |手表，字符串类型。|
| XR        | 'XR' |VR+AR设备，字符串类型。|