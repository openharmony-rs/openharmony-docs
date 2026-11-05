# DownloadableProfile

```TypeScript
export interface DownloadableProfile
```

Defines a downloadable profile.

**Since:** 18

<!--Device-eSIM-export interface DownloadableProfile--><!--Device-eSIM-export interface DownloadableProfile-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## accessRules

```TypeScript
accessRules?: Array<AccessRule>
```

Access rule array. If this parameter is not transferred, the default value is null.

**Type:** Array&lt;[AccessRule](arkts-telephony-esim-accessrule-i.md)&gt;

**Since:** 18

<!--Device-DownloadableProfile-accessRules?: Array<AccessRule>--><!--Device-DownloadableProfile-accessRules?: Array<AccessRule>-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

## activationCode

```TypeScript
activationCode: string
```

Activation code. For a profile that does not require an activation code, the value may be left empty.

**Type:** string

**Since:** 18

<!--Device-DownloadableProfile-activationCode: string--><!--Device-DownloadableProfile-activationCode: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

## carrierName

```TypeScript
carrierName?: string
```

Carrier name. If this parameter is not specified, the default value is null.

**Type:** string

**Since:** 18

<!--Device-DownloadableProfile-carrierName?: string--><!--Device-DownloadableProfile-carrierName?: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

## confirmationCode

```TypeScript
confirmationCode?: string
```

Confirmation code. If this parameter is not specified, the value is a null string by default.

**Type:** string

**Since:** 18

<!--Device-DownloadableProfile-confirmationCode?: string--><!--Device-DownloadableProfile-confirmationCode?: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim
