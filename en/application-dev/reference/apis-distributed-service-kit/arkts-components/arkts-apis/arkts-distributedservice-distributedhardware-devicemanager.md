# @ohos.distributedHardware.deviceManager(Device Management)

The APIs of this module are deprecated. You are advised to use [@ohos.distributedDeviceManager](arkts-distributedservice-distributeddevicemanager.md). The **deviceManager** module provides APIs for distributed device management. System applications can call the APIs to do the following:

- Subscribe to or unsubscribe from device state changes.  
- Discover devices nearby.  
- Authenticate or deauthenticate a device.  
- Query the trusted device list.  
- Query local device information, including the device name, type, and ID.  
- Publishes device information for discovery purposes.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [distributedDeviceManager](arkts-distributedservice-distributeddevicemanager.md)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DistributedServiceKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createDeviceManager](arkts-distributedservice-devicemanager-createdevicemanager-f-sys.md) | Creates a **DeviceManager** instance. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AuthInfo](arkts-distributedservice-devicemanager-authinfo-i-sys.md) | Defines authentication information. |
| [AuthParam](arkts-distributedservice-devicemanager-authparam-i-sys.md) | Defines the authentication parameters. |
| [DeviceInfo](arkts-distributedservice-devicemanager-deviceinfo-i-sys.md) | Defines device information. |
| [DeviceManager](arkts-distributedservice-devicemanager-devicemanager-i-sys.md) | Provides APIs to obtain information about trusted devices and local devices. Before calling any API in **DeviceManager**, you must use **createDeviceManager** to create a **DeviceManager** instance, for example, **dmInstance**. |
| [PublishInfo](arkts-distributedservice-devicemanager-publishinfo-i-sys.md) | Defines published device information. |
| [SubscribeInfo](arkts-distributedservice-devicemanager-subscribeinfo-i-sys.md) | Defines subscription information. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AuthForm](arkts-distributedservice-devicemanager-authform-e-sys.md) | Enumerates the device authentication types. |
| [DeviceStateChangeAction](arkts-distributedservice-devicemanager-devicestatechangeaction-e-sys.md) | Enumerates the device states. |
| [DeviceType](arkts-distributedservice-devicemanager-devicetype-e-sys.md) | Enumerates the device types. |
| [DiscoverMode](arkts-distributedservice-devicemanager-discovermode-e-sys.md) | Enumerates the device discovery modes. |
| [ExchangeFreq](arkts-distributedservice-devicemanager-exchangefreq-e-sys.md) | Enumerates the device discovery frequencies. |
| [ExchangeMedium](arkts-distributedservice-devicemanager-exchangemedium-e-sys.md) | Enumerates the media used for device discovery. |
| [SubscribeCap](arkts-distributedservice-devicemanager-subscribecap-e-sys.md) | Enumerates the discovery capabilities. |
<!--DelEnd-->
