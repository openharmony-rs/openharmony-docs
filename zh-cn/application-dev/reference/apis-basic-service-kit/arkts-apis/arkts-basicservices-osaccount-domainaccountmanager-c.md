# DomainAccountManager

域账号管理类。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-osAccount-class DomainAccountManager--><!--Device-osAccount-class DomainAccountManager-End-->

**系统能力：** SystemCapability.Account.OsAccount

## updateAccountInfo

```TypeScript
static updateAccountInfo(oldAccountInfo: DomainAccountInfo, newAccountInfo: DomainAccountInfo): Promise<void>
```

修改指定域账号信息。使用Promise异步回调。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.MANAGE_DOMAIN_ACCOUNTS

<!--Device-DomainAccountManager-static updateAccountInfo(oldAccountInfo: DomainAccountInfo, newAccountInfo: DomainAccountInfo): Promise<void>--><!--Device-DomainAccountManager-static updateAccountInfo(oldAccountInfo: DomainAccountInfo, newAccountInfo: DomainAccountInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldAccountInfo | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示旧域账号信息。 |
| newAccountInfo | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示新域账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | The new account info is invalid. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | The old account not found. |
| [12300004](../../apis-basic-services-kit/errorcode-account.md#12300004-账号已存在) | The new account already exists. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
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

ArkTS-Sta示例：

```TypeScript
import osAccount from '@ohos.account.osAccount';
import { BusinessError } from '@kit.BasicServicesKit';

let oldDomainInfo: osAccount.DomainAccountInfo =
  {domain: 'testDomain', accountName: 'oldtestAccountName'};
let newDomainInfo: osAccount.DomainAccountInfo =
  {domain: 'testDomain', accountName: 'newtestAccountName'};
try {
  osAccount.DomainAccountManager.updateAccountInfo(oldDomainInfo, newDomainInfo).then(() => {
    console.info('updateAccountInfo, success');
  }).catch((e: Error) => {
    const err = e as BusinessError;
    console.error('updateAccountInfo err: ' + err);
  });
} catch (e: Error) {
  const err = e as BusinessError;
  console.error(`updateAccountInfo exception: code is ${err.code}, message is ${err.message}`);
}
```

