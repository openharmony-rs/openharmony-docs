# IccAccountInfo

```TypeScript
export interface IccAccountInfo
```

Defines the ICC account information.

**Since:** 10

<!--Device-sim-export interface IccAccountInfo--><!--Device-sim-export interface IccAccountInfo-End-->

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## iccId

```TypeScript
iccId: string
```

ICCID number.

**Type:** string

**Since:** 10

<!--Device-IccAccountInfo-iccId: string--><!--Device-IccAccountInfo-iccId: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

## isActive

```TypeScript
isActive: boolean
```

Whether the card is activated.

**true**: activated.

**false**: not activated.

**Type:** boolean

**Since:** 10

<!--Device-IccAccountInfo-isActive: boolean--><!--Device-IccAccountInfo-isActive: boolean-End-->

**System capability:** SystemCapability.Telephony.CoreService

## isEsim

```TypeScript
isEsim: boolean
```

Whether the SIM card is an eSIM.

- **true**: The SIM card is an eSIM.  
- **false**: The SIM card is not an eSIM.

**Type:** boolean

**Since:** 10

<!--Device-IccAccountInfo-isEsim: boolean--><!--Device-IccAccountInfo-isEsim: boolean-End-->

**System capability:** SystemCapability.Telephony.CoreService

## showName

```TypeScript
showName: string
```

SIM card display name.

**Type:** string

**Since:** 10

<!--Device-IccAccountInfo-showName: string--><!--Device-IccAccountInfo-showName: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

## showNumber

```TypeScript
showNumber: string
```

SIM card display number.

**Type:** string

**Since:** 10

<!--Device-IccAccountInfo-showNumber: string--><!--Device-IccAccountInfo-showNumber: string-End-->

**System capability:** SystemCapability.Telephony.CoreService

## simId

```TypeScript
simId: number
```

SIM card ID.

**Type:** number

**Since:** 10

<!--Device-IccAccountInfo-simId: int--><!--Device-IccAccountInfo-simId: int-End-->

**System capability:** SystemCapability.Telephony.CoreService

## slotIndex

```TypeScript
slotIndex: number
```

Card slot ID.

**Type:** number

**Since:** 10

<!--Device-IccAccountInfo-slotIndex: int--><!--Device-IccAccountInfo-slotIndex: int-End-->

**System capability:** SystemCapability.Telephony.CoreService
