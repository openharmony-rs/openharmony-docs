# Enums

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件首批接口从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Class首批接口从API version 8开始支持。

## MessageLevel

ConsoleMessage的信息级别。

> **说明：**
>
> - 在html5侧，调用console.log或console.info对应ConsoleMessage的信息级别在ArkTS-Dyn中均为MessageLevel.Info，在ArkTS-Sta中均为MessageLevel.INFO。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22

| 名称    | 值 | 说明    |
| ----- | -- | ---- |
| ArkTS-Dyn: Debug <br>ArkTS-Sta: DEBUG| 0 | 调试级别。 |
| ArkTS-Dyn: Error <br>ArkTS-Sta: ERROR| 1 | 错误级别。 |
| ArkTS-Dyn: Info  <br>ArkTS-Sta: INFO| 2 | 消息级别。 |
| ArkTS-Dyn: Log  <br>ArkTS-Sta: LOG| 3 | 日志级别。 |
| ArkTS-Dyn: Warn <br>ArkTS-Sta: WARN| 4 | 警告级别。 |

## MixedMode

混合内容模式。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 22


| 名称        | 值 | 说明                                 |
| ---------- | -- | ---------------------------------- |
| ArkTS-Dyn: All <br>ArkTS-Sta: ALL| 0 | 宽松模式：允许加载HTTP和HTTPS混合内容。所有不安全的内容都可以被加载。 |
| ArkTS-Dyn: Compatible <br>ArkTS-Sta: COMPATIBLE| 1 | 兼容模式：混合内容兼容性模式，部分不安全的内容可能被加载。           |
| ArkTS-Dyn: None  <br>ArkTS-Sta: NONE| 2 | 严格模式：不允许加载HTTP和HTTPS混合内容。               |

## HitTestType

 **系统能力：** SystemCapability.Web.Webview.Core

| 名称            | 值 | 说明                       |
| ------------- | -- | ------------------------ |
| EditText      | 0 | 可编辑的区域。                  |
| Email         | 1 | 电子邮件地址。                  |
| HttpAnchor    | 2 | 超链接，其src为http。           |
| HttpAnchorImg | 3 | 带有超链接的图片，其中超链接的src为http。 |
| Img           | 4 | HTML::img标签。             |
| Map           | 5 | 地理地址。                    |
| Phone         | 6 | 电话号码。                    |
| Unknown       | 7 | 未知内容。                    |

## CacheMode

缓存模式。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称      | 值 | 说明                                   |
| ------- | -- | ------------------------------------ |
| ArkTS-Dyn: Default<sup>9+</sup> <br>ArkTS-Sta: DEFAULT| 0 | 优先使用未过期cache加载资源，无效或无cache时从网络获取。<br>**ArkTS-Dyn起始版本：** 9 <br> **ArkTS-Sta起始版本：** 22|
| ArkTS-Dyn: None  <br> ArkTS-Sta: NONE| 1 | 优先使用cache(含过期)加载资源，无cache时从网络获取。 <br>**ArkTS-Dyn起始版本：** 8 <br> **ArkTS-Sta起始版本：** 22|
| ArkTS-Dyn: Online <br>ArkTS-Sta: ONLINE| 2 | 强制从网络获取最新资源，不使用任何cache。<br>**ArkTS-Dyn起始版本：** 8 <br> **ArkTS-Sta起始版本：** 22|
| ArkTS-Dyn: Only <br>ArkTS-Sta: ONLY| 3 | 仅使用本地cache加载资源。 <br>**ArkTS-Dyn起始版本：** 8 <br> **ArkTS-Sta起始版本：** 22|

## OverScrollMode<sup>11+</sup>

设置Web的过滚动模式为关闭或开启。

 **系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

| 名称     | 值 | 说明          |
| ------ | -- | ----------- |
| NEVER  | 0 | Web过滚动模式关闭。 |
| ALWAYS | 1 | Web过滚动模式开启。 |

## BlurOnKeyboardHideMode<sup>14+</sup>

设置手动收起软键盘时Web元素是否失焦。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

**参数：**

| 名称     | 值 | 说明          |
| ------ | -- | ----------- |
| SILENT  | 0 | 软键盘收起时Web组件失焦功能关闭，当用户手动收起软键盘时焦点仍在文本框。 |
| BLUR | 1 | 软键盘收起时Web组件失焦功能开启，当用户手动收起软键盘时，焦点会从文本框转移到Web的body上，文本框失焦。 |

## WebDarkMode<sup>9+</sup>

Web深色模式的配置。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称   | 值 | 说明           |
| ---- | -- | ------------ |
| ArkTS-Dyn: Off <br>ArkTS-Sta: OFF| 0 | Web深色模式关闭。   |
| ArkTS-Dyn: On  <br>ArkTS-Sta: ON| 1 | Web深色模式开启。   |
| ArkTS-Dyn: Auto <br>ArkTS-Sta: AUTO| 2 | Web深色模式跟随系统。 |

## WebCaptureMode<sup>10+</sup>

Web屏幕捕获模式。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 22

| 名称          | 值 | 说明      |
| ----------- | -- | ------- |
| HOME_SCREEN | 0 | 主屏捕获模式。 |

## ThreatType<sup>11+</sup>

定义网站风险类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

| 名称             | 值 | 说明                   |
| ---------------- | -- | ----------------------|
| THREAT_ILLEGAL  | 0 | 非法网站。              |
| THREAT_FRAUD    | 1 | 欺诈网站。              |
| THREAT_RISK     | 2 | 存在安全风险的网站。      |
| THREAT_WARNING  | 3 | 涉嫌包含不健康内容的网站。 |
| THREAT_NONE<sup>21+</sup>      | 4 | 安全检查通过，未发现任何风险。 |
| THREAT_UNPROCESSED<sup>21+</sup>  | 5 | 未进行安全检查。 |

## RenderExitReason<sup>9+</sup>

onRenderExited接口返回的渲染进程退出的具体原因。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称                         | 值 | 说明                |
| -------------------------- | -- | ----------------- |
| ArkTS-Dyn: ProcessAbnormalTermination <br>ArkTS-Sta: PROCESS_ABNORMAL_TERMINATION| 0 | 渲染进程异常退出。         |
| ArkTS-Dyn: ProcessWasKilled <br>ArkTS-Sta: PROCESS_WAS_KILLED| 1 | 收到SIGKILL，或被手动终止。 |
| ArkTS-Dyn: ProcessCrashed <br>ArkTS-Sta: PROCESS_CRASHED| 2 | 渲染进程崩溃退出，如段错误。    |
| ArkTS-Dyn: ProcessOom <br>ArkTS-Sta: PROCESS_OOM| 3 | 程序内存不足。           |
| ArkTS-Dyn: ProcessExitUnknown <br>ArkTS-Sta: PROCESS_EXIT_UNKNOWN| 4 | 其他原因。             |

## SslError<sup>9+</sup>

onSslErrorEventReceive接口返回的SSL错误的具体原因。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称           | 值 | 说明          |
| ------------ | -- | ----------- |
| ArkTS-Dyn: Invalid <br>ArkTS-Sta: INVALID| 0 | 一般错误。       |
| ArkTS-Dyn: HostMismatch <br>ArkTS-Sta: HOST_MISMATCH| 1 | 主机名不匹配。     |
| ArkTS-Dyn: DateInvalid <br>ArkTS-Sta: DATE_INVALID| 2 | 证书日期无效。     |
| ArkTS-Dyn: Untrusted <br>ArkTS-Sta: UNTRUSTED| 3 | 证书颁发机构不受信任。 |

## FileSelectorMode<sup>9+</sup>

文件选择器的模式。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称                   | 值 | 说明         |
| -------------------- | -- | ---------- |
| FileOpenMode         | 0 | 打开上传单个文件。  |
| FileOpenMultipleMode | 1 | 打开上传多个文件。  |
| FileOpenFolderMode   | 2 | 打开上传文件夹模式。 |
| FileSaveMode         | 3 | 文件保存模式。    |

