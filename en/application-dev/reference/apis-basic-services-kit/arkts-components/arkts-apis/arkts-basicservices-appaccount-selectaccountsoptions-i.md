# SelectAccountsOptions

Defines the options for selecting accounts.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

## Modules to Import

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## allowedAccounts

```TypeScript
allowedAccounts?: Array<AppAccountInfo>
```

Array of allowed accounts. By default, no value is passed in.

**Type:** Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

## allowedOwners

```TypeScript
allowedOwners?: Array<string>
```

Array of the owners of the allowed accounts. By default, no value is passed in.

**Type:** Array&lt;string&gt;

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

## requiredLabels

```TypeScript
requiredLabels?: Array<string>
```

Labels of the authenticator. By default, no value is passed in.

**Type:** Array&lt;string&gt;

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount
