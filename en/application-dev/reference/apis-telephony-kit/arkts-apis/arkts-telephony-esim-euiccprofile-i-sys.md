# EuiccProfile (System API)

```TypeScript
export interface EuiccProfile
```

Profile information.

**Since:** 18

<!--Device-eSIM-export interface EuiccProfile--><!--Device-eSIM-export interface EuiccProfile-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## accessRules

```TypeScript
accessRules: Array<AccessRule>
```

Profile access rules.

**Type:** Array&lt;[AccessRule](arkts-telephony-esim-accessrule-i-sys.md)&gt;

**Since:** 18

<!--Device-EuiccProfile-accessRules: Array<AccessRule>--><!--Device-EuiccProfile-accessRules: Array<AccessRule>-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## iccid

```TypeScript
iccid: string
```

Profile ICCID.

**Type:** string

**Since:** 18

<!--Device-EuiccProfile-iccid: string--><!--Device-EuiccProfile-iccid: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## nickName

```TypeScript
nickName: string
```

Profile nickname.

**Type:** string

**Since:** 18

<!--Device-EuiccProfile-nickName: string--><!--Device-EuiccProfile-nickName: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## operatorId

```TypeScript
operatorId: OperatorId
```

Operation ID of the profile.

**Type:** [OperatorId](arkts-telephony-esim-operatorid-i-sys.md)

**Since:** 18

<!--Device-EuiccProfile-operatorId: OperatorId--><!--Device-EuiccProfile-operatorId: OperatorId-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## policyRules

```TypeScript
policyRules: PolicyRules
```

Profile policy rules.

**Type:** [PolicyRules](arkts-telephony-esim-policyrules-e-sys.md)

**Since:** 18

<!--Device-EuiccProfile-policyRules: PolicyRules--><!--Device-EuiccProfile-policyRules: PolicyRules-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## profileClass

```TypeScript
profileClass: ProfileClass
```

Profile class.

**Type:** [ProfileClass](arkts-telephony-esim-profileclass-e-sys.md)

**Since:** 18

<!--Device-EuiccProfile-profileClass: ProfileClass--><!--Device-EuiccProfile-profileClass: ProfileClass-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## profileName

```TypeScript
profileName: string
```

Profile name.

**Type:** string

**Since:** 18

<!--Device-EuiccProfile-profileName: string--><!--Device-EuiccProfile-profileName: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## serviceProviderName

```TypeScript
serviceProviderName: string
```

Service provider name.

**Type:** string

**Since:** 18

<!--Device-EuiccProfile-serviceProviderName: string--><!--Device-EuiccProfile-serviceProviderName: string-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## state

```TypeScript
state: ProfileState
```

Profile status.

**Type:** [ProfileState](arkts-telephony-esim-profilestate-e-sys.md)

**Since:** 18

<!--Device-EuiccProfile-state: ProfileState--><!--Device-EuiccProfile-state: ProfileState-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.
