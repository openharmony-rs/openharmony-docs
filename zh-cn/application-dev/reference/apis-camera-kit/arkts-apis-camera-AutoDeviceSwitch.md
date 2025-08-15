# Interface (AutoDeviceSwitch)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @zengyawen-->

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 13开始支持。

AutoDeviceSwitch 继承自 [AutoDeviceSwitchQuery](arkts-apis-camera-AutoDeviceSwitch.md)。

自动切换镜头类，继承自[AutoDeviceSwitchQuery](arkts-apis-camera-AutoDeviceSwitch.md)，用于使能或去使能自动切换镜头。

使用建议：自动切换镜头功能由系统自动完成输入设备切换、会话配置和参数接续，
如系统发现镜头切换时，两颗镜头的变焦范围不一致，则会通过[AutoDeviceSwitchStatus](arkts-apis-camera-i.md#autodeviceswitchstatus13)中的isDeviceCapabilityChanged字段告知应用，
但仍需要应用自己处理UX的变更（如变焦范围的调整，需要重新通过[getZoomRatioRange](arkts-apis-camera-ZoomQuery.md#getzoomratiorange11)接口获取数据并更新UX），
因此更适用于极简UX交换的场景。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## enableAutoDeviceSwitch<sup>13+</sup>

enableAutoDeviceSwitch(enabled: boolean): void

使能或去使能自动切换镜头。可以先通过[isAutoDeviceSwitchSupported](arkts-apis-camera-AutoDeviceSwitchQuery.md#isautodeviceswitchsupported13)获取当前设备是否支持自动切换镜头。

> **说明：**
> 该接口仅用于有多个前置镜头的折叠设备，在不同的折叠状态下可自动切换到当前可使用的前置镜头。无法实现前后置镜头的切换。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名         | 类型  | 必填 | 说明  |
| ----------- |---------------------- |---| -------------------------- |
| enabled | boolean  | 是 | 使能或去使能自动切换镜头。true表示使能，false表示不使能。   |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID   | 错误信息                                                                                                                                       |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------|
| 7400101 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameters verification failed. |
| 7400102 | Operation not allowed.                                                                                                                         |
| 7400103 | Session not config.                                                                                                                            |
| 7400201 | Camera service fatal error.                                                                                                                    |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function enableAutoDeviceSwitch(session: camera.PhotoSession, isEnable: boolean): void {
  try {
    session.enableAutoDeviceSwitch(isEnable);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The enableAutoDeviceSwitch call failed, error code: ${err.code}`);
  }
}
```
