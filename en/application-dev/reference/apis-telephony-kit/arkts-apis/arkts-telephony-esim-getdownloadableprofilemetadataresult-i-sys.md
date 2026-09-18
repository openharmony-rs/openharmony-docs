# GetDownloadableProfileMetadataResult (System API)

Obtains the metadata of the downloadable profile.

**Since:** 18

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

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## iccid

```TypeScript
iccid: string
```

Profile ICCID.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## pprFlag

```TypeScript
pprFlag: boolean
```

Whether the profile has a policy rule. The value **true** indicates that the profile has a policy rule, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## pprType

```TypeScript
pprType: number
```

Profile policy rule type.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## profileClass

```TypeScript
profileClass: ProfileClass
```

Profile class.

**Type:** [ProfileClass](arkts-telephony-esim-profileclass-e-sys.md)

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## profileName

```TypeScript
profileName: string
```

Profile name.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## responseResult

```TypeScript
responseResult: ResultCode
```

Operation result code.

**Type:** [ResultCode](arkts-telephony-esim-resultcode-e-sys.md)

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## serviceProviderName

```TypeScript
serviceProviderName: string
```

Service provider name.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## solvableErrors

```TypeScript
solvableErrors: SolvableErrors
```

Solvable errors.

**Type:** [SolvableErrors](arkts-telephony-esim-solvableerrors-e-sys.md)

**Since:** 18

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.
