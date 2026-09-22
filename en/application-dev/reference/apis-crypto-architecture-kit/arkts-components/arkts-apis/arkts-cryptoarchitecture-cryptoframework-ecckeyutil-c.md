# ECCKeyUtil

```TypeScript
class ECCKeyUtil
```

Provides utilities for ECC key parameter generation and point conversion based on the specified elliptic curve.

**Since:** 11

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## convertPoint

```TypeScript
static convertPoint(curveName: string, encodedPoint: Uint8Array): Point
```

Converts the specified point data into a **Point** object based on the curve name (NID). Currently, compressed and uncompressed point data is supported.

> **NOTE:** 
> 
> According to section 2.2 in RFC 5480:
> 1. The uncompressed point data is represented as **0x04**|x coordinate|y coordinate.
> 2. The compressed point data in the **Fp** field (the **F2m** field is not supported currently) is represented as follows: **0x03**|x coordinate (when the coordinate y is an odd number); **0x02**|x coordinate (when the coordinate y is an even number).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| curveName | string | Yes | Elliptic curve name, that is, the NID. |
| encodedPoint | Uint8Array | Yes | Data of the point on the ECC elliptic curve to convert. |

**Return value:**

| Type | Description |
| --- | --- |
| [Point](arkts-cryptoarchitecture-cryptoframework-point-i.md) | **Point** object obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 26.2.0 and later |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

// Randomly generated uncompressed point data.
let pkData =
  new Uint8Array([4, 143, 39, 57, 249, 145, 50, 63, 222, 35, 70, 178, 121, 202, 154, 21, 146, 129, 75, 76, 63, 8, 195,
    157, 111, 40, 217, 215, 148, 120, 224, 205, 82, 83, 92, 185, 21, 211, 184, 5, 19, 114, 33, 86, 85, 228, 123, 242,
    206, 200, 98, 178, 184, 130, 35, 232, 45, 5, 202, 189, 11, 46, 163, 156, 152]);
let returnPoint = cryptoFramework.ECCKeyUtil.convertPoint('NID_brainpoolP256r1', pkData);
console.info('returnPoint: ' + returnPoint.x.toString(16));
```

## genECCCommonParamsSpec

```TypeScript
static genECCCommonParamsSpec(curveName: string): ECCCommonParamsSpec
```

Generates common parameters for an asymmetric key pair based on the specified name identifier (NID) of an elliptic curve. For details, see [ECC](../../../security/CryptoArchitectureKit/crypto-key-generation-conversion.md#ecc) and [SM2](../../../security/CryptoArchitectureKit/crypto-key-generation-conversion.md#sm2).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.CryptoFramework.Key.AsymKey
- API version 11: SystemCapability.Security.CryptoFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| curveName | string | Yes | NID of the elliptic curve. |

**Return value:**

| Type | Description |
| --- | --- |
| [ECCCommonParamsSpec](arkts-cryptoarchitecture-cryptoframework-ecccommonparamsspec-i.md) | ECC common parameters generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let ECCCommonParamsSpec = cryptoFramework.ECCKeyUtil.genECCCommonParamsSpec('NID_brainpoolP160r1');
  console.info('genECCCommonParamsSpec result: success.');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`genECCCommonParamsSpec failed: errCode: ${e.code}, errMsg: ${e.message}`);
}
```

## getEncodedPoint

```TypeScript
static getEncodedPoint(curveName: string, point: Point, format: string): Uint8Array
```

Obtains the point data in the specified format from a **Point** object. Currently, compressed and uncompressed point data is supported.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.CryptoFramework.Key.AsymKey

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| curveName | string | Yes | Elliptic curve name, that is, the NID. |
| point | [Point](arkts-cryptoarchitecture-cryptoframework-point-i.md) | Yes | **Point** object of the elliptic curve. |
| format | string | Yes | Format of the point data to obtain. Currently, the value can be **COMPRESSED** or **UNCOMPRESSED** only. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Point data in the specified format. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 26.2.0 and later |
| [17620001](../errorcode-crypto-framework.md#17620001-memory-operation-failed) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-cryptographic-operation-error) | Crypto operation error. |

**Examples**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function doTest() {
  let generator = cryptoFramework.createAsyKeyGenerator('ECC_BrainPoolP256r1');
  let keyPair = await generator.generateKeyPair();
  let eccPkX = keyPair.pubKey.getAsyKeySpec(cryptoFramework.AsyKeySpecItem.ECC_PK_X_BN);
  let eccPkY = keyPair.pubKey.getAsyKeySpec(cryptoFramework.AsyKeySpecItem.ECC_PK_Y_BN);
  console.info('ECC_PK_X_BN 16: ' + eccPkX.toString(16));
  console.info('ECC_PK_Y_BN 16: ' + eccPkY.toString(16));
  // Place eccPkX.toString(16) in x and eccPkY.toString(16) in y.
  let returnPoint: cryptoFramework.Point = {
    x: BigInt('0x' + eccPkX.toString(16)),
    y: BigInt('0x' + eccPkY.toString(16))
  };
  let returnData = cryptoFramework.ECCKeyUtil.getEncodedPoint('NID_brainpoolP256r1', returnPoint, 'UNCOMPRESSED');
  console.info('returnData: ' + returnData);
}
```
