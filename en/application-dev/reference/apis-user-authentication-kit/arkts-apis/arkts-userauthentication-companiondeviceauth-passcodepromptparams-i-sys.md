# PasscodePromptParams (System API)

Params carried by the framework when prompting for a companion device passcode.

@interface PasscodePromptParams

**Since:** 26.1.0

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## challenge

```TypeScript
challenge: Uint8Array
```

Challenge carried by the framework when prompting for a companion device passcode.

**Type:** Uint8Array

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
