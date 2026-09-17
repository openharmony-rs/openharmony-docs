# @ohos.distributedHardware.mechanicManager

Provides capabilities for controlling and interacting with mechanical devices connected to this device. The capabilities cover connection management, control, and monitoring.

@namespace mechanicManager

**Since:** 20

**System capability:** SystemCapability.Mechanic.Core

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAttachedMechDevices](arkts-mechanic-mechanicmanager-getattachedmechdevices-f.md) | Obtain the list of connected mechanical devices. |
| [getCameraTrackingEnabled](arkts-mechanic-mechanicmanager-getcameratrackingenabled-f.md) | Checks whether camera tracking is enabled for this mechanical device. |
| [getCameraTrackingLayout](arkts-mechanic-mechanicmanager-getcameratrackinglayout-f.md) | Obtains the camera tracking layout of this mechanical device. |
| [isControlSupported](arkts-mechanic-mechanicmanager-iscontrolsupported-f.md) | Checks whether the current device supports embodied control for a specific type of device. |
| [off](arkts-mechanic-mechanicmanager-off-f.md#offattachstatechange) | Unsubscribes from device attachment state change events. |
| [off](arkts-mechanic-mechanicmanager-off-f.md#offtrackingstatechange) | Unsubscribes from tracking events. |
| [on](arkts-mechanic-mechanicmanager-on-f.md#onattachstatechange) | Subscribes to device attachment state change events. |
| [on](arkts-mechanic-mechanicmanager-on-f.md#ontrackingstatechange) | Subscribes to tracking events. |
| [setCameraTrackingEnabled](arkts-mechanic-mechanicmanager-setcameratrackingenabled-f.md) | Enables or disables camera tracking. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [connectDevice](arkts-mechanic-mechanicmanager-connectdevice-f-sys.md) | Connecting devices based on addresses |
| [disconnectDevice](arkts-mechanic-mechanicmanager-disconnectdevice-f-sys.md) | Disconnect a device with mechanic id. |
| [doAction](arkts-mechanic-mechanicmanager-doaction-f-sys.md) | Execute an action sequence. |
| [getCurrentAngles](arkts-mechanic-mechanicmanager-getcurrentangles-f-sys.md) | Obtains the current angles of a mechanical device. |
| [getDeviceAdsorbState](arkts-mechanic-mechanicmanager-getdeviceadsorbstate-f-sys.md) | Obtains the adsorb state of a device. Before calling this method, ensure that the device is connected. |
| [getMaxRotationSpeed](arkts-mechanic-mechanicmanager-getmaxrotationspeed-f-sys.md) | Obtains the maximum rotation speed of a mechanical device. |
| [getMaxRotationTime](arkts-mechanic-mechanicmanager-getmaxrotationtime-f-sys.md) | Obtains the maximum continuous rotation duration of a mechanical device. |
| [getRotationAxesStatus](arkts-mechanic-mechanicmanager-getrotationaxesstatus-f-sys.md) | Obtains the status of the rotation axes. |
| [getRotationLimits](arkts-mechanic-mechanicmanager-getrotationlimits-f-sys.md) | Obtains the maximum rotation angles relative to the reference point for the specified mechanical device. |
| [isSupportAction](arkts-mechanic-mechanicmanager-issupportaction-f-sys.md) | Check whether the specific action type is supported. |
| [move](arkts-mechanic-mechanicmanager-move-f-sys.md) | Move a mechanical device with the specified parameters. |
| [moveBySpeed](arkts-mechanic-mechanicmanager-movebyspeed-f-sys.md) | Move a mechanical device at the specified speed. |
| [off](arkts-mechanic-mechanicmanager-off-f-sys.md#offrotationaxesstatuschange) | Unregister a listener for axis state changes. |
| [offBatteryLevelChange](arkts-mechanic-mechanicmanager-offbatterylevelchange-f-sys.md) | Unsubscribes to device battery level change information. |
| [on](arkts-mechanic-mechanicmanager-on-f-sys.md#onrotationaxesstatuschange) | Register a listener for axis state changes. The status of the rotation axis changes dynamically, which needs to be monitored. |
| [onBatteryLevelChange](arkts-mechanic-mechanicmanager-onbatterylevelchange-f-sys.md) | Subscribes to device battery level change information. Before calling this method, ensure that the device is connected. |
| [rotate](arkts-mechanic-mechanicmanager-rotate-f-sys.md) | Rotates a mechanical device to the relative angles. |
| [rotateBySpeed](arkts-mechanic-mechanicmanager-rotatebyspeed-f-sys.md) | Rotates a mechanical device at the specified speed. |
| [rotateToEulerAngles](arkts-mechanic-mechanicmanager-rotatetoeulerangles-f-sys.md) | Rotates a mechanical device to the absolute angles. |
| [searchTarget](arkts-mechanic-mechanicmanager-searchtarget-f-sys.md) | Searching for a specified target. |
| [setCameraTrackingLayout](arkts-mechanic-mechanicmanager-setcameratrackinglayout-f-sys.md) | Sets the camera tracking layout for this mechanical device. |
| [setUserOperation](arkts-mechanic-mechanicmanager-setuseroperation-f-sys.md) | Sets a user operation. |
| [stopMoving](arkts-mechanic-mechanicmanager-stopmoving-f-sys.md) | Stops a mechanical device from moving. |
| [subscribe](arkts-mechanic-mechanicmanager-subscribe-f-sys.md) | Subscribe to the specified events. |
| [turnBySpeed](arkts-mechanic-mechanicmanager-turnbyspeed-f-sys.md) | Rotate in place according to the speed. |
| [unSubscribe](arkts-mechanic-mechanicmanager-unsubscribe-f-sys.md) | Unsubscribes the specified events. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AttachStateChangeInfo](arkts-mechanic-mechanicmanager-attachstatechangeinfo-i.md) | Callback information about the device attachment state change. @typedef AttachStateChangeInfo |
| [MechInfo](arkts-mechanic-mechanicmanager-mechinfo-i.md) | Mechanical device information. @typedef MechInfo |
| [TrackingEventInfo](arkts-mechanic-mechanicmanager-trackingeventinfo-i.md) | Tracking event callback info. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AddressInfo](arkts-mechanic-mechanicmanager-addressinfo-i-sys.md) | Definition of device adress information. |
| [BatteryLevelInfo](arkts-mechanic-mechanicmanager-batterylevelinfo-i-sys.md) | Definition of battery level information. |
| [ConnectParam](arkts-mechanic-mechanicmanager-connectparam-i-sys.md) | Definition of connect parameter. |
| [EulerAngles](arkts-mechanic-mechanicmanager-eulerangles-i-sys.md) | Absolute euler angles relative to the home position. |
| [MechEvent](arkts-mechanic-mechanicmanager-mechevent-i-sys.md) | Definition of Mechanic device event. |
| [MoveParams](arkts-mechanic-mechanicmanager-moveparams-i-sys.md) | Parameters for moving the target. |
| [RotationAngles](arkts-mechanic-mechanicmanager-rotationangles-i-sys.md) | The rotion angles, relative to the current position. @typedef RotationAngles |
| [RotationAxesStateChangeInfo](arkts-mechanic-mechanicmanager-rotationaxesstatechangeinfo-i-sys.md) | Rotation axes state change information. @typedef RotationAxesStateChangeInfo |
| [RotationAxesStatus](arkts-mechanic-mechanicmanager-rotationaxesstatus-i-sys.md) | Rotation axes status |
| [RotationLimits](arkts-mechanic-mechanicmanager-rotationlimits-i-sys.md) | Rotation angle limits relative to the reference point. @typedef RotationLimits |
| [RotationSpeed](arkts-mechanic-mechanicmanager-rotationspeed-i-sys.md) | Rotational speed. A negative value indicates a clockwise rotation, and a positive value indicates a counterclockwise rotation. @typedef RotationSpeed |
| [SearchParams](arkts-mechanic-mechanicmanager-searchparams-i-sys.md) | Parameters for target searching. |
| [SearchResult](arkts-mechanic-mechanicmanager-searchresult-i-sys.md) | Search result. |
| [SpeedParams](arkts-mechanic-mechanicmanager-speedparams-i-sys.md) | Parameters for moving or turning at a speed. |
| [TargetInfo](arkts-mechanic-mechanicmanager-targetinfo-i-sys.md) | Target information. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AttachState](arkts-mechanic-mechanicmanager-attachstate-e.md) | Device attach states. |
| [CameraTrackingLayout](arkts-mechanic-mechanicmanager-cameratrackinglayout-e.md) | Enumerates the camera tracking layouts. @enum { int } |
| [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e.md) | Enumerates the mechanical device types. @enum { int } |
| [TrackingEvent](arkts-mechanic-mechanicmanager-trackingevent-e.md) | Enumerates the tracking events. @enum { int } |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ActionType](arkts-mechanic-mechanicmanager-actiontype-e-sys.md) | Type of action sequence. |
| [AddressType](arkts-mechanic-mechanicmanager-addresstype-e-sys.md) | Mechanic device address type. |
| [AdsorbState](arkts-mechanic-mechanicmanager-adsorbstate-e-sys.md) | Mechanic device state. The state indicates whether the device is adsorbed or unadsorbed. |
| [MarchingMode](arkts-mechanic-mechanicmanager-marchingmode-e-sys.md) | Marching mode definition. |
| [MechDeviceType](arkts-mechanic-mechanicmanager-mechdevicetype-e-sys.md) | Enumerates the mechanical device types. @enum { int } |
| [MechEventType](arkts-mechanic-mechanicmanager-mecheventtype-e-sys.md) | Mechanic event definition. |
| [Operation](arkts-mechanic-mechanicmanager-operation-e-sys.md) | Enumerates the user operations. @enum { int } |
| [Result](arkts-mechanic-mechanicmanager-result-e-sys.md) | Rotation execution results. |
| [RotationAxisLimited](arkts-mechanic-mechanicmanager-rotationaxislimited-e-sys.md) | Enumerates the rotation axis limit states. @enum { int } |
| [SearchDirection](arkts-mechanic-mechanicmanager-searchdirection-e-sys.md) | Search direction. |
| [SpeedGear](arkts-mechanic-mechanicmanager-speedgear-e-sys.md) | Speed gear definition. |
| [TargetType](arkts-mechanic-mechanicmanager-targettype-e-sys.md) | Target type. |
<!--DelEnd-->
