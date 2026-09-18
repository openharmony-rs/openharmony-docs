# @ohos.rpc(RPC)

The **RPC** module implements communication between processes, including inter-process communication (IPC) on a single device and remote procedure call (RPC) between processes on difference devices. IPC is implemented based on the Binder driver, and RPC is based on the DSoftBus driver.

This module supports return of error codes since API version 9.

**Since:** 7

**System capability:** SystemCapability.Communication.IPC.Core

## Modules to Import

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Ashmem](arkts-ipc-rpc-ashmem-c.md) | Provides methods related to anonymous shared memory objects, including creating, closing, mapping, and unmapping an **Ashmem** object, reading data from and writing data to an **Ashmem** object, obtaining the **Ashmem** size, and setting **Ashmem** protection. The shared memory applies only to cross-process communication within the local device. |
| [CallingInfo](arkts-ipc-rpc-callinginfo-c.md) | Defines the IPC context, including the PID and UID, local and remote device IDs, and whether the API is invoked on the same device. |
| [IPCSkeleton](arkts-ipc-rpc-ipcskeleton-c.md) | Obtains IPC context, including the UID and PID, local and remote device IDs, and whether the method is invoked on the same device. |
| [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md) | Provides methods to query of obtain interface descriptors, add or delete death notifications, dump object status to specific files, and send messages. |
| [MessageOption](arkts-ipc-rpc-messageoption-c.md) | Defines the options used to construct the **MessageOption** object. |
| [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | Provides APIs for reading and writing data in specific format. During RPC, the sender can use the **write()** method provided by **MessageParcel** to write data in specific format to a **MessageParcel** object. The receiver can use the **read()** method provided by **MessageParcel** to read data in specific format from a **MessageParcel** object. The data formats include basic data types and arrays, IPC objects, interface tokens, and custom sequenceable objects. |
| [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | Provides APIs for reading and writing data in specific format. During RPC or IPC, the sender can use the **write()** method provided by **MessageSequence** to write data in specific format to a **MessageSequence** object. The receiver can use the **read()** method provided by **MessageSequence** to read data in specific format from a **MessageSequence** object. The data formats include basic data types and arrays, IPC objects, interface tokens, and custom sequenceable objects. |
| [RemoteObject](arkts-ipc-rpc-remoteobject-c.md) | Provides methods to implement **RemoteObject**. The service provider must inherit from this class. |
| [RemoteProxy](arkts-ipc-rpc-remoteproxy-c.md) | Provides APIs to implement **IRemoteObject**. |

### Interfaces

| Name | Description |
| --- | --- |
| [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | Subscribes to death notifications of a remote object. When the remote object is dead, the local end will receive a notification and **[onRemoteDied](arkts-ipc-rpc-deathrecipient-i.md#onremotedied)** will be called. A remote object is dead when the process holding the object is terminated or the device of the remote object is shut down or restarted. If the local and remote objects belong to different devices, the remote object is dead when the device holding the remote object is detached from the network. |
| [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | Represents the holder of a remote proxy object. It is used to obtain a proxy object. |
| [Parcelable](arkts-ipc-rpc-parcelable-i.md) | Writes an object to a **MessageSequence** and reads it from the **MessageSequence** during IPC. |
| [RequestResult](arkts-ipc-rpc-requestresult-i.md) | Defines the response to the request. |
| [SendRequestResult](arkts-ipc-rpc-sendrequestresult-i.md) | Defines the response to the request. |
| [Sequenceable](arkts-ipc-rpc-sequenceable-i.md) | Writes objects of classes to a **MessageParcel** and reads them from the **MessageParcel** during IPC. |

### Enums

| Name | Description |
| --- | --- |
| [ErrorCode](arkts-ipc-rpc-errorcode-e.md) | The APIs of this module return exceptions since API version 9. The following table lists the error codes. |
| [TypeCode](arkts-ipc-rpc-typecode-e.md) | Since API version 12, [writeArrayBuffer](arkts-ipc-rpc-messagesequence-c.md#writearraybuffer) and [readArrayBuffer](arkts-ipc-rpc-messagesequence-c.md#readarraybuffer) are added to pass ArrayBuffer data. The specific TypedArray type is determined by the **TypeCode** defined as follows: |