## WebLayoutMode<sup>11+</sup>

Web布局模式的配置。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

| 名称          | 值 | 说明                 |
| ----------- | -- | ------------------ |
| NONE        | 0 | Web布局跟随系统。         |
| FIT_CONTENT | 1 | Web基于页面大小的自适应网页布局。 |

## RenderProcessNotRespondingReason<sup>12+</sup>

触发渲染进程无响应回调的原因。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23
| 名称                           | 值 | 说明           |
| ----------------------------- | -- | ------------ |
| INPUT_TIMEOUT                  | 0 | 发送给渲染进程的input事件响应超时。   |
| NAVIGATION_COMMIT_TIMEOUT      | 1 | 新的网页加载导航响应超时。   |

## ProtectedResourceType<sup>9+</sup>

**系统能力：** SystemCapability.Web.Webview.Core

| 名称                          | 值 | 说明            |    可申请的权限          |
| --------------------------- | --------------- | ------------- |  ---------------------|
| ArkTS-Dyn: MidiSysex  <br>ArkTS-Sta: MIDI_SYSEX| TYPE_MIDI_SYSEX | MIDI SYSEX资源。<br>目前仅支持权限事件上报，MIDI设备的使用还未支持。<br>**ArkTS-Dyn起始版本：** 9 <br> **ArkTS-Sta起始版本：** 22|暂不支持申请使用MIDI(Musical Instrument Digital Interface)设备相关权限。|
| ArkTS-Dyn: VIDEO_CAPTURE<sup>10+</sup> <br>ArkTS-Sta: VIDEO_CAPTURE| TYPE_VIDEO_CAPTURE | 视频捕获资源，例如相机。<br>**ArkTS-Dyn起始版本：** 10 <br> **ArkTS-Sta起始版本：** 22|相机权限：ohos.permission.CAMERA。|
| ArkTS-Dyn: AUDIO_CAPTURE<sup>10+</sup> <br>ArkTS-Sta: AUDIO_CAPTURE| TYPE_AUDIO_CAPTURE | 音频捕获资源，例如麦克风。<br>**ArkTS-Dyn起始版本：** 10 <br> **ArkTS-Sta起始版本：** 22|麦克风权限：ohos.permission.MICROPHONE。|
| ArkTS-Dyn: SENSOR<sup>12+</sup> <br>ArkTS-Sta: SENSOR| TYPE_SENSOR | 传感器资源，例如加速度传感器。<br>**ArkTS-Dyn起始版本：** 12 <br> **ArkTS-Sta起始版本：** 22|加速度传感器权限：ohos.permission.ACCELEROMETER、 <br>陀螺仪传感器权限：ohos.permission.GYROSCOPE。 |

## ContextMenuSourceType<sup>9+</sup>

触发上下文菜单的事件来源。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称       | 值 | 说明         |
| --------- | -- |------------ |
| None      | 0 | 其他事件来源。 |
| Mouse     | 1 | 鼠标事件。   |
| LongPress | 2 | 长按事件。   |

## ContextMenuDataMediaType<sup>22+</sup>
触发上下文菜单的网页元素类型（增强获取类型能力）。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

| 名称    | 值 | 说明            |
| ----- | -- | ------------- |
| NONE  | 0 | 默认值，表示当前上下文菜单不关联任何媒体类型（例如右键文本或空白区域）。|
| IMAGE | 1 | 图片类型。           |
| VIDEO | 2 | 视频类型。           |
| AUDIO | 3 | 音频类型。           |
| CANVAS| 4 | Canvas类型。           |

## ContextMenuMediaType<sup>9+</sup>

触发上下文菜单的网页元素类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称    | 值 | 说明            |
| ----- | -- | ------------- |
| None  | 0 | 非特殊媒体或其他媒体类型。 |
| Image | 1 | 图片。           |

## ContextMenuDataMediaType<sup>22+</sup>
触发上下文菜单的网页元素类型（增强获取类型能力）。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 22

| 名称    | 值 | 说明            |
| ----- | -- | ------------- |
| NONE  | 0 | 默认值，表示当前上下文菜单不关联任何媒体类型（例如右键文本或空白区域）。|
| IMAGE | 1 | 图片类型。           |
| VIDEO | 2 | 视频类型。           |
| AUDIO | 3 | 音频类型。           |
| CANVAS| 4 | Canvas类型。           |

## ContextMenuInputFieldType<sup>9+</sup>

输入框类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称        | 值 | 说明                          |
| --------- | -- | --------------------------- |
| None      | 0 | 非输入框。                       |
| PlainText | 1 | 纯文本类型，包括text、search、email等。 |
| Password  | 2 | 密码类型。                       |
| Number    | 3 | 数字类型。                       |
| Telephone | 4 | 电话号码类型。                     |
| Other     | 5 | 其他类型。                       |

## NativeEmbedStatus<sup>11+</sup>

定义同层标签生命周期，当加载页面中有同层标签会触发CREATE，同层标签移动或者放大会触发UPDATE，退出页面会触发DESTROY。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

| 名称                           | 值 | 说明           |
| ----------------------------- | -- | ------------ |
| CREATE                        | 0 | 同层标签创建。   |
| UPDATE                        | 1 | 同层标签更新。   |
| DESTROY                       | 2 | 同层标签销毁。 |
| ENTER_BFCACHE<sup>12+</sup>   | 3 | 同层标签进入BFCache。   |
| LEAVE_BFCACHE<sup>12+</sup>   | 4 | 同层标签离开BFCache。 |

## ContextMenuEditStateFlags<sup>9+</sup>

支持以按位或的方式使用此枚举。例如，如果需要同时支持CAN_CUT、CAN_COPY和CAN_SELECT_ALL，可使用CAN_CUT | CAN_COPY | CAN_SELECT_ALL或11。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称            | 值 | 说明     |
| -------------- | -- | -------- |
| NONE           | 0 | 不可编辑。 |
| CAN_CUT        | 1 << 0 | 支持剪切。 |
| CAN_COPY       | 1 << 1 | 支持拷贝。 |
| CAN_PASTE      | 1 << 2 | 支持粘贴。 |
| CAN_SELECT_ALL | 1 << 3 | 支持全选。 |

## WebNavigationType<sup>11+</sup>

定义navigation类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

| 名称                           | 值 | 说明           |
| ----------------------------- | -- | ------------ |
| UNKNOWN                       | 0 | 未知类型。   |
| MAIN_FRAME_NEW_ENTRY          | 1 | 主文档上产生的新的历史节点跳转。   |
| MAIN_FRAME_EXISTING_ENTRY     | 2 | 主文档上产生的到已有的历史节点的跳转。 |
| NAVIGATION_TYPE_NEW_SUBFRAME  | 4 | 子文档上产生的用户触发的跳转。 |
| NAVIGATION_TYPE_AUTO_SUBFRAME | 5 | 子文档上产生的非用户触发的跳转。 |

## RenderMode<sup>12+</sup>

定义Web组件的渲染方式，默认为异步渲染模式。

建议使用异步渲染模式，异步渲染模式有更好的性能和更低的功耗。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称                           | 值 | 说明           |
| ----------------------------- | -- | ------------ |
| ASYNC_RENDER                        | 0 | Web组件异步渲染模式，ArkWeb组件作为图形surface节点，独立送显，Web组件的宽度最大规格不超过7,680 px（物理像素）。   |
| SYNC_RENDER                        | 1 | Web组件同步渲染模式，ArkWeb组件作为图形canvas节点，跟随系统组件一起送显，可以渲染更长的Web组件内容，Web组件的宽度最大规格不超过500,000 px（物理像素）。   |

## ViewportFit<sup>12+</sup>

