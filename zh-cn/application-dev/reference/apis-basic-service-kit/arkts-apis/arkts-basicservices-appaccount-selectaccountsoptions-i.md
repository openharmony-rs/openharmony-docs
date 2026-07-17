# SelectAccountsOptions

表示用于选择账号的选项。

**起始版本：** 9

<!--Device-appAccount-interface SelectAccountsOptions--><!--Device-appAccount-interface SelectAccountsOptions-End-->

**系统能力：** SystemCapability.Account.AppAccount

## 导入模块

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## allowedAccounts

```TypeScript
allowedAccounts?: Array<AppAccountInfo>
```

允许的账号数组，默认为空。

**类型：** Array<AppAccountInfo>

**起始版本：** 9

<!--Device-SelectAccountsOptions-allowedAccounts?: Array<AppAccountInfo>--><!--Device-SelectAccountsOptions-allowedAccounts?: Array<AppAccountInfo>-End-->

**系统能力：** SystemCapability.Account.AppAccount

## allowedOwners

```TypeScript
allowedOwners?: Array<string>
```

允许的账号所有者数组，默认为空。

**类型：** Array<string>

**起始版本：** 9

<!--Device-SelectAccountsOptions-allowedOwners?: Array<string>--><!--Device-SelectAccountsOptions-allowedOwners?: Array<string>-End-->

**系统能力：** SystemCapability.Account.AppAccount

## requiredLabels

```TypeScript
requiredLabels?: Array<string>
```

认证器的标签标识，默认为空。

**类型：** Array<string>

**起始版本：** 9

<!--Device-SelectAccountsOptions-requiredLabels?: Array<string>--><!--Device-SelectAccountsOptions-requiredLabels?: Array<string>-End-->

**系统能力：** SystemCapability.Account.AppAccount

