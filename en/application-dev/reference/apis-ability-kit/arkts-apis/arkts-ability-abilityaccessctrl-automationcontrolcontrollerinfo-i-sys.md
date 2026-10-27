# AutomationControlControllerInfo (System API)

```TypeScript
interface AutomationControlControllerInfo
```

Represents a controller app that has automation control over a target app.

**Since:** 26.1.0

<!--Device-abilityAccessCtrl-interface AutomationControlControllerInfo--><!--Device-abilityAccessCtrl-interface AutomationControlControllerInfo-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the controller app.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutomationControlControllerInfo-bundleName: string--><!--Device-AutomationControlControllerInfo-bundleName: string-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## controllerTokenID

```TypeScript
controllerTokenID: number
```

Token ID of the controller app.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutomationControlControllerInfo-controllerTokenID: int--><!--Device-AutomationControlControllerInfo-controllerTokenID: int-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
