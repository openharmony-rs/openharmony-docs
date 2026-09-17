# @ohos.bluetooth.bas

Provide methods to access BAS(Battery Service)-related capabilities.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { bas } from '@kit.ConnectivityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getRemoteDeviceBatteryInfo](arkts-connectivity-bas-getremotedevicebatteryinfo-f-sys.md) | Get remote device battery information. |
| [isBasSupported](arkts-connectivity-bas-isbassupported-f-sys.md) | Determine whether the local device can obtain the battery level of the remote device. |
| [offBatteryChange](arkts-connectivity-bas-offbatterychange-f-sys.md) | Unsubscribe the event of battery state changes from a remote device. |
| [onBatteryChange](arkts-connectivity-bas-onbatterychange-f-sys.md) | Subscribe the event of battery state changed from a remote device. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BatteryInfo](arkts-connectivity-bas-batteryinfo-i-sys.md) | Describe the contents of the battery information. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [BluetoothAddress](arkts-connectivity-bas-bluetoothaddress-t-sys.md) | Bluetooth device address. |
<!--DelEnd-->
