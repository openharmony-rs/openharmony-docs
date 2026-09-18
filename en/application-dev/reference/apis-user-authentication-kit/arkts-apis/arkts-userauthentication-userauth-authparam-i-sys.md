# AuthParam

Defines the user authentication parameters. This API is used to configure user authentication parameters, including the challenge value, authentication type list, authentication trust level, and authentication result reuse configuration. By properly configuring these parameters, you can meet authentication requirements in different service scenarios.

**Since:** 10

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## credentialIdList

```TypeScript
credentialIdList?: Uint8Array[]
```

Credential ID list, which is used to specify the credentials to be authenticated. This parameter is passed when only specific credentials instead of all credentials of the user need to be authenticated. If this parameter is not passed or an empty array is passed, all credentials of the user are authenticated by default.

**Type:** Uint8Array[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

ID of the target user to be authenticated, which specifies the user to be authenticated. This parameter is passed when a specific user instead of the current login user needs to be authenticated. If this parameter is not passed, the ID of the current login user is used by default. The value is a non-negative integer.

**Type:** number

**Default:** The ID of the current user. The value is a positive integer greater than or equal to 0.

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.
