# ContinuousAuthParam (System API)

Defines continuous authentication parameters. They are used to configure parameters related to the subscription to the continuous authentication status, for example, specifying the target template to be subscribed to.

**Since:** 23

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## templateId

```TypeScript
templateId?: Uint8Array
```

Template ID. It is used to specify the target template to be subscribed to. If this parameter is not specified, the continuous authentication status of all templates of the current user is subscribed to by default. If a specific template ID is specified, only the authentication status change of the template is subscribed to.

**Type:** Uint8Array

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
