# @ohos.distributed.softbusBase (Device Awareness) (System API)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @Lucky-M-->
<!--Designer: @Lucky-M-->
<!--Tester: @openharmony_ci-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=8daeb7b1665bdb6abe169e7157c1f05b9834aff4 translatedAt=2026-11-03T11:10:57.627Z pushedAt=2026-11-03T12:26:31.880Z nl=1 -->

This module provides device awareness capabilities, including starting and stopping perception advertisement, high-frequency switching, starting and stopping awareness scan, and querying the discovered device list. System applications can wake up surrounding collaborative devices through custom data advertisement and discover surrounding awareness devices through scanning, which is suitable for low-power and efficient collaborative wakeup and discovery scenarios between near-field devices.

**Since:** 26.0.1

> **NOTE**
>
> The APIs provided by this module are system APIs and can be used only in the stage model.

## Modules to Import

``` TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
```

## PerceptionType

Enumerates the awareness service types.

**Since:** 26.0.1

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| PERCEPTION_TYPE_COLLABORATIVE_WAKE | 0 | Collaborative wakeup. The awareness advertisement or scan of this type is used for cross-device collaborative wakeup. |

## PerceptionCycle

Enumerates the keepalive period levels of an awareness scan. The keepalive period refers to the duration after which a device is removed from the discovered device list if no advertisement from that device is received by the scanning end within the specified duration. A higher level indicates a shorter keepalive period.

**Since:** 26.0.1

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| PERCEPTION_CYCLE_LOW | 0 | Low level. The keepalive period is 150 seconds, that is, a device is removed from the discovered device list if no advertisement from that device is received within 150 seconds. |
| PERCEPTION_CYCLE_MEDIUM | 1 | Medium level. The keepalive period is 75 seconds, that is, a device is removed from the discovered device list if no advertisement from that device is received within 75 seconds. |
| PERCEPTION_CYCLE_HIGH | 2 | High level. The keepalive period is 30 seconds, that is, a device is removed from the discovered device list if no advertisement from that device is received within 30 seconds. |

## PerceptionDeviceInfo

Device information discovered by an Awareness Scan, including the device type, device ID, and custom data carried in the broadcast.

**Since:** 26.0.1

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | ---- | ---- | -------- |
| deviceType | number | No | No | Device type ID, which indicates the device type. The value is an integer, for example, **0x0E** is the mobile phone ID, **0x11** is the tablet ID, **0x9C** is the TV ID, and **0x0C** is the PC ID. The specific value is subject to the system definition. |
| deviceId | ArrayBuffer | No | No | Device ID, which is binary data in network byte order (big-endian) with a maximum length of 6 bytes. |
| customData | ArrayBuffer | No | No | Custom data carried in the broadcast. Its length is the same as that of the custom data carried in the broadcast of the discovered device, with a maximum length of 5 bytes. |

## softbusBase.startPerceptionAdv

startPerceptionAdv(type:&nbsp;[PerceptionType](#perceptiontype), customData?:&nbsp;ArrayBuffer):&nbsp;Promise&lt;void&gt;

Starts perception advertisement or updates the custom data of the current owner (the application that currently holds the awareness service). After the advertisement is started, nearby scanning devices can discover this device. This API is applicable to near-field device collaboration scenarios such as cross-device collaborative wakeup. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Required permissions**: ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Communication.SoftBus.Core

**Device behavior differences**: This API can be properly called on devices other than wearables and 2-in-1 devices that do not support distributed services. If it is called on wearables or 2-in-1 devices, error code 801 is returned.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | Yes | Awareness service type. |
| customData | ArrayBuffer | No | Custom data carried in the advertisement. The data structure is defined by the application-layer protocol. The maximum length is 5 bytes. If the length exceeds 5 bytes, an error is thrown. If this parameter is not set, an empty ArrayBuffer is used by default. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Awareness Error Codes](errorcode-softbusBase.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**Example**

``` TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Custom data (≤5 bytes)
  let customData: ArrayBuffer = new ArrayBuffer(2);
  let view = new Uint8Array(customData);
  view[0] = 0x01;
  view[1] = 0x02;
  softbusBase.startPerceptionAdv(softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE, customData)
    .then(() => {
      console.info('startPerceptionAdv success');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to startPerceptionAdv. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
  const error: BusinessError = err as BusinessError;
  console.error(`Failed to startPerceptionAdv. Code: ${error.code}, message: ${error.message}`);
}
```

## softbusBase.setPerceptionAdvHighFreq

setPerceptionAdvHighFreq(type:&nbsp;[PerceptionType](#perceptiontype), customData?:&nbsp;ArrayBuffer):&nbsp;Promise&lt;void&gt;

Switches the active perception advertisement to high frequency for 10 seconds, after which it automatically restores the original frequency band. The custom data can be updated at the same time during the switch. Typical use case: when a device needs to be quickly discovered by nearby scanning devices (for example, first-time pairing or a collaborative wakeup response), it can temporarily switch to high-frequency advertisement to reduce the discovery latency. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Communication.SoftBus.Core

**Device behavior differences**: This API returns error code 801 on wearables and 2-in-1 devices that do not support distributed services, and can be properly called on other devices.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | Yes | Type of the awareness service. |
| customData | ArrayBuffer | No | Custom data carried in the advertisement. The data structure is defined by the application-layer protocol. The maximum length is 5 bytes; exceeding this limit throws an error. If not specified, an empty ArrayBuffer is used by default. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Awareness Error Codes](errorcode-softbusBase.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**Example**

``` TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let customData: ArrayBuffer = new ArrayBuffer(1);
  new Uint8Array(customData)[0] = 0x03;
  softbusBase.setPerceptionAdvHighFreq(softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE, customData)
    .then(() => {
      console.info('setPerceptionAdvHighFreq success');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to setPerceptionAdvHighFreq. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
  const error: BusinessError = err as BusinessError;
  console.error(`Failed to setPerceptionAdvHighFreq. Code: ${error.code}, message: ${error.message}`);
}
```

## softbusBase.stopPerceptionAdv

stopPerceptionAdv(type:&nbsp;[PerceptionType](#perceptiontype)):&nbsp;Promise&lt;void&gt;

Stops the perception advertisement of the current owner. After the advertisement stops, nearby scanning devices can no longer discover this device. This API uses a promise to return the result.

**Since:** 26.0.1

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Communication.SoftBus.Core

**Device behavior differences**: This API returns error code 801 on Wearable/2in1 devices that do not support distributed services, and can be properly called on other devices.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | Yes | Awareness Service type. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Awareness Error Codes](errorcode-softbusBase.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**Example**

``` TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  softbusBase.stopPerceptionAdv(softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE)
    .then(() => {
      console.info('stopPerceptionAdv success');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to stopPerceptionAdv. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
  const error: BusinessError = err as BusinessError;
  console.error(`Failed to stopPerceptionAdv. Code: ${error.code}, message: ${error.message}`);
}
```

## softbusBase.startPerceptionScan

startPerceptionScan(type:&nbsp;[PerceptionType](#perceptiontype), cycle:&nbsp;[PerceptionCycle](#perceptioncycle)):&nbsp;Promise&lt;void&gt;

Starts the awareness scan of the current owner with the specified keepalive period. After the scan is started, nearby advertising devices can be discovered, and the discovered devices can be obtained through [getPerceptionDeviceList](#softbusbasegetperceptiondevicelist). This API is applicable to scenarios such as nearby device discovery and collaborative wakeup. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Communication.SoftBus.Core

**Device Behavior Difference:** This API can be called normally on Phone/Tablet/some 2-in-1 devices that support sensorhub in hardware. Calling this API on other devices returns error code 801.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | Yes | Type of the awareness service. |
| cycle | [PerceptionCycle](#perceptioncycle) | Yes | Keepalive period level, that is, the timeout level for how long a device is removed from the device list after its advertisement is not received. A higher level indicates a shorter keepalive period. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Awareness Error Codes](errorcode-softbusBase.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**Example**

``` TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  softbusBase.startPerceptionScan(
    softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE,
    softbusBase.PerceptionCycle.PERCEPTION_CYCLE_MEDIUM)
    .then(() => {
      console.info('startPerceptionScan success');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to startPerceptionScan. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
  const error: BusinessError = err as BusinessError;
  console.error(`Failed to startPerceptionScan. Code: ${error.code}, message: ${error.message}`);
}
```

## softbusBase.stopPerceptionScan

stopPerceptionScan(type:&nbsp;[PerceptionType](#perceptiontype)):&nbsp;Promise&lt;void&gt;

Stops the awareness scan and clears the discovered device list of the current owner. After the scan stops, the device list can no longer be obtained through [getPerceptionDeviceList](#softbusbasegetperceptiondevicelist). This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Required permissions**: ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Communication.SoftBus.Core

**Device Behavior**: This API can be called normally on Phone/Tablet/some 2-in-1 devices whose hardware supports sensorhub. Calling this API on other devices returns error code 801.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | Yes | Awareness service type. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Awareness Error Codes](errorcode-softbusBase.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**Example**

``` TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  softbusBase.stopPerceptionScan(softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE)
    .then(() => {
      console.info('stopPerceptionScan success');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to stopPerceptionScan. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
  const error: BusinessError = err as BusinessError;
  console.error(`Failed to stopPerceptionScan. Code: ${error.code}, message: ${error.message}`);
}
```

## softbusBase.getPerceptionDeviceList

getPerceptionDeviceList(type:&nbsp;[PerceptionType](#perceptiontype)):&nbsp;Promise&lt;[PerceptionDeviceInfo](#perceptiondeviceinfo)[]&gt;

Obtains the device list discovered by the awareness scan. You must first call [startPerceptionScan](#softbusbasestartperceptionscan) to start the scan. After [stopPerceptionScan](#softbusbasestopperceptionscan) is called to stop the scan, the discovered device list is cleared. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Communication.SoftBus.Core

**Device Behavior Difference:** This API can be called normally on Phone/Tablet/some 2-in-1 devices that support sensorhub in hardware. Calling this API on other devices returns error code 801.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | Yes | Type of the awareness service. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[PerceptionDeviceInfo](#perceptiondeviceinfo)[]&gt; | Promise object that returns the device list discovered by the awareness scan. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Device Awareness Error Codes](errorcode-softbusBase.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000002 | Caller error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**Example**

``` TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  softbusBase.getPerceptionDeviceList(softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE)
    .then((devices: Array<softbusBase.PerceptionDeviceInfo>) => {
      console.info(`getPerceptionDeviceList success, count: ${devices.length}`);
      devices.forEach((device, idx) => {
        let idView = new Uint8Array(device.deviceId);
        let dataView = new Uint8Array(device.customData);
        console.info(`device[${idx}]: type=${device.deviceType}, idLen=${idView.length}, customDataLen=${dataView.length}`);
      });
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to getPerceptionDeviceList. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
  const error: BusinessError = err as BusinessError;
  console.error(`Failed to getPerceptionDeviceList. Code: ${error.code}, message: ${error.message}`);
}
```
