# @ohos.distributedHardware.mechanicManager

Provides capabilities for controlling and interacting with mechanical devices connected to this device.The capabilities cover connection management, control, and monitoring.

**起始版本：** 20

<!--Device-unnamed-declare namespace mechanicManager--><!--Device-unnamed-declare namespace mechanicManager-End-->

**系统能力：** SystemCapability.Mechanic.Core

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAttachedMechDevices](arkts-mechanic-mechanicmanager-getattachedmechdevices-f.md#getattachedmechdevices-1) | Obtain the list of connected mechanical devices. |
| [getCameraTrackingEnabled](arkts-mechanic-mechanicmanager-getcameratrackingenabled-f.md#getcameratrackingenabled-1) | Checks whether camera tracking is enabled for this mechanical device. |
| [getCameraTrackingLayout](arkts-mechanic-mechanicmanager-getcameratrackinglayout-f.md#getcameratrackinglayout-1) | Obtains the camera tracking layout of this mechanical device. |
| [isControlSupported](arkts-mechanic-mechanicmanager-iscontrolsupported-f.md#iscontrolsupported-1) | Checks whether the current device supports embodied control for a specific type of device. |
| [off](arkts-mechanic-mechanicmanager-off-f.md#off-1) | Unsubscribes from device attachment state change events. |
| [off](arkts-mechanic-mechanicmanager-off-f.md#off-2) | Unsubscribes from tracking events. |
| [on](arkts-mechanic-mechanicmanager-on-f.md#on-1) | Subscribes to device attachment state change events. |
| [on](arkts-mechanic-mechanicmanager-on-f.md#on-2) | Subscribes to tracking events. |
| [setCameraTrackingEnabled](arkts-mechanic-mechanicmanager-setcameratrackingenabled-f.md#setcameratrackingenabled-1) | Enables or disables camera tracking. |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [doAction](arkts-mechanic-mechanicmanager-doaction-f-sys.md#doaction-1) | Execute an action sequence. |
| [getCurrentAngles](arkts-mechanic-mechanicmanager-getcurrentangles-f-sys.md#getcurrentangles-1) | Obtains the current angles of a mechanical device. |
| [getMaxRotationSpeed](arkts-mechanic-mechanicmanager-getmaxrotationspeed-f-sys.md#getmaxrotationspeed-1) | Obtains the maximum rotation speed of a mechanical device. |
| [getMaxRotationTime](arkts-mechanic-mechanicmanager-getmaxrotationtime-f-sys.md#getmaxrotationtime-1) | Obtains the maximum continuous rotation duration of a mechanical device. |
| [getRotationAxesStatus](arkts-mechanic-mechanicmanager-getrotationaxesstatus-f-sys.md#getrotationaxesstatus-1) | Obtains the status of the rotation axes. |
| [getRotationLimits](arkts-mechanic-mechanicmanager-getrotationlimits-f-sys.md#getrotationlimits-1) | Obtains the maximum rotation angles relative to the reference point for the specified mechanical device. |
| [isSupportAction](arkts-mechanic-mechanicmanager-issupportaction-f-sys.md#issupportaction-1) | Check whether the specific action type is supported. |
| [move](arkts-mechanic-mechanicmanager-move-f-sys.md#move-1) | Move a mechanical device with the specified parameters. |
| [moveBySpeed](arkts-mechanic-mechanicmanager-movebyspeed-f-sys.md#movebyspeed-1) | Move a mechanical device at the specified speed. |
| [off](arkts-mechanic-mechanicmanager-off-f-sys.md#off-3) | Unregister a listener for axis state changes. |
| [on](arkts-mechanic-mechanicmanager-on-f-sys.md#on-3) | Register a listener for axis state changes.The status of the rotation axis changes dynamically, which needs to be monitored. |
| [rotate](arkts-mechanic-mechanicmanager-rotate-f-sys.md#rotate-1) | Rotates a mechanical device to the relative angles. |
| [rotateBySpeed](arkts-mechanic-mechanicmanager-rotatebyspeed-f-sys.md#rotatebyspeed-1) | Rotates a mechanical device at the specified speed. |
| [rotateToEulerAngles](arkts-mechanic-mechanicmanager-rotatetoeulerangles-f-sys.md#rotatetoeulerangles-1) | Rotates a mechanical device to the absolute angles. |
| [searchTarget](arkts-mechanic-mechanicmanager-searchtarget-f-sys.md#searchtarget-1) | Searching for a specified target. |
| [setCameraTrackingLayout](arkts-mechanic-mechanicmanager-setcameratrackinglayout-f-sys.md#setcameratrackinglayout-1) | Sets the camera tracking layout for this mechanical device. |
| [setUserOperation](arkts-mechanic-mechanicmanager-setuseroperation-f-sys.md#setuseroperation-1) | Sets a user operation. |
| [stopMoving](arkts-mechanic-mechanicmanager-stopmoving-f-sys.md#stopmoving-1) | Stops a mechanical device from moving. |
| [subscribe](arkts-mechanic-mechanicmanager-subscribe-f-sys.md#subscribe-1) | Subscribe to the specified events. |
| [turnBySpeed](arkts-mechanic-mechanicmanager-turnbyspeed-f-sys.md#turnbyspeed-1) | Rotate in place according to the speed. |
| [unSubscribe](arkts-mechanic-mechanicmanager-unsubscribe-f-sys.md#unsubscribe-1) | Unsubscribes the specified events. |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AttachStateChangeInfo](arkts-mechanic-mechanicmanager-attachstatechangeinfo-i.md) | Callback information about the device attachment state change. |
| [MechInfo](arkts-mechanic-mechanicmanager-mechinfo-i.md) | Mechanical device information. |
| [TrackingEventInfo](arkts-mechanic-mechanicmanager-trackingeventinfo-i.md) | Tracking event callback info. |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EulerAngles](arkts-mechanic-mechanicmanager-eulerangles-i-sys.md) | Absolute euler angles relative to the home position. |
| [MechEvent](arkts-mechanic-mechanicmanager-mechevent-i-sys.md) | Definition of Mechanic device event. |
| [MoveParams](arkts-mechanic-mechanicmanager-moveparams-i-sys.md) | Parameters for moving the target. |
| [RotationAngles](arkts-mechanic-mechanicmanager-rotationangles-i-sys.md) | The rotion angles, relative to the current position. |
| [RotationAxesStateChangeInfo](arkts-mechanic-mechanicmanager-rotationaxesstatechangeinfo-i-sys.md) | Rotation axes state change information. |
| [RotationAxesStatus](arkts-mechanic-mechanicmanager-rotationaxesstatus-i-sys.md) | Rotation axes status |
| [RotationLimits](arkts-mechanic-mechanicmanager-rotationlimits-i-sys.md) | Rotation angle limits relative to the reference point. |
| [RotationSpeed](arkts-mechanic-mechanicmanager-rotationspeed-i-sys.md) | Rotational speed. A negative value indicates a clockwise rotation, and a positive value indicates a counterclockwise rotation. |
| [SearchParams](arkts-mechanic-mechanicmanager-searchparams-i-sys.md) | Parameters for target searching. |
| [SearchResult](arkts-mechanic-mechanicmanager-searchresult-i-sys.md) | Search result. |
| [SpeedParams](arkts-mechanic-mechanicmanager-speedparams-i-sys.md) | Parameters for moving or turning at a speed. |
| [TargetInfo](arkts-mechanic-mechanicmanager-targetinfo-i-sys.md) | Target information. |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AttachState](arkts-mechanic-mechanicmanager-attachstate-e.md) | Device attach states. |
| [CameraTrackingLayout](arkts-mechanic-mechanicmanager-cameratrackinglayout-e.md) | Enumerates the camera tracking layouts. |
| [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e.md) | Enumerates the mechanical device types. |
| [TrackingEvent](arkts-mechanic-mechanicmanager-trackingevent-e.md) | Enumerates the tracking events. |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionType](arkts-mechanic-mechanicmanager-actiontype-e-sys.md) | Type of action sequence. |
| [MarchingMode](arkts-mechanic-mechanicmanager-marchingmode-e-sys.md) | Marching mode definition. |
| [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e-sys.md) | Enumerates the mechanical device types. |
| [MechEventType](arkts-mechanic-mechanicmanager-mecheventtype-e-sys.md) | Mechanic event definition. |
| [Operation](arkts-mechanic-mechanicmanager-operation-e-sys.md) | Enumerates the user operations. |
| [Result](arkts-mechanic-mechanicmanager-result-e-sys.md) | Rotation execution results. |
| [RotationAxisLimited](arkts-mechanic-mechanicmanager-rotationaxislimited-e-sys.md) | Enumerates the rotation axis limit states. |
| [SearchDirection](arkts-mechanic-mechanicmanager-searchdirection-e-sys.md) | Search direction. |
| [SpeedGear](arkts-mechanic-mechanicmanager-speedgear-e-sys.md) | Speed gear definition. |
| [TargetType](arkts-mechanic-mechanicmanager-targettype-e-sys.md) | Target type. |
<!--DelEnd-->

