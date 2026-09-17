# @ohos.distributedDeviceManager(Device Management)

The **distributedDeviceManager** module provides APIs for distributed device management. Applications can call the APIs to:

- Subscribe to or unsubscribe from device state changes.  
- Discover devices nearby.  
- Authenticate or deauthenticate a device.  
- Query the trusted device list.  
- Query local device information, including the device name, type, and ID.

**Since:** 10

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## Modules to Import

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createDeviceManager](arkts-distributedservice-distributeddevicemanager-createdevicemanager-f.md) | Creates a **DeviceManager** instance. The **DeviceManager** instance is the entry for invoking the APIs for distributed device management. It can be used to obtain information about trusted devices and local devices. |
| [releaseDeviceManager](arkts-distributedservice-distributeddevicemanager-releasedevicemanager-f.md) | Releases a **DeviceManager** instance that is no longer used. |

### Interfaces

| Name | Description |
| --- | --- |
| [DeviceBasicInfo](arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md) | Represents the basic information about a distributed device. |
| [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md) | Provides APIs to obtain information about trusted devices and local devices. Before calling any API in **DeviceManager**, you must use **createDeviceManager** to create a **DeviceManager** instance, for example, **dmInstance**. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DeviceIconInfo](arkts-distributedservice-distributeddevicemanager-deviceiconinfo-i-sys.md) | Defines the device icon information. |
| [DeviceIconInfoFilterOptions](arkts-distributedservice-distributeddevicemanager-deviceiconinfofilteroptions-i-sys.md) | Defines the device icon information filter options. |
| [DeviceIdentification](arkts-distributedservice-distributeddevicemanager-deviceidentification-i-sys.md) | Struct for distributed device identification. |
| [DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i-sys.md) | Provides APIs to obtain information about trusted devices and local devices. Before calling any API in **DeviceManager**, you must use **createDeviceManager** to create a **DeviceManager** instance, for example, **dmInstance**. |
| [DeviceProfileInfo](arkts-distributedservice-distributeddevicemanager-deviceprofileinfo-i-sys.md) | Defines the device profile information. |
| [DeviceProfileInfoFilterOptions](arkts-distributedservice-distributeddevicemanager-deviceprofileinfofilteroptions-i-sys.md) | Defines device profile information filter options. |
| [NetworkIdQueryFilter](arkts-distributedservice-distributeddevicemanager-networkidqueryfilter-i-sys.md) | Defines the network ID filter options. |
| [ServiceProfileInfo](arkts-distributedservice-distributeddevicemanager-serviceprofileinfo-i-sys.md) | Defines the service profile information. It is populated based on the data returned from the cloud. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [DeviceStateChange](arkts-distributedservice-distributeddevicemanager-devicestatechange-e.md) | Enumerates the device states. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [StrategyForHeartbeat](arkts-distributedservice-distributeddevicemanager-strategyforheartbeat-e-sys.md) | Defines the heartbeat broadcast policy. |
<!--DelEnd-->
