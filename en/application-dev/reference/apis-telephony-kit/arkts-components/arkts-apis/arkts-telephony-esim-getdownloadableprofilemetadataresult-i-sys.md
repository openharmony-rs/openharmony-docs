# GetDownloadableProfileMetadataResult (System API)

```TypeScript
export interface GetDownloadableProfileMetadataResult
```

Obtains the metadata of the downloadable profile.

**Since:** 18

<!--Device-eSIM-export interface GetDownloadableProfileMetadataResult--><!--Device-eSIM-export interface GetDownloadableProfileMetadataResult-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## downloadableProfile

```TypeScript
downloadableProfile: DownloadableProfile
```

Downloadable profile.

**Type:** [DownloadableProfile](arkts-telephony-esim-downloadableprofile-i.md)

**Since:** 18

<!--Device-GetDownloadableProfileMetadataResult-downloadableProfile: DownloadableProfile--><!--Device-GetDownloadableProfileMetadataResult-downloadableProfile: DownloadableProfile-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## iccid

```TypeScript
iccid: string
```

Profile ICCID.

**Type:** string

**Since:** 18

<!--Device-GetDownloadableProfileMetadataResult-iccid: string--><!--Device-GetDownloadableProfileMetadataResult-iccid: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## pprFlag

```TypeScript
pprFlag: boolean
```

Whether the profile has a policy rule. The value **true** indicates that the profile has a policy rule, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 18

<!--Device-GetDownloadableProfileMetadataResult-pprFlag: boolean--><!--Device-GetDownloadableProfileMetadataResult-pprFlag: boolean-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## pprType

```TypeScript
pprType: number
```

Profile policy rule type.

**Type:** number

**Since:** 18

<!--Device-GetDownloadableProfileMetadataResult-pprType: int--><!--Device-GetDownloadableProfileMetadataResult-pprType: int-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## profileClass

```TypeScript
profileClass: ProfileClass
```

Profile class.

**Type:** [ProfileClass](arkts-telephony-esim-profileclass-e-sys.md)

**Since:** 18

<!--Device-GetDownloadableProfileMetadataResult-profileClass: ProfileClass--><!--Device-GetDownloadableProfileMetadataResult-profileClass: ProfileClass-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## profileName

```TypeScript
profileName: string
```

Profile name.

**Type:** string

**Since:** 18

<!--Device-GetDownloadableProfileMetadataResult-profileName: string--><!--Device-GetDownloadableProfileMetadataResult-profileName: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## responseResult

```TypeScript
responseResult: ResultCode
```

Operation result code.

**Type:** [ResultCode](arkts-telephony-esim-resultcode-e-sys.md)

**Since:** 18

<!--Device-GetDownloadableProfileMetadataResult-responseResult: ResultCode--><!--Device-GetDownloadableProfileMetadataResult-responseResult: ResultCode-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## serviceProviderName

```TypeScript
serviceProviderName: string
```

Service provider name.

**Type:** string

**Since:** 18

<!--Device-GetDownloadableProfileMetadataResult-serviceProviderName: string--><!--Device-GetDownloadableProfileMetadataResult-serviceProviderName: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## solvableErrors

```TypeScript
solvableErrors: SolvableErrors
```

Solvable errors.

**Type:** [SolvableErrors](arkts-telephony-esim-solvableerrors-e-sys.md)

**Since:** 18

<!--Device-GetDownloadableProfileMetadataResult-solvableErrors: SolvableErrors--><!--Device-GetDownloadableProfileMetadataResult-solvableErrors: SolvableErrors-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.
