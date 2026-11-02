# @ohos.userIAM.pinAuth(PIN Authentication)

The **pinAuth** module is the OpenHarmony user identity and access management (UserIAM system). Used for PIN authentication management. This module provides security policy interfaces for configuring PIN authentication for system applications.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace pinAuth--><!--Device-unnamed-declare namespace pinAuth-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getPinComplexityPolicy](arkts-userauthentication-pinauth-getpincomplexitypolicy-f-sys.md#getpincomplexitypolicy-1) | Gets PIN complexity check policy and description. |
| [getPinDeletionDisabledState](arkts-userauthentication-pinauth-getpindeletiondisabledstate-f-sys.md#getpindeletiondisabledstate-1) | Gets the disable state of the PIN deletion feature. |
| [getPinValidityPeriod](arkts-userauthentication-pinauth-getpinvalidityperiod-f-sys.md#getpinvalidityperiod-1) | Get PIN validity period. |
| [setPinComplexityPolicy](arkts-userauthentication-pinauth-setpincomplexitypolicy-f-sys.md#setpincomplexitypolicy-1) | Set the PIN complexity check policy and description. After setting this policy, users must create or change their lock screen PIN to match the specified complexity regular expression. |
| [setPinDeletionDisabledState](arkts-userauthentication-pinauth-setpindeletiondisabledstate-f-sys.md#setpindeletiondisabledstate-1) | Sets the disable state of the PIN deletion feature. After the policy is set, the user cannot delete the PIN when the feature is disabled. |
| [setPinValidityPeriod](arkts-userauthentication-pinauth-setpinvalidityperiod-f-sys.md#setpinvalidityperiod-1) | Sets PIN validity period. After the policy is set, when PIN is expired, a security prompt will be displayed asking the user to reset the PIN. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [PinComplexityPolicy](arkts-userauthentication-pinauth-pincomplexitypolicy-i-sys.md) | PIN complexity check policy and description. |
<!--DelEnd-->
