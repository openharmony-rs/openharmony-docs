# AuthorizationResult

Defines the authorization result. Currently, the authorization validity period of all [Privileges](arkts-basicservices-authorization-privilege-e.md) follows the lifecycle of the caller process.

**Since:** 26.1.0

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { authorization } from '@kit.BasicServicesKit';
```

## privilege

```TypeScript
privilege: Privilege
```

Privilege associated with the authorization.

**Type:** [Privilege](arkts-basicservices-authorization-privilege-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

## resultCode

```TypeScript
resultCode: AuthorizationResultCode
```

Authorization result code. If the authorization is granted, [AUTHORIZATION_GRANTED](arkts-basicservices-authorization-authorizationresultcode-e.md#authorization_granted) is returned. Otherwise, an error code is returned. For details, see [AuthorizationResultCode](arkts-basicservices-authorization-authorizationresultcode-e.md).

**Type:** [AuthorizationResultCode](arkts-basicservices-authorization-authorizationresultcode-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount
