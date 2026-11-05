# PasscodePromptParams (System API)

```TypeScript
interface PasscodePromptParams
```

Defines the parameters of a passcode input request, used to pass context information such as the challenge value.

**Since:** 26.0.1

<!--Device-companionDeviceAuth-interface PasscodePromptParams--><!--Device-companionDeviceAuth-interface PasscodePromptParams-End-->

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

Challenge value issued by the system when a passcode is requested.

**Type:** Uint8Array

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-PasscodePromptParams-challenge: Uint8Array--><!--Device-PasscodePromptParams-challenge: Uint8Array-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
