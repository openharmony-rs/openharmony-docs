# @ohos.distributedHardware.mechanicManager

提供与本设备连接的机械设备的控制和交互能力。 包括连接管理、控制和监控功能@namespace mechanicManager

**起始版本：** 20

**系统能力：** SystemCapability.Mechanic.Core

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAttachedMechDevices](arkts-mechanic-mechanicmanager-getattachedmechdevices-f.md) | 获取已连接的机械设备列表 |
| [getCameraTrackingEnabled](arkts-mechanic-mechanicmanager-getcameratrackingenabled-f.md) | 获取相机跟踪状态 |
| [getCameraTrackingLayout](arkts-mechanic-mechanicmanager-getcameratrackinglayout-f.md) | 获取当前摄像头跟踪布局 |
| [isControlSupported](arkts-mechanic-mechanicmanager-iscontrolsupported-f.md) | 判断当前设备是否支持某类设备的具身控制 |
| [off](arkts-mechanic-mechanicmanager-off-f.md#offattachstatechange) | Unsubscribes from device attachment state change events. |
| [off](arkts-mechanic-mechanicmanager-off-f.md#offtrackingstatechange) | 设置相机跟踪布局 |
| [on](arkts-mechanic-mechanicmanager-on-f.md#onattachstatechange) | Subscribes to device attachment state change events. |
| [on](arkts-mechanic-mechanicmanager-on-f.md#ontrackingstatechange) | Subscribes to tracking events. |
| [setCameraTrackingEnabled](arkts-mechanic-mechanicmanager-setcameratrackingenabled-f.md) | 启用或禁用摄像机跟踪 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [connectDevice](arkts-mechanic-mechanicmanager-connectdevice-f-sys.md) | 基于地址连接设备 |
| [disconnectDevice](arkts-mechanic-mechanicmanager-disconnectdevice-f-sys.md) | 基于具身设备ID断开设备 |
| [doAction](arkts-mechanic-mechanicmanager-doaction-f-sys.md) | 执行一个动作序列 |
| [getCurrentAngles](arkts-mechanic-mechanicmanager-getcurrentangles-f-sys.md) | 获取机械设备的当前角度 |
| [getMaxRotationSpeed](arkts-mechanic-mechanicmanager-getmaxrotationspeed-f-sys.md) | Obtains the maximum rotation speed of a mechanical device. |
| [getMaxRotationTime](arkts-mechanic-mechanicmanager-getmaxrotationtime-f-sys.md) | Obtains the maximum continuous rotation duration of a mechanical device. |
| [getRotationAxesStatus](arkts-mechanic-mechanicmanager-getrotationaxesstatus-f-sys.md) | 获取当前转轴状态 |
| [getRotationLimits](arkts-mechanic-mechanicmanager-getrotationlimits-f-sys.md) | Obtains the maximum rotation angles relative to the reference point for the specified mechanical device. |
| [isSupportAction](arkts-mechanic-mechanicmanager-issupportaction-f-sys.md) | 判断是否支持某个动作 |
| [move](arkts-mechanic-mechanicmanager-move-f-sys.md) | 以特定参数移动一个具身设备 |
| [moveBySpeed](arkts-mechanic-mechanicmanager-movebyspeed-f-sys.md) | 以特定速度移动一个具身设备 |
| off | Unregister a listener for axis state changes. |
| on | Register a listener for axis state changes. The status of the rotation axis changes dynamically, which needs to be monitored. |
| [rotate](arkts-mechanic-mechanicmanager-rotate-f-sys.md) | 将机械设备旋转到相对角度 |
| [rotateBySpeed](arkts-mechanic-mechanicmanager-rotatebyspeed-f-sys.md) | 以指定的速度旋转机械设备 |
| [rotateToEulerAngles](arkts-mechanic-mechanicmanager-rotatetoeulerangles-f-sys.md) | 将机械设备旋转到绝对角度 |
| [searchTarget](arkts-mechanic-mechanicmanager-searchtarget-f-sys.md) | Searching for a specified target. |
| [setCameraTrackingLayout](arkts-mechanic-mechanicmanager-setcameratrackinglayout-f-sys.md) | 设置相机跟踪布局 |
| [setUserOperation](arkts-mechanic-mechanicmanager-setuseroperation-f-sys.md) | 设置用户操作 |
| [stopMoving](arkts-mechanic-mechanicmanager-stopmoving-f-sys.md) | 停止转动 |
| [subscribe](arkts-mechanic-mechanicmanager-subscribe-f-sys.md) | 订阅具身设备事件回调 |
| [turnBySpeed](arkts-mechanic-mechanicmanager-turnbyspeed-f-sys.md) | 以固定速度原地旋转 |
| [unSubscribe](arkts-mechanic-mechanicmanager-unsubscribe-f-sys.md) | 取消事件注册 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AttachStateChangeInfo](arkts-mechanic-mechanicmanager-attachstatechangeinfo-i.md) | 设备吸附状态回调信息 |
| [MechInfo](arkts-mechanic-mechanicmanager-mechinfo-i.md) | 机械设备信息 |
| [TrackingEventInfo](arkts-mechanic-mechanicmanager-trackingeventinfo-i.md) | Tracking event callback info. |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AddressInfo](arkts-mechanic-mechanicmanager-addressinfo-i-sys.md) | 配件设备信息定义 |
| [ConnectParam](arkts-mechanic-mechanicmanager-connectparam-i-sys.md) | 连接参数定义 |
| [EulerAngles](arkts-mechanic-mechanicmanager-eulerangles-i-sys.md) | Absolute euler angles relative to the home position. |
| [MechEvent](arkts-mechanic-mechanicmanager-mechevent-i-sys.md) | 具身设备事件定义 |
| [MoveParams](arkts-mechanic-mechanicmanager-moveparams-i-sys.md) | 设备移动参数 |
| [RotationAngles](arkts-mechanic-mechanicmanager-rotationangles-i-sys.md) | The rotion angles, relative to the current position. |
| [RotationAxesStateChangeInfo](arkts-mechanic-mechanicmanager-rotationaxesstatechangeinfo-i-sys.md) | 旋转轴状态变更信息 |
| [RotationAxesStatus](arkts-mechanic-mechanicmanager-rotationaxesstatus-i-sys.md) | Rotation axes status |
| [RotationLimits](arkts-mechanic-mechanicmanager-rotationlimits-i-sys.md) | 相对于参考点的旋转角度限制 |
| [RotationSpeed](arkts-mechanic-mechanicmanager-rotationspeed-i-sys.md) | 转速，负值表示顺时针旋转。正值表示逆时针旋转。 |
| [SearchParams](arkts-mechanic-mechanicmanager-searchparams-i-sys.md) | Parameters for target searching. |
| [SearchResult](arkts-mechanic-mechanicmanager-searchresult-i-sys.md) | Search result. |
| [SpeedParams](arkts-mechanic-mechanicmanager-speedparams-i-sys.md) | 速度控制参数 |
| [TargetInfo](arkts-mechanic-mechanicmanager-targetinfo-i-sys.md) | Target information. |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AttachState](arkts-mechanic-mechanicmanager-attachstate-e.md) | Device attach states.@enum { number } |
| [CameraTrackingLayout](arkts-mechanic-mechanicmanager-cameratrackinglayout-e.md) | 相机跟踪布局@enum { number } |
| [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e.md) | Enumerates the mechanical device types. @enum { number } |
| [TrackingEvent](arkts-mechanic-mechanicmanager-trackingevent-e.md) | 跟踪事件@enum { number } |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionType](arkts-mechanic-mechanicmanager-actiontype-e-sys.md) | 动作序列类型 |
| [AddressType](arkts-mechanic-mechanicmanager-addresstype-e-sys.md) | 具身设备地址类型 |
| [MarchingMode](arkts-mechanic-mechanicmanager-marchingmode-e-sys.md) | 行进模式定义 |
| [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e-sys.md) | Enumerates the mechanical device types. @enum { number } |
| [MechEventType](arkts-mechanic-mechanicmanager-mecheventtype-e-sys.md) | 具身设备事件定义 |
| [Operation](arkts-mechanic-mechanicmanager-operation-e-sys.md) | 用户操作@enum { number } |
| [Result](arkts-mechanic-mechanicmanager-result-e-sys.md) | Rotation execution results.@enum { number } |
| [RotationAxisLimited](arkts-mechanic-mechanicmanager-rotationaxislimited-e-sys.md) | 旋转轴限位状态@enum { number } |
| [SearchDirection](arkts-mechanic-mechanicmanager-searchdirection-e-sys.md) | Search direction.@enum { number } |
| [SpeedGear](arkts-mechanic-mechanicmanager-speedgear-e-sys.md) | 速度档位定义 |
| [TargetType](arkts-mechanic-mechanicmanager-targettype-e-sys.md) | Target type.@enum { number } |
<!--DelEnd-->
