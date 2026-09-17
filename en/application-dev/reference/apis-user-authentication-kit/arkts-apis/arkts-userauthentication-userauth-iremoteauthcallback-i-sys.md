# IRemoteAuthCallback (System API)

Defines the callback of remote authentication. This API is used in remote authentication scenarios to obtain parameters of the remote authentication page and return the authentication result.

**Since:** 26.0.0

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## onGetRemoteAuthWidgetParam

```TypeScript
onGetRemoteAuthWidgetParam: WidgetParamCallback
```

Callback triggered to obtain remote authentication page parameters. When a remote device initiates an authentication request, the system calls this callback to obtain the configuration parameters on the authentication page.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## onRemoteAuthResult

```TypeScript
onRemoteAuthResult: ResultCallback
```

Callback triggered to return the remote authentication result. After remote authentication is complete, the system calls this callback to return the authentication result to the initiator.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.
