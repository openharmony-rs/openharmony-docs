# @ohos.PiPWindow

该模块提供画中画基础功能，包括判断当前系统是否支持画中画功能，以及创建画中画控制器用于启动或停止画中画等。适用于视频播放、视频通话或视频会议场景下，以小窗（画中画）模式呈现内容。
> **说明：**  
>  
> - 在<!--RP2-->OpenHarmony 6.0<!--RP2End-->之前，支持在Phone、Tablet设备使用画中画功能，其他设备不可用；从<!--RP2-->OpenHarmony 6.0&lt;!--RP2End--  
> &gt;开始，支持在Phone、PC/2in1、Tablet设备使用画中画功能，其他设备不可用。  
>  
> - 针对系统能力SystemCapability.Window.SessionManager，请先使用  
> [canIUse()](arkts-arkui-global-caniuse-f.md#caniuse)接口判断当前设备是否支持此syscap及对应接口。

**起始版本：** 11

<!--Device-unnamed-declare namespace PiPWindow--><!--Device-unnamed-declare namespace PiPWindow-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-arkui-pipwindow-create-f.md#create) | 创建画中画控制器，使用Promise异步回调。 |
| [create](arkts-arkui-pipwindow-create-f.md#create-1) | 创建画中画控制器，使用typeNode为画中画添加自定义UI节点。使用Promise异步回调。 |
| [isPiPEnabled](arkts-arkui-pipwindow-ispipenabled-f.md#ispipenabled) | 判断当前设备是否支持画中画功能。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ControlEventParam](arkts-arkui-pipwindow-controleventparam-i.md) | 画中画控制面板控件动作回调的参数。 |
| [PiPConfiguration](arkts-arkui-pipwindow-pipconfiguration-i.md) | 创建画中画控制器时的参数。 |
| [PiPController](arkts-arkui-pipwindow-pipcontroller-i.md) | 画中画控制器实例。用于启动、停止画中画以及更新回调注册等。  下列API示例中都需先使用[PiPWindow.create()](arkts-arkui-pipwindow-create-f.md#create)方法获取到PiPController实例，再通过此实例调用对应方法。 |
| [PiPWindowInfo](arkts-arkui-pipwindow-pipwindowinfo-i.md) | 画中画窗口信息。 |
| [PiPWindowSize](arkts-arkui-pipwindow-pipwindowsize-i.md) | 画中画窗口大小。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PiPController](arkts-arkui-pipwindow-pipcontroller-i-sys.md) | 画中画控制器实例。用于启动、停止画中画以及更新回调注册等。  下列API示例中都需先使用[PiPWindow.create()](arkts-arkui-pipwindow-create-f.md#create)方法获取到PiPController实例，再通过此实例调用对应方法。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PiPControlStatus](arkts-arkui-pipwindow-pipcontrolstatus-e.md) | 控制面板控件状态枚举。 |
| [PiPControlType](arkts-arkui-pipwindow-pipcontroltype-e.md) | 控制面板控件类型枚举。 |
| [PiPState](arkts-arkui-pipwindow-pipstate-e.md) | 画中画生命周期状态枚举。 |
| [PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md) | 画中画模板类型枚举。 |
| [VideoCallControlGroup](arkts-arkui-pipwindow-videocallcontrolgroup-e.md) | 视频通话控件组枚举。仅当[PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md) 为VIDEO_CALL时使用。 |
| [VideoLiveControlGroup](arkts-arkui-pipwindow-videolivecontrolgroup-e.md) | 视频直播控件组枚举。仅当[PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md) 为VIDEO_LIVE时使用。 |
| [VideoMeetingControlGroup](arkts-arkui-pipwindow-videomeetingcontrolgroup-e.md) | 视频会议控件组枚举。仅当[PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md) 为VIDEO_MEETING时使用。 |
| [VideoPlayControlGroup](arkts-arkui-pipwindow-videoplaycontrolgroup-e.md) | 视频播放控件组枚举。仅当[PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md)为VIDEO_PLAY时使用。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ControlPanelActionEventCallback](arkts-arkui-pipwindow-controlpanelactioneventcallback-t.md) | 描述画中画控制面板控件动作事件回调。 |
| [PiPActionEventType](arkts-arkui-pipwindow-pipactioneventtype-t.md) | 画中画控制面板控件动作事件类型，支持以下四种。 |
| [PiPCallActionEvent](arkts-arkui-pipwindow-pipcallactionevent-t.md) | 视频通话控制事件类型。 |
| [PiPControlGroup](arkts-arkui-pipwindow-pipcontrolgroup-t.md) | 画中画控制面板的可选控件组列表，应用可以配置是否显示可选控件。使用时必须和[PiPTemplateType](arkts-arkui-pipwindow-piptemplatetype-e.md)对应，否则[create](arkts-arkui-pipwindow-create-f.md#create)接口抛出401错误码。 |
| [PiPLiveActionEvent](arkts-arkui-pipwindow-pipliveactionevent-t.md) | 直播控制事件类型。 |
| [PiPMeetingActionEvent](arkts-arkui-pipwindow-pipmeetingactionevent-t.md) | 视频会议控制事件类型。 |
| [PiPVideoActionEvent](arkts-arkui-pipwindow-pipvideoactionevent-t.md) | 视频播放控制事件类型。 |

