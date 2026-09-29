# SimAuthenticationResponse (System API)

```TypeScript
export interface SimAuthenticationResponse
```

Defines the SIM card authentication response.

**Since:** 14

<!--Device-sim-export interface SimAuthenticationResponse--><!--Device-sim-export interface SimAuthenticationResponse-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## response

```TypeScript
response: string
```

Indicates the response of authentication.

**Type:** string

**Since:** 14

<!--Device-SimAuthenticationResponse-response: string--><!--Device-SimAuthenticationResponse-response: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## simStatusWord1

```TypeScript
simStatusWord1: number
```

Status word 1 of the SIM card, which is returned by the SIM card after command execution.

**Type:** number

**Since:** 14

<!--Device-SimAuthenticationResponse-simStatusWord1: int--><!--Device-SimAuthenticationResponse-simStatusWord1: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

## simStatusWord2

```TypeScript
simStatusWord2: number
```

Status word 2 of the SIM card, which is returned by the SIM card after command execution.

**Type:** number

**Since:** 14

<!--Device-SimAuthenticationResponse-simStatusWord2: int--><!--Device-SimAuthenticationResponse-simStatusWord2: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.
