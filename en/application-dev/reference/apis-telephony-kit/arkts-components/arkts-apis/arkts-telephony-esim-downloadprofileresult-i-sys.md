# DownloadProfileResult (System API)

```TypeScript
export interface DownloadProfileResult
```

Defines the profile download result.

**Since:** 18

<!--Device-eSIM-export interface DownloadProfileResult--><!--Device-eSIM-export interface DownloadProfileResult-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## cardId

```TypeScript
cardId: number
```

Card ID.

**Type:** number

**Since:** 18

<!--Device-DownloadProfileResult-cardId: int--><!--Device-DownloadProfileResult-cardId: int-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## responseResult

```TypeScript
responseResult: ResultCode
```

Operation result code.

**Type:** [ResultCode](arkts-telephony-esim-resultcode-e-sys.md)

**Since:** 18

<!--Device-DownloadProfileResult-responseResult: ResultCode--><!--Device-DownloadProfileResult-responseResult: ResultCode-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## solvableErrors

```TypeScript
solvableErrors: SolvableErrors
```

Solvable errors.

**Type:** [SolvableErrors](arkts-telephony-esim-solvableerrors-e-sys.md)

**Since:** 18

<!--Device-DownloadProfileResult-solvableErrors: SolvableErrors--><!--Device-DownloadProfileResult-solvableErrors: SolvableErrors-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.
