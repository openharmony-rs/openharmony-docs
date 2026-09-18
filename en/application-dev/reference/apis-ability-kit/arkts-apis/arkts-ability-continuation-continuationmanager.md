# @ohos.continuation.continuationManager

The continuationManager module provides the continuation/collaboration management entry. You can use the APIs of this module to connect to and cancel the continuation/collaboration management service, subscribe to and unsubscribe from device connection events, start the device selection module, and update the device connection state.

**Since:** 8

**Deprecated since:** 22

**Substitutes:** [distributedDeviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager.md)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.DistributedAbilityManager

## Modules to Import

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [off](arkts-ability-continuationmanager-off-f.md#offdeviceselected) | Unsubscribes from device connection events. |
| [off](arkts-ability-continuationmanager-off-f.md#offdeviceunselected) | Unsubscribes from device disconnection events. |
| [off](arkts-ability-continuationmanager-off-f.md#offdeviceconnect) | Unsubscribes from device connection events. This API uses an asynchronous callback to return the result. |
| [off](arkts-ability-continuationmanager-off-f.md#offdevicedisconnect) | Unsubscribes from device disconnection events. This API uses an asynchronous callback to return the result. |
| [on](arkts-ability-continuationmanager-on-f.md#ondeviceselected) | Subscribes to device connection events. This API uses an asynchronous callback to return the result. |
| [on](arkts-ability-continuationmanager-on-f.md#ondeviceunselected) | Subscribes to device disconnection events. This API uses an asynchronous callback to return the result. |
| [on](arkts-ability-continuationmanager-on-f.md#ondeviceconnect) | Subscribes to device connection events. This API uses an asynchronous callback to return the result. |
| [on](arkts-ability-continuationmanager-on-f.md#ondevicedisconnect) | Subscribes to device disconnection events. This API uses an asynchronous callback to return the result. |
| [register](arkts-ability-continuationmanager-register-f.md) | Registers the continuation management service and obtains a token. This API does not involve any filter parameters and uses an asynchronous callback to return the result. |
| [register](arkts-ability-continuationmanager-register-f.md) | Registers the continuation management service and obtains a token. This API uses an asynchronous callback to return the result. |
| [register](arkts-ability-continuationmanager-register-f.md) | Registers the continuation management service and obtains a token. This API uses a promise to return the result. |
| [registerContinuation](arkts-ability-continuationmanager-registercontinuation-f.md) | Registers the continuation management service and obtains a token. This API does not involve any filter parameters and uses an asynchronous callback to return the result. |
| [registerContinuation](arkts-ability-continuationmanager-registercontinuation-f.md) | Registers the continuation management service and obtains a token. This API uses an asynchronous callback to return the result. |
| [registerContinuation](arkts-ability-continuationmanager-registercontinuation-f.md) | Registers the continuation management service and obtains a token. This API uses a promise to return the result. |
| [startContinuationDeviceManager](arkts-ability-continuationmanager-startcontinuationdevicemanager-f.md) | Starts the device selection module to show the list of available devices on the network. This API does not involve any filter parameters and uses an asynchronous callback to return the result. |
| [startContinuationDeviceManager](arkts-ability-continuationmanager-startcontinuationdevicemanager-f.md) | Starts the device selection module to show the list of available devices on the network. This API uses an asynchronous callback to return the result. |
| [startContinuationDeviceManager](arkts-ability-continuationmanager-startcontinuationdevicemanager-f.md) | Starts the device selection module to show the list of available devices on the network. This API uses a promise to return the result. |
| [startDeviceManager](arkts-ability-continuationmanager-startdevicemanager-f.md) | Starts the device selection module to show the list of available devices on the network. This API does not involve any filter parameters and uses an asynchronous callback to return the result. |
| [startDeviceManager](arkts-ability-continuationmanager-startdevicemanager-f.md) | Starts the device selection module to show the list of available devices on the network. This API uses an asynchronous callback to return the result. |
| [startDeviceManager](arkts-ability-continuationmanager-startdevicemanager-f.md) | Starts the device selection module to show the list of available devices on the network. This API uses a promise to return the result. |
| [unregister](arkts-ability-continuationmanager-unregister-f.md) | Unregisters the continuation management service. This API uses an asynchronous callback to return the result. |
| [unregister](arkts-ability-continuationmanager-unregister-f.md) | Unregisters the continuation management service. This API uses a promise to return the result. |
| [unregisterContinuation](arkts-ability-continuationmanager-unregistercontinuation-f.md) | Unregisters the continuation management service. This API uses an asynchronous callback to return the result. |
| [unregisterContinuation](arkts-ability-continuationmanager-unregistercontinuation-f.md) | Unregisters the continuation management service. This API uses a promise to return the result. |
| [updateConnectStatus](arkts-ability-continuationmanager-updateconnectstatus-f.md) | Instructs the device selection module to update the device connection state. This API uses an asynchronous callback to return the result. |
| [updateConnectStatus](arkts-ability-continuationmanager-updateconnectstatus-f.md) | Instructs the device selection module to update the device connection state. This API uses a promise to return the result. |
| [updateContinuationState](arkts-ability-continuationmanager-updatecontinuationstate-f.md) | Instructs the device selection module to update the device connection state. This API uses an asynchronous callback to return the result. |
| [updateContinuationState](arkts-ability-continuationmanager-updatecontinuationstate-f.md) | Instructs the device selection module to update the device connection state. This API uses a promise to return the result. |

### Enums

| Name | Description |
| --- | --- |
| [ContinuationMode](arkts-ability-continuationmanager-continuationmode-e.md) | Enumerates the continuation modes provided by the device selection module. |
| [DeviceConnectState](arkts-ability-continuationmanager-deviceconnectstate-e.md) | Device connection state. |

### Types

| Name | Description |
| --- | --- |
| [ContinuationExtraParams](arkts-ability-continuationmanager-continuationextraparams-t.md) | Defines the extra parameters required by the device selection module in the continuation management entry. |
| [ContinuationResult](arkts-ability-continuationmanager-continuationresult-t.md) | Defines the device information returned by the continuation management entry. |
