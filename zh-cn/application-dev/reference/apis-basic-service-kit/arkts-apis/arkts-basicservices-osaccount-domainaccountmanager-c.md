# DomainAccountManager

域账号管理类。

**起始版本：** 18

**系统能力：** SystemCapability.Account.OsAccount

## updateAccountInfo

```TypeScript
static updateAccountInfo(oldAccountInfo: DomainAccountInfo, newAccountInfo: DomainAccountInfo): Promise<void>
```

修改指定域账号信息。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.MANAGE_DOMAIN_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldAccountInfo | DomainAccountInfo | 是 | 表示旧域账号信息。 |
| newAccountInfo | DomainAccountInfo | 是 | 表示新域账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [12300001](../../errorcode-universal.md#12300001-The) | The system service works abnormally. |
| [12300002](../../errorcode-universal.md#12300002-The) | The new account info is invalid. |
| [12300003](../../errorcode-universal.md#12300003-The) | The old account not found. |
| [12300004](../../errorcode-universal.md#12300004-The) | The new account already exists. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let oldDomainInfo: osAccount.DomainAccountInfo =
  {domain: 'testDomain', accountName: 'oldtestAccountName'};
let newDomainInfo: osAccount.DomainAccountInfo =
  {domain: 'testDomain', accountName: 'newtestAccountName'};
try {
  osAccount.DomainAccountManager.updateAccountInfo(oldDomainInfo, newDomainInfo).then(() => {
    console.info('updateAccountInfo, success');
  }).catch((err: BusinessError) => {
    console.error('updateAccountInfo err: ' + err);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`updateAccountInfo exception: code is ${err.code}, message is ${err.message}`);
}

```

