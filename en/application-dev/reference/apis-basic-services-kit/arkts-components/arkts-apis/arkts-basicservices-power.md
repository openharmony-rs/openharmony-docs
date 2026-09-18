# @ohos.power(Power Management)

The **power** module provides APIs for rebooting and shutting down the system, as well as querying the screen status. You can use these APIs to obtain the device activity status, power mode, and screen on/off status.

**Since:** 7

**System capability:** SystemCapability.PowerManager.PowerManager.Core

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getPowerMode](arkts-basicservices-power-getpowermode-f.md) | Obtains the power mode of this device. |
| [isActive](arkts-basicservices-power-isactive-f.md) | Checks whether the current device is active. |
| [isScreenOn](arkts-basicservices-power-isscreenon-f.md) | Checks the screen status of the current device. This API uses an asynchronous callback to return the result. |
| [isScreenOn](arkts-basicservices-power-isscreenon-f.md) | Checks the screen status of the current device. This API uses a promise to return the result. |
| [isStandby](arkts-basicservices-power-isstandby-f.md) | Checks whether the device is in standby mode. |
| [rebootDevice](arkts-basicservices-power-rebootdevice-f.md) | Restarts the system. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getPowerConfig](arkts-basicservices-power-getpowerconfig-f-sys.md) | Query the power configuration value for a given scene name. |
| [hibernate](arkts-basicservices-power-hibernate-f-sys.md) | Hibernates a device. |
| [reboot](arkts-basicservices-power-reboot-f-sys.md) | Reboots a device. |
| [refreshActivity](arkts-basicservices-power-refreshactivity-f-sys.md) | Refreshes the device activity status (for example, resetting the screen-off time). |
| [registerShutdownCallback](arkts-basicservices-power-registershutdowncallback-f-sys.md) | Registers a callback to be invoked when the device is shut down or rebooted. This API uses an asynchronous callback to return the result. |
| [setPowerConfig](arkts-basicservices-power-setpowerconfig-f-sys.md) | Update the power configuration value for a given scene name. |
| [setPowerKeyFilteringStrategy](arkts-basicservices-power-setpowerkeyfilteringstrategy-f-sys.md) | Sets the power key filtering strategy. After the power service subscribes to the power key event, this API is used to configure the processing mode of this event. |
| [setPowerMode](arkts-basicservices-power-setpowermode-f-sys.md) | Sets the power mode of a device. This API uses an asynchronous callback to return the result. |
| [setPowerMode](arkts-basicservices-power-setpowermode-f-sys.md) | Sets the power mode of a device. This API uses a promise to return the result. |
| [setScreenOffTime](arkts-basicservices-power-setscreenofftime-f-sys.md) | Sets the screen-off timeout duration, in unit of ms. |
| [shutdown](arkts-basicservices-power-shutdown-f-sys.md) | Shuts down the system. |
| [suspend](arkts-basicservices-power-suspend-f-sys.md) | Enables a device to enter the sleep state. |
| [unregisterShutdownCallback](arkts-basicservices-power-unregistershutdowncallback-f-sys.md) | Unregisters the callback to be invoked when the device is shut down or rebooted. This API uses a callback to return the result. |
| [wakeup](arkts-basicservices-power-wakeup-f-sys.md) | Wakes up a device. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | Enumerates power modes. |
| [PowerKeyFilteringStrategy](arkts-basicservices-power-powerkeyfilteringstrategy-e.md) | Enumerates the power key filtering strategies. |
