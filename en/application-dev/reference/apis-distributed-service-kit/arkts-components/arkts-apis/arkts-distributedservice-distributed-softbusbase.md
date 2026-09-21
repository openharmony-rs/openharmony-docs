# @ohos.distributed.softbusBase(This module provides the capabilities for device perception.)

The **softbusBase** module provides APIs for device perception, including starting and stopping perception advertising, starting and stopping perception scanning, switching an advertiser to high frequency, and obtaining the list of discovered devices. With these APIs, a system application can carry a custom payload in perception advertising to wake up surrounding collaborative devices, and scan to discover surrounding perception devices.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getPerceptionDeviceList](arkts-distributedservice-softbusbase-getperceptiondevicelist-f-sys.md) | Obtains the list of devices discovered by perception scanning. Before calling this API, call [startPerceptionScan](arkts-distributedservice-softbusbase-startperceptionscan-f-sys.md) to start scanning. After the scanning is stopped by calling [stopPerceptionScan](arkts-distributedservice-softbusbase-stopperceptionscan-f-sys.md), the discovered device list is cleared. |
| [setPerceptionAdvHighFreq](arkts-distributedservice-softbusbase-setperceptionadvhighfreq-f-sys.md) | Switches an active perception advertiser to high frequency for 10 seconds. After the high-frequency period expires, the advertising automatically restores to the previous frequency. The custom payload can be updated at the same time. |
| [startPerceptionAdv](arkts-distributedservice-softbusbase-startperceptionadv-f-sys.md) | Starts perception advertising or updates the custom payload carried in the advertising of the current owner. After the advertising is started, surrounding devices that are scanning can discover the current device. |
| [startPerceptionScan](arkts-distributedservice-softbusbase-startperceptionscan-f-sys.md) | Starts perception scanning for the current owner. After the scanning is started, surrounding devices that are advertising can be discovered. The discovered devices can be obtained by calling [getPerceptionDeviceList](arkts-distributedservice-softbusbase-getperceptiondevicelist-f-sys.md). |
| [stopPerceptionAdv](arkts-distributedservice-softbusbase-stopperceptionadv-f-sys.md) | Stops perception advertising of the current owner. After the advertising is stopped, surrounding devices can no longer discover the current device through scanning. |
| [stopPerceptionScan](arkts-distributedservice-softbusbase-stopperceptionscan-f-sys.md) | Stops perception scanning and clears the discovered device list of the current owner. After the scanning is stopped, the previously discovered device list is cleared and can no longer be obtained by calling [getPerceptionDeviceList](arkts-distributedservice-softbusbase-getperceptiondevicelist-f-sys.md). |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [PerceptionDeviceInfo](arkts-distributedservice-softbusbase-perceptiondeviceinfo-i-sys.md) | Defines the device information discovered by perception scanning, including the device type, device ID, and custom data carried in the advertising. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [PerceptionCycle](arkts-distributedservice-softbusbase-perceptioncycle-e-sys.md) | Defines the keepalive cycle level for perception scanning. A higher level indicates a shorter keepalive cycle. |
| [PerceptionType](arkts-distributedservice-softbusbase-perceptiontype-e-sys.md) | Defines the perception service type. |
<!--DelEnd-->
