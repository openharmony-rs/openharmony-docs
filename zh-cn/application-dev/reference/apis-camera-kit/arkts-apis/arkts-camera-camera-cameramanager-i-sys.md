# CameraManager

```TypeScript
interface CameraManager
```

相机管理器类，使用前需要通过[getCameraManager](arkts-camera-camera-getcameramanager-f.md)接口获取相机管理实例。

**起始版本：** 10

<!--Device-camera-interface CameraManager--><!--Device-camera-interface CameraManager-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## createCameraInputWithTokenId

```TypeScript
createCameraInputWithTokenId(camera: CameraDevice, tokenId: number): CameraInput
```

通过相机和调用方 token 创建 CameraInput 实例。

使用此接口前，需先通过 getSupportedCameras 接口查询当前设备支持的相机设备列表，开发者需根据具体场景选择满足需求的相机设备，然后使用此接口创建 CameraInput 实例。

**起始版本：** 24

**需要权限：** ohos.permission.CAMERA

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CameraManager-createCameraInputWithTokenId(camera: CameraDevice, tokenId: int): CameraInput--><!--Device-CameraManager-createCameraInputWithTokenId(camera: CameraDevice, tokenId: int): CameraInput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 是 | 用于创建实例的相机设备。 |
| tokenId | number | 是 | 调用方 token id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CameraInput](arkts-camera-camera-camerainput-i.md) | 返回 CameraInput 实例。接口调用失败时返回对应的错误码，类型为CameraErrorCode。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## createControlCenterSession

```TypeScript
createControlCenterSession(): ControlCenterSession
```

创建ControlCenterSession实例。

**起始版本：** 20

**需要权限：** ohos.permission.CAMERA_CONTROL

<!--Device-CameraManager-createControlCenterSession(): ControlCenterSession--><!--Device-CameraManager-createControlCenterSession(): ControlCenterSession-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ControlCenterSession](arkts-camera-camera-controlcentersession-i-sys.md) | ControlCenterSession 实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |

## createDepthDataOutput

```TypeScript
createDepthDataOutput(profile: DepthProfile): DepthDataOutput
```

创建DepthDataOutput实例。此接口同步返回结果。

**起始版本：** 13

