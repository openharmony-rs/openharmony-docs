# getVirtualAddressByHash

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## getVirtualAddressByHash

```TypeScript
function getVirtualAddressByHash(algorithmType: HashAlgorithmType, hashValue: string): string
```

Obtain the virtual address of the corresponding device based on the hash value of the real address.

**Since:** 24

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| algorithmType | [HashAlgorithmType](arkts-connectivity-connection-hashalgorithmtype-e.md) | Yes | Indicate the hash algorithm type. |
| hashValue | string | Yes | Indicate the hash value of the device MAC address. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the virtual mac address. For example, "11:22:33:AA:BB:FF". |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API when the short-range chip is not inserted on 2in1 device. |
| 2900003 | Bluetooth disabled. |
| [2900015](../errorcode-bluetoothManager.md#2900015-parameter-format-inconsistent-with-specifications) | Parameter format mismatch with specification. |
| [2900016](../errorcode-bluetoothManager.md#2900016-device-not-paired) | Device unpaired. |
| 2900099 | Internal system error. For example, IPC error. Detailed error messages can be used to assist in locating the problem. |

**Examples**

```TypeScript
// If the queried actual address is 11:22:33:44:55:AA,
// the corresponding 64-bit hash is d2204cb9b6d3d3962cc90fa54130efb4c10b57deb2e1aafd255596e0d4fd6789.
// If HashAlgorithmType is set to HASH_ALGORITHM_SHA256, the last 32 bits of the hash are used.
let hashValue: string = "c10b57deb2e1aafd255596e0d4fd6789";
try {
  let addr: string = connection.getVirtualAddressByHash(connection.HashAlgorithmType.HASH_ALGORITHM_SHA256, hashValue);
} catch (err) {
  console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
