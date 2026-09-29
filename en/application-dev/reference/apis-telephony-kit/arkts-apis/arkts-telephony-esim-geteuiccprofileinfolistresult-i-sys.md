# GetEuiccProfileInfoListResult (System API)

```TypeScript
export interface GetEuiccProfileInfoListResult
```

Obtains the profile information list.

**Since:** 18

<!--Device-eSIM-export interface GetEuiccProfileInfoListResult--><!--Device-eSIM-export interface GetEuiccProfileInfoListResult-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## isRemovable

```TypeScript
isRemovable: boolean
```

Whether the eUICC is removable. The value **true** indicates that the eUICC is removable, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 18

<!--Device-GetEuiccProfileInfoListResult-isRemovable: boolean--><!--Device-GetEuiccProfileInfoListResult-isRemovable: boolean-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## profiles

```TypeScript
profiles: Array<EuiccProfile>
```

Profile array.

**Type:** Array&lt;[EuiccProfile](arkts-telephony-esim-euiccprofile-i-sys.md)&gt;

**Since:** 18

<!--Device-GetEuiccProfileInfoListResult-profiles: Array<EuiccProfile>--><!--Device-GetEuiccProfileInfoListResult-profiles: Array<EuiccProfile>-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## responseResult

```TypeScript
responseResult: ResultCode
```

Promise used to return the operation result.

**Type:** [ResultCode](arkts-telephony-esim-resultcode-e-sys.md)

**Since:** 18

<!--Device-GetEuiccProfileInfoListResult-responseResult: ResultCode--><!--Device-GetEuiccProfileInfoListResult-responseResult: ResultCode-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.