<!--Device-CameraManager-createDepthDataOutput(profile: DepthProfile): DepthDataOutput--><!--Device-CameraManager-createDepthDataOutput(profile: DepthProfile): DepthDataOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profile | [DepthProfile](arkts-camera-camera-depthprofile-i-sys.md) | 是 | 支持的预览profile，通过[getSupportedOutputCapability](arkts-camera-camera-cameramanager-i.md#getsupportedoutputcapability) 获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DepthDataOutput](arkts-camera-camera-depthdataoutput-i-sys.md) | DepthDataOutput 实例。如果操作失败，返回[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) 中定义的错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createDepthDataOutput(cameraOutputCapability: camera.CameraOutputCapability, cameraManager: camera.CameraManager): camera.DepthDataOutput | undefined {
  let profile: camera.DepthProfile = cameraOutputCapability.depthProfiles[0];
  let depthDataOutput: camera.DepthDataOutput | undefined = undefined;
  try {
    depthDataOutput = cameraManager.createDepthDataOutput(profile);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The createDepthDataOutput call failed. error code: ${err.code}`);
  }
  return depthDataOutput;
}
```

<!--DelEnd-->

## isCameraMuteSupported

```TypeScript
isCameraMuteSupported(): boolean
```

查询相机设备是否支持静音。

**起始版本：** 10

<!--Device-CameraManager-isCameraMuteSupported(): boolean--><!--Device-CameraManager-isCameraMuteSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询相机设备是否可以静音的结果。**true** 表示可以静音，**false** 表示不可以。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 13+ |

<!--Del-->
**示例**

```TypeScript
function isCameraMuteSupported(cameraManager: camera.CameraManager): boolean {
  let isMuteSupported: boolean = cameraManager.isCameraMuteSupported();
  return isMuteSupported;
}
```

<!--DelEnd-->

## isControlCenterActive

```TypeScript
isControlCenterActive(): boolean
```

查询控制中心是否处于活跃状态。

**起始版本：** 20

<!--Device-CameraManager-isControlCenterActive(): boolean--><!--Device-CameraManager-isControlCenterActive(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示控制中心是否处于活跃状态的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |

## isPrelaunchSupported

```TypeScript
isPrelaunchSupported(camera: CameraDevice): boolean
```

查询相机设备是否支持预启动。

**起始版本：** 10

<!--Device-CameraManager-isPrelaunchSupported(camera: CameraDevice): boolean--><!--Device-CameraManager-isPrelaunchSupported(camera: CameraDevice): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 是 | 相机设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询是否支持预启动的结果。**true** 表示支持，**false** 表示不支持 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |

<!--Del-->
**示例**

```TypeScript
import { common } from '@kit.AbilityKit';

function isPreLaunchSupported(context: common.BaseContext): boolean {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  let cameras: Array<camera.CameraDevice> = cameraManager.getSupportedCameras();
  let isSupported: boolean = false;
  if (cameras && cameras.length >= 1) {
    isSupported = cameraManager.isPrelaunchSupported(cameras[0]);
    console.info(`PreLaunch supported states: ${isSupported}`);
    return isSupported;
  }
  return isSupported;
}
```

<!--DelEnd-->

## muteCameraPersistent

```TypeScript
muteCameraPersistent(mute: boolean, type: PolicyType): void
```

永久静音相机设备。

**起始版本：** 12

**需要权限：** ohos.permission.CAMERA_CONTROL

<!--Device-CameraManager-muteCameraPersistent(mute: boolean, type: PolicyType): void--><!--Device-CameraManager-muteCameraPersistent(mute: boolean, type: PolicyType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 静音或取消静音相机设备。**true** 表示静音，**false** 表示取消静音。 |
| type | [PolicyType](arkts-camera-camera-policytype-e-sys.md) | 是 | 策略类型。可用选项详情请参见[PolicyType](arkts-camera-camera-policytype-e-sys.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |

<!--Del-->
**示例**

```TypeScript
function muteCameraPersistent(cameraManager: camera.CameraManager): void {
  let mute: boolean = true;
  cameraManager.muteCameraPersistent(mute, camera.PolicyType.PRIVACY);
}
```

<!--DelEnd-->

## off('cameraMute')

```TypeScript
off(type: 'cameraMute', callback?: AsyncCallback<boolean>): void
```

取消订阅相机静音状态事件。

**起始版本：** 10

<!--Device-CameraManager-off(type: 'cameraMute', callback?: AsyncCallback<boolean>): void--><!--Device-CameraManager-off(type: 'cameraMute', callback?: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cameraMute' | 是 | 事件类型。值固定为 **'cameraMute'**，表示相机静音状态。获取 CameraManager 实例后即可监听此事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 否 | 用于返回相机静音状态的回调。**true** 表示已静音，**false** 表示未静音。此参数为可选参数。如果指定此参数，将取消订阅指定回调的 **on('cameraMute')** 事件。（回调对象不能是匿名函数。） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 13+ |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, curMuted: boolean): void {
  let isMuted: boolean = curMuted;
}

function unregisterCameraMute(cameraManager: camera.CameraManager): void {
  cameraManager.off('cameraMute', callback);
}
```

<!--DelEnd-->

## off('controlCenterStatusChange')

```TypeScript
off(type: 'controlCenterStatusChange', callback?: AsyncCallback<boolean>): void
```

取消订阅控制中心状态变更事件回调。

**起始版本：** 20

<!--Device-CameraManager-off(type: 'controlCenterStatusChange', callback?: AsyncCallback<boolean>): void--><!--Device-CameraManager-off(type: 'controlCenterStatusChange', callback?: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'controlCenterStatusChange' | 是 | 事件类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 否 | 用于获取控制中心状态变更的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |

## offCameraSharedStatus

```TypeScript
offCameraSharedStatus(callback?: Callback<CameraSharedStatusInfo>): void
```

取消订阅相机共享状态变更事件回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CameraManager-offCameraSharedStatus(callback?: Callback<CameraSharedStatusInfo>): void--><!--Device-CameraManager-offCameraSharedStatus(callback?: Callback<CameraSharedStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CameraSharedStatusInfo](arkts-camera-camera-camerasharedstatusinfo-i-sys.md)&gt; | 否 | 用于获取相机共享状态变更的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## on('cameraMute')

```TypeScript
on(type: 'cameraMute', callback: AsyncCallback<boolean>): void
```

订阅相机静音状态事件。此接口使用异步回调返回结果。

**起始版本：** 10

<!--Device-CameraManager-on(type: 'cameraMute', callback: AsyncCallback<boolean>): void--><!--Device-CameraManager-on(type: 'cameraMute', callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cameraMute' | 是 | 事件类型。值固定为 **'cameraMute'**，表示相机静音状态。获取 CameraManager 实例后即可监听此事件。当相机设备被静音或取消静音时，将触发此事件并返回状态。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 用于返回相机静音状态的回调。**true** 表示已静音，**false** 表示未静音。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 13+ |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, curMuted: boolean): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  let isMuted: boolean = curMuted;
  console.info(`cameraMute status: ${isMuted}`);
}

function registerCameraMute(cameraManager: camera.CameraManager): void {
  cameraManager.on('cameraMute', callback);
}
```

<!--DelEnd-->

## on('controlCenterStatusChange')

```TypeScript
on(type: 'controlCenterStatusChange', callback: AsyncCallback<boolean>): void
```

订阅控制中心状态变更事件回调。

**起始版本：** 20

<!--Device-CameraManager-on(type: 'controlCenterStatusChange', callback: AsyncCallback<boolean>): void--><!--Device-CameraManager-on(type: 'controlCenterStatusChange', callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'controlCenterStatusChange' | 是 | 事件类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 用于获取控制中心状态变更的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |

## onCameraSharedStatus

```TypeScript
onCameraSharedStatus(callback: Callback<CameraSharedStatusInfo>): void
```

订阅相机共享状态变更事件回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CameraManager-onCameraSharedStatus(callback: Callback<CameraSharedStatusInfo>): void--><!--Device-CameraManager-onCameraSharedStatus(callback: Callback<CameraSharedStatusInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CameraSharedStatusInfo](arkts-camera-camera-camerasharedstatusinfo-i-sys.md)&gt; | 是 | 用于获取相机共享状态变更的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## prelaunch

```TypeScript
prelaunch(): void
```

预启动相机设备。当用户点击系统相机图标启动相机应用时调用此接口。

**起始版本：** 10

<!--Device-CameraManager-prelaunch(): void--><!--Device-CameraManager-prelaunch(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application.<br>**适用版本：** 13+ |

<!--Del-->
**示例**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { camera } from '@kit.CameraKit';

function preLaunch(context: common.BaseContext): void {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  try {
    cameraManager.prelaunch();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`prelaunch error. Code: ${err.code}, message: ${err.message}`);
  }
}
```

<!--DelEnd-->

## preSwitchCamera

```TypeScript
preSwitchCamera(cameraId: string): void
```

预切换相机设备以加速其启动。

**起始版本：** 11

<!--Device-CameraManager-preSwitchCamera(cameraId: string): void--><!--Device-CameraManager-preSwitchCamera(cameraId: string): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraId | string | 是 | 相机 ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

<!--Del-->
**示例**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function preSwitch(cameraDevice: camera.CameraDevice, context: common.BaseContext): void {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  try {
    cameraManager.preSwitchCamera(cameraDevice.cameraId);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`prelaunch error. Code: ${err.code}, message: ${err.message}`);
  }
}
```

<!--DelEnd-->

## setPrelaunchConfig

```TypeScript
setPrelaunchConfig(prelaunchConfig: PrelaunchConfig): void
```

设置预启动配置。设置前，请先调用 [isPrelaunchSupported](#isprelaunchsupported) 查询相机设备是否支持预启动。

**起始版本：** 10

**需要权限：** ohos.permission.CAMERA

<!--Device-CameraManager-setPrelaunchConfig(prelaunchConfig: PrelaunchConfig): void--><!--Device-CameraManager-setPrelaunchConfig(prelaunchConfig: PrelaunchConfig): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| prelaunchConfig | [PrelaunchConfig](arkts-camera-camera-prelaunchconfig-i-sys.md) | 是 | 预启动配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application.<br>**适用版本：** 12+ |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

<!--Del-->
**示例**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function setPrelaunchConfig(context: common.BaseContext): void {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  let cameras: Array<camera.CameraDevice> = cameraManager.getSupportedCameras();
  if (cameras && cameras.length >= 1) {
    let cameraDevice: camera.CameraDevice = cameras[0];
    if(cameraManager.isPrelaunchSupported(cameraDevice)) {
      try {
        cameraManager.setPrelaunchConfig({cameraDevice: cameraDevice});
      } catch (error) {
        let err = error as BusinessError;
        console.error(`setPrelaunchConfig error. Code: ${err.code}, message: ${err.message}`);
      }
    }
  }
}
```

<!--DelEnd-->

## muteCamera

```TypeScript
muteCamera(mute: boolean): void
```

静音或取消静音相机设备。

**起始版本：** 10

**废弃版本：** 12

**替代接口：** [muteCameraPersistent](#mutecamerapersistent)

<!--Device-CameraManager-muteCamera(mute: boolean): void--><!--Device-CameraManager-muteCamera(mute: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mute | boolean | 是 | 静音或取消静音相机设备。**true** 表示静音，**false** 表示取消静音。 |

<!--Del-->
**示例**

```TypeScript
function muteCamera(cameraManager: camera.CameraManager): void {
  let mute: boolean = true;
  cameraManager.muteCamera(mute);
}
```

<!--DelEnd-->
