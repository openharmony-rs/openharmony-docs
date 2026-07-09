# @ohos.PiPWindow (画中画窗口)(系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @betafringe007-->
<!--Designer: @taoweihua-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

该模块提供画中画基础功能，包括判断当前系统是否支持画中画功能，以及创建画中画控制器用于启动或停止画中画等。适用于视频播放、视频通话、视频会议或车载影像场景下，以小窗（画中画）模式呈现内容。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 在<!--RP2-->OpenHarmony 6.0<!--RP2End-->之前，支持在Phone、Tablet设备使用画中画功能，其他设备不可用；从<!--RP2-->OpenHarmony 6.0<!--RP2End-->开始，支持在Phone、PC/2in1、Tablet设备使用画中画功能，其他设备不可用；从OpenHarmony 7.0.0开始，支持在Phone、PC/2in1、Tablet、Car设备使用画中画功能，其他设备不可用。
>
> - 针对系统能力SystemCapability.Window.SessionManager，请先使用[canIUse()](../common/js-apis-syscap.md#caniuse)接口判断当前设备是否支持此syscap及对应接口。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.PiPWindow (画中画窗口)](js-apis-pipWindow.md)。

## 导入模块

```ts
import { PiPWindow } from '@kit.ArkUI';
```


## PiPTemplateType

画中画模板类型枚举。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Window.SessionManager

| 名称            | 值   | 说明                                   |
|---------------|-----|--------------------------------------|
| VIDEO_DRIVE   | 4   | 表示将要切换为画中画播放的媒体类型是车载影像，系统依此加载车载影像模板。<br>**ArkTS-Dyn起始版本：** 26.0.0<br>**ArkTS-Sta起始版本：** 26.0.0<br>**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0 开始，该接口支持在原子化服务中使用。<br>**设备行为差异：** 该模板类型在Car设备中正常调用，在其他设备中返回801错误码。|

## PiPController

画中画控制器实例。用于启动、停止画中画以及更新回调注册等。

下列API示例中都需先使用[PiPWindow.create()](js-apis-pipWindow.md#pipwindowcreate)方法获取到PiPController实例，再通过此实例调用对应方法。

**系统能力：** SystemCapability.Window.SessionManager

### isPiPSupported<sup>18+</sup>

isPiPSupported(): boolean

判断当前设备是否支持画中画功能。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Window.SessionManager

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型      | 说明                                  |
|----------|-------------------------------------|
| boolean  | 当前设备是否支持画中画功能。true表示支持，false表示不支持。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[窗口错误码](errorcode-window.md)。

| 错误码ID | 错误信息                                    |
|-------|---------------------------------------------|
| 202   | Not System App. Interface caller is not a system app. |
| 1300014    | PiP internal error.                                    |

**示例：**

```ts
try {
  if (!this.pipController) {
    return;
  }
  let isSupported: boolean = this.pipController!.isPiPSupported();
  console.info('isPiPSupported:' + isSupported);
} catch (exception) {
  console.error(`Failed to check if pip is supported. Cause code: ${exception.code}, message: ${exception.message}`);
}
```