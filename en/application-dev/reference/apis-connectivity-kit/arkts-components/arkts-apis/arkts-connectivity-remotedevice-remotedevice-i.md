# RemoteDevice

Provides the method for operating on a remote device. Before using this method, you need to call [remoteDevice.createRemoteDevice](arkts-connectivity-remotedevice-createremotedevice-f.md) to create a [RemoteDevice](arkts-connectivity-remotedevice-remotedevice-i.md) instance. You need to create only one instance for a device.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## getAcbState

```TypeScript
getAcbState(): AcbState
```

Obtains the logical link connection status with a remote device. This method is applicable when you need to check whether a logical link is ready, for example, checking the logical link status before data transfer or message communication. Unlike [getConnectionState](#getconnectionstate) which obtains the connection status at the device level, this API obtains the connection status at the logical link (ACB) level.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| [AcbState](arkts-connectivity-remotedevice-acbstate-t.md) | Logical link connection state with a remote device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## getConnectionState

```TypeScript
getConnectionState(): ConnectionState
```

Obtains the connection status between the local and remote devices. Unlike [getAcbState](#getacbstate) which obtains the connection status at the logical link (ACB) level, this API obtains the connection status at the device level.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| [ConnectionState](arkts-connectivity-remotedevice-connectionstate-t.md) | Connection status between the local and remote devices. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## getDeviceClass

```TypeScript
getDeviceClass(): DeviceClass
```

Obtains the type of a remote device.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceClass](arkts-connectivity-remotedevice-deviceclass-t.md) | Remote device type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## getDeviceInformation

```TypeScript
getDeviceInformation(): DeviceInformation
```

Obtains the information of a remote device.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceInformation](arkts-connectivity-remotedevice-deviceinformation-i.md) | Information of a remote device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## getDeviceName

```TypeScript
getDeviceName(): string
```

Obtains the name of a remote device.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| string | Remote device name. The value contains a maximum of 30 characters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## getPairingState

```TypeScript
getPairingState(): PairingState
```

Obtains the pairing status with a remote device.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| [PairingState](arkts-connectivity-remotedevice-pairingstate-t.md) | Pairing status with a remote device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## startPairing

```TypeScript
startPairing(): Promise<void>
```

Initiates pairing with a remote device. This API uses a promise to return the result. After the pairing is initiated, different types of dialog boxes will be displayed based on the input and output capability IDs of the local and remote devices, for example, whether the devices have the display and keyboard input capabilities. The user will need to confirm the pairing.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