网页meta中viewport-fit配置的视口类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

| 名称                           | 值 | 说明           |
| ----------------------------- | -- | ------------ |
| AUTO                  | 0 | 默认值，整个网页可见。   |
| CONTAINS      | 1 | 初始布局视口和视觉视口为适应设备显示屏的最大矩形内。   |
| COVER      | 2| 初始布局视口和视觉视口为设备物理屏幕的外接矩形内。   |

## WebKeyboardAvoidMode<sup>12+</sup>

软键盘避让的模式。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称               | 值 | 说明           |
| ------------------ | -- | ------------ |
| RESIZE_VISUAL      | 0 | 软键盘避让时，仅调整可视视口大小，不调整布局视口大小。   |
| RESIZE_CONTENT     | 1 | 默认值，软键盘避让时，同时调整可视视口和布局视口的大小。 |
| OVERLAYS_CONTENT   | 2 | 不调整任何视口大小，不会触发软键盘避让。   |
| RETURN_TO_UICONTEXT<sup>22+</sup> | 3 | Web组件的软键盘避让行为将跟随UIcontext设置的[KeyboardAvoidMode](../apis-arkui/js-apis-arkui-UIContext.md#keyboardavoidmode11)模式，Web组件不再处理组件的避让。 |

## WebElementType<sup>13+</sup>

网页元素信息。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 名称       | 值 | 说明              |
| --------- | -- | ----------------- |
| IMAGE     | 1 | 网页元素为图像类型。<br>**ArkTS-Dyn起始版本：** 13 <br> **ArkTS-Sta起始版本：** 23 |
| LINK     | 2 | 网页元素为超链接类型。<br>**ArkTS-Dyn起始版本：** 20 <br> **ArkTS-Sta起始版本：** 23 |
| TEXT     | 3 | 网页元素为文本或可编辑区域类型。<br>**ArkTS-Dyn起始版本：** 21 <br> **ArkTS-Sta起始版本：** 23 |

## WebResponseType<sup>13+</sup>

菜单的响应类型。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 名称            | 值 | 说明                |
| -------------- | -- | ------------------  |
| LONG_PRESS     | 1 | 通过长按触发菜单弹出。<br>**ArkTS-Dyn起始版本：** 13 <br> **ArkTS-Sta起始版本：** 23 |
| RIGHT_CLICK<sup>21+</sup>    | 2 | 通过鼠标右键触发菜单弹出。<br>**ArkTS-Dyn起始版本：** 21 <br> **ArkTS-Sta起始版本：** 23 |

## AudioSessionType<sup>20+</sup>

应用中Web音频类型。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 22

**参数：**

| 名称            | 值 | 说明                |
| -------------- | -- | ------------------  |
| AMBIENT     | 3 | 适用于网页游戏场景，支持Web游戏声音与系统音乐同时播放。对应系统音频流类型STREAM_USAGE_GAME。|

## PdfLoadResult<sup>20+</sup>

定义PDF页面的加载结果。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

| 名称             | 值    | 说明                                       |
| -------------- | ---- | ---------------------------------------- |
| LOAD_SUCCESS | 0 | PDF页面加载成功。    |
| PARSE_ERROR_FILE | 1 | PDF文件加载失败的错误码。 |
| PARSE_ERROR_FORMAT | 2 | PDF文件格式不支持的错误码。 |
| PARSE_ERROR_PASSWORD | 3 | PDF文件密码不正确的错误码。 |
| PARSE_ERROR_HANDLER | 4 | PDF文件处理失败的错误码。 |

## GestureFocusMode<sup>20+</sup>

手势获焦的模式。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

| 名称                       | 值 | 说明           |
| -------------------------- | -- | ------------- |
| DEFAULT                    | 0 | 默认值，Web会在触摸按下屏幕时申请获焦，包括点击、长按、滑动、缩放等任何触摸屏幕的手势行为。 |
| GESTURE_TAP_AND_LONG_PRESS | 1 | Web只会在点击和长按手势事件生成时申请获焦，点击和长按在触摸抬起之后生成，滑动和缩放等手势行为不会获焦。 |

## WebRotateEffect<sup>22+</sup>

组件旋转时，宽高动画过程中组件内容如何填充以适应新尺寸的方式。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 22

| 名称                       | 值 | 说明           |
| -------------------------- | -- | ------------- |
| TOPLEFT_EFFECT                    | 0 | 默认值，组件旋转时，保持动画终态的内容大小，并且内容始终与组件保持左上角对齐。 |
| RESIZE_COVER_EFFECT | 1 | 组件旋转时，保持动画终态内容的宽高比进行缩小或放大，使内容两边都大于或等于组件两边，且与组件保持中心对齐，显示内容的中间部分。 |

## NativeEmbedParamStatus<sup>21+</sup>

定义同层渲染object标签内嵌param元素的状态变化类型，当添加param元素时触发ADD，修改param元素属性触发UPDATE，删除param元素触发DELETE。

**系统能力：** SystemCapability.Web.Webview.Core

| 名称                           | 值 | 说明           |
| ----------------------------- | -- | ------------ |
| ADD                           | 0 | 添加param元素。   |
| UPDATE                        | 1 | 更改param元素属性。   |
| DELETE                        | 2 | 删除param元素。 |

## DetectedBlankScreenReason<sup>22+</sup>

白屏的具体原因。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

| 名称          | 值 | 说明                 |
| ----------- | -- | ------------------ |
| NO_CONTENTFUL_NODES        | 0 | 没有命中任何有内容的节点。<br>当检测策略为DETECTION_CONTENTFUL_NODES_SEVENTEEN时可能触发。         |
| SUB_THRESHOLD_CONTENTFUL_NODES | 1 | 命中有内容节点的数量小于等于阈值。<br>当检测策略为DETECTION_CONTENTFUL_NODES_SEVENTEEN，且开发者设置了节点数量阈值contentfulNodesCountThreshold时可能触发。 |

## BlankScreenDetectionMethod<sup>22+</sup>

白屏检测使用的检测策略的方法。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

| 名称          | 值 | 说明                 |
| ----------- | -- | ------------------ |
| DETECTION_CONTENTFUL_NODES_SEVENTEEN        | 0 | 以17点检测法进行页面检测。当检测点命中已经渲染了且有意义的节点，则认为有命中。有意义的节点指的是图片，视频和文字节点。<br>当无命中，或少于用户设置阈值命中时，则认为是白屏或者近似白屏。<br>其中，检测的17个点位包括：<br>中心点 (1个)： 位于页面的几何中心。<br>内部网格交点 (16个)：在页面区域内定义一个5×5 的均匀网格，这16个点即为页面内4条垂直等分线和4条水平等分线的交点。         |


## CameraCaptureState<sup>23+</sup>

定义摄像头使用状态的值。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称   | 值   | 说明         |
| ------ | ---- | ------------ |
| NONE   | 0    | 摄像头未工作。 |
| PAUSED | 1    | 摄像头暂停中。 |
| ACTIVE | 2    | 摄像头捕获中。 |

## MicrophoneCaptureState<sup>23+</sup>

定义麦克风使用状态的值。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称   | 值   | 说明         |
| ------ | ---- | ------------ |
| NONE   | 0    | 麦克风未工作。 |
| PAUSED | 1    | 麦克风暂停中。 |
| ACTIVE | 2    | 麦克风捕获中。 |

## NavigationPolicy<sup>23+</sup>

WebView中新窗口的打开方式。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称                           | 值 | 说明           |
| ----------------------------- | -- | ------------ |
| NEW_POPUP                     | 0 | 在新弹窗中打开。   |
| NEW_WINDOW                    | 1 | 在新窗口中打开。   |
| NEW_BACKGROUND_TAB            | 2 | 在新标签页中以后台方式打开。 |
| NEW_FOREGROUND_TAB            | 3 | 在新标签页中以前台方式打开。 |
