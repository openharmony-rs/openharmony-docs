# @ohos.distributedsched.linkEnhance(Enhanced Connection)

The **linkEnhance** module delivers highly efficient Bluetooth connectivity and data transmission capabilities, significantly enhancing the cross-device connection stability. By employing a multi-channel merging algorithm, it addresses issues such as unstable connections and limited number of connections of classic Bluetooth. This enhances cross-device data transmission capabilities and improves user experience.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createConnection](arkts-distributedservice-linkenhance-createconnection-f.md) | Creates a **Connection** object on the device that functions as the client. After the **Connection** object is created, subscribe to **on('connectResult')** and call **connect()** to initiate a connection request to the server. After the connection is successful, call **sendData()** to send data. If the connection is not required, call **close()** to destroy the **Connection** object to release resources. |
| [createServer](arkts-distributedservice-linkenhance-createserver-f.md) | Creates a **Server** object. After **start()** is called, the device can be connected to other devices as a server. After using the object, call **close()** to destroy the **Server** object to release resources. To use the object again, you need to create another **Server** object. |

### Interfaces

| Name | Description |
| --- | --- |
| [Connection](arkts-distributedservice-linkenhance-connection-i.md) | Represents a **Connection** object, which provides methods for connecting to and disconnecting from a peer device, obtaining the device's ID, sending data, and registering or unregistering event callbacks. |
| [ConnectResult](arkts-distributedservice-linkenhance-connectresult-i.md) | Represents the connection result, which is returned after the client calls **connect()**. |
| [Server](arkts-distributedservice-linkenhance-server-i.md) | Represents a **Server** object, which provides methods for starting, stopping, and closing the server, and registering or unregistering event callbacks. |
