# ContractRequestData (System API)

```TypeScript
export interface ContractRequestData
```

Information required for encryption.

**Since:** 20

<!--Device-eSIM-export interface ContractRequestData--><!--Device-eSIM-export interface ContractRequestData-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## nonce

```TypeScript
nonce: string
```

Random number in hexadecimal format.

**Type:** string

**Since:** 20

<!--Device-ContractRequestData-nonce: string--><!--Device-ContractRequestData-nonce: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## pkid

```TypeScript
pkid: string
```

Select a public key ID from the value returned by the getSupportedPkids interface.

**Type:** string

**Since:** 20

<!--Device-ContractRequestData-pkid: string--><!--Device-ContractRequestData-pkid: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## publicKey

```TypeScript
publicKey: string
```

Public key, which is encoded in Base64 format.

**Type:** string

**Since:** 20

<!--Device-ContractRequestData-publicKey: string--><!--Device-ContractRequestData-publicKey: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.
