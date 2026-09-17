# @ohos.cooperate

The **cooperate** module implements screen hopping for two or more networked devices to share the keyboard and mouse for collaborative operations.

**Since:** 10

**System capability:** SystemCapability.Msdp.DeviceStatus.Cooperate

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [activate](arkts-distributedservice-cooperate-activate-f-sys.md) | Starts screen hopping. This API uses an asynchronous callback to return the result. |
| [activate](arkts-distributedservice-cooperate-activate-f-sys.md) | Starts screen hopping. This API uses a promise to return the result. |
| [activateCooperate](arkts-distributedservice-cooperate-activatecooperate-f-sys.md) | Starts screen hopping. This API uses an asynchronous callback to return the result. |
| [activateCooperate](arkts-distributedservice-cooperate-activatecooperate-f-sys.md) | Starts screen hopping. This API uses a promise to return the result. |
| [activateCooperateWithOptions](arkts-distributedservice-cooperate-activatecooperatewithoptions-f-sys.md) | Starts screen hopping based on the specified options. This API uses a promise to return the result. |
| [deactivate](arkts-distributedservice-cooperate-deactivate-f-sys.md) | Stops screen hopping. This API uses an asynchronous callback to return the result. |
| [deactivate](arkts-distributedservice-cooperate-deactivate-f-sys.md) | Stops screen hopping. This API uses a promise to return the result. |
| [deactivateCooperate](arkts-distributedservice-cooperate-deactivatecooperate-f-sys.md) | Stops screen hopping. This API uses an asynchronous callback to return the result. |
| [deactivateCooperate](arkts-distributedservice-cooperate-deactivatecooperate-f-sys.md) | Stops screen hopping. This API uses a promise to return the result. |
| [getCooperateSwitchState](arkts-distributedservice-cooperate-getcooperateswitchstate-f-sys.md) | Obtains the screen hopping status of the target device. This API uses an asynchronous callback to return the result. |
| [getCooperateSwitchState](arkts-distributedservice-cooperate-getcooperateswitchstate-f-sys.md) | Obtains the screen hopping status of the target device. This API uses a promise to return the result. |
| [getCrossingSwitchState](arkts-distributedservice-cooperate-getcrossingswitchstate-f-sys.md) | Obtains the screen hopping status of the target device. This API uses an asynchronous callback to return the result. |
| [getCrossingSwitchState](arkts-distributedservice-cooperate-getcrossingswitchstate-f-sys.md) | Obtains the screen hopping status of the target device. This API uses a promise to return the result. |
| [off](arkts-distributedservice-cooperate-off-f-sys.md#offcooperate) | Disables listening for screen hopping status change events. |
| [off](arkts-distributedservice-cooperate-off-f-sys.md#offcooperatemessage) | Disables listening for screen hopping status change events. |
| [off](arkts-distributedservice-cooperate-off-f-sys.md#offcooperatemouse) | Unregisters the listener for the mouse cursor position of a device. |
| [on](arkts-distributedservice-cooperate-on-f-sys.md#oncooperate) | Enables listening for screen hopping status change events. |
| [on](arkts-distributedservice-cooperate-on-f-sys.md#oncooperatemessage) | Enables listening for screen hopping status change events. |
| [on](arkts-distributedservice-cooperate-on-f-sys.md#oncooperatemouse) | Registers a listener for the mouse cursor position of a device. |
| [prepare](arkts-distributedservice-cooperate-prepare-f-sys.md) | Prepares for screen hopping. This API uses an asynchronous callback to return the result. |
| [prepare](arkts-distributedservice-cooperate-prepare-f-sys.md) | Prepares for screen hopping. This API uses a promise to return the result. |
| [prepareCooperate](arkts-distributedservice-cooperate-preparecooperate-f-sys.md) | Prepares for screen hopping. This API uses an asynchronous callback to return the result. |
| [prepareCooperate](arkts-distributedservice-cooperate-preparecooperate-f-sys.md) | Prepares for screen hopping. This API uses a promise to return the result. |
| [unprepare](arkts-distributedservice-cooperate-unprepare-f-sys.md) | Cancels the preparation for screen hopping. This API uses an asynchronous callback to return the result. |
| [unprepare](arkts-distributedservice-cooperate-unprepare-f-sys.md) | Cancels the preparation for screen hopping. This API uses a promise to return the result. |
| [unprepareCooperate](arkts-distributedservice-cooperate-unpreparecooperate-f-sys.md) | Cancels the preparation for screen hopping. This API uses an asynchronous callback to return the result. |
| [unprepareCooperate](arkts-distributedservice-cooperate-unpreparecooperate-f-sys.md) | Cancels the preparation for screen hopping. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CooperateMessage](arkts-distributedservice-cooperate-cooperatemessage-i-sys.md) | Defines a screen hopping status change event. |
| [CooperateOptions](arkts-distributedservice-cooperate-cooperateoptions-i-sys.md) | Screen hopping options, such as the exit position. |
| [MouseLocation](arkts-distributedservice-cooperate-mouselocation-i-sys.md) | Defines the mouse pointer position for screen hopping. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [CooperateMsg](arkts-distributedservice-cooperate-cooperatemsg-e-sys.md) | Represents a screen hopping message notification. |
| [CooperateState](arkts-distributedservice-cooperate-cooperatestate-e-sys.md) | Enumerates the screen hopping states. |
<!--DelEnd-->
