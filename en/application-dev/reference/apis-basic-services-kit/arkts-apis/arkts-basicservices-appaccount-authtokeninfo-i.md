# AuthTokenInfo

```TypeScript
interface AuthTokenInfo
```

Defines authorization token information.

**Since:** 9

<!--Device-appAccount-interface AuthTokenInfo--><!--Device-appAccount-interface AuthTokenInfo-End-->

**System capability:** SystemCapability.Account.AppAccount

## Modules to Import

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## account

```TypeScript
account?: AppAccountInfo
```

Information about the account to which the token belongs. By default, no value is passed in.

**Type:** [AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)

**Since:** 9

<!--Device-AuthTokenInfo-account?: AppAccountInfo--><!--Device-AuthTokenInfo-account?: AppAccountInfo-End-->

**System capability:** SystemCapability.Account.AppAccount

## authType

```TypeScript
authType: string
```

Authentication type.

**Type:** string

**Since:** 9

<!--Device-AuthTokenInfo-authType: string--><!--Device-AuthTokenInfo-authType: string-End-->

**System capability:** SystemCapability.Account.AppAccount

## token

```TypeScript
token: string
```

Value of the authorization token.

**Type:** string

**Since:** 9

<!--Device-AuthTokenInfo-token: string--><!--Device-AuthTokenInfo-token: string-End-->

**System capability:** SystemCapability.Account.AppAccount
