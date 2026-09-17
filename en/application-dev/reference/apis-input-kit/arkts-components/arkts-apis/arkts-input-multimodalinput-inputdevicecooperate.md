# @ohos.multimodalInput.inputDeviceCooperate(Screen Hopping)

The **inputDeviceCooperate** module implements screen hopping for two or more networked devices to share the keyboard and mouse for collaborative operations.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** [cooperate/cooperate](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate.md)

**System capability:** SystemCapability.MultimodalInput.Input.Cooperator

## Modules to Import

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [enable](arkts-input-inputdevicecooperate-enable-f-sys.md) | Enables or disables screen hopping. This API uses an asynchronous callback to return the result. |
| [enable](arkts-input-inputdevicecooperate-enable-f-sys.md) | Specifies whether to enable screen hopping. This API uses a promise to return the result. |
| [getState](arkts-input-inputdevicecooperate-getstate-f-sys.md) | Obtains the state of the screen hopping switch. This API uses an asynchronous callback to return the result. |
| [getState](arkts-input-inputdevicecooperate-getstate-f-sys.md) | Checks whether screen hopping is enabled. This API uses a promise to return the result. |
| [off](arkts-input-inputdevicecooperate-off-f-sys.md#offcooperation) | Deregisters the listener for screen hopping status changes. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputdevicecooperate-on-f-sys.md#oncooperation) | Registers a listener for screen hopping state changes. This API uses an asynchronous callback to return the result. |
| [start](arkts-input-inputdevicecooperate-start-f-sys.md) | Starts screen hopping. This API uses an asynchronous callback to return the result. |
| [start](arkts-input-inputdevicecooperate-start-f-sys.md) | Starts screen hopping. This API uses a promise to return the result. |
| [stop](arkts-input-inputdevicecooperate-stop-f-sys.md) | Stops screen hopping. This API uses an asynchronous callback to return the result. |
| [stop](arkts-input-inputdevicecooperate-stop-f-sys.md) | Stops screen hopping. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [EventMsg](arkts-input-inputdevicecooperate-eventmsg-e-sys.md) | Enumerates screen hopping events. |
<!--DelEnd-->
