# RemoteDeviceDriver

```TypeScript
interface RemoteDeviceDriver
```

Represents information about a remote device driver.

**Since:** 11

<!--Device-deviceManager-interface RemoteDeviceDriver--><!--Device-deviceManager-interface RemoteDeviceDriver-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DriverDevelopmentKit';
```

## deviceId

```TypeScript
deviceId: number
```

ID of the peripheral device.

**Type:** number

**Since:** 11

<!--Device-RemoteDeviceDriver-deviceId: long--><!--Device-RemoteDeviceDriver-deviceId: long-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

## remote

```TypeScript
remote: rpc.IRemoteObject
```

Remote driver object.

**Type:** [rpc.IRemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-iremoteobject-c.md)

**Since:** 11

<!--Device-RemoteDeviceDriver-remote: rpc.IRemoteObject--><!--Device-RemoteDeviceDriver-remote: rpc.IRemoteObject-End-->

**System capability:** SystemCapability.Driver.ExternalDevice
