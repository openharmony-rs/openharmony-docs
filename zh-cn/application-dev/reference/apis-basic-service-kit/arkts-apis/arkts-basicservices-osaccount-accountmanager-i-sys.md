# AccountManager

系统账号管理类。

**起始版本：** 7

<!--Device-osAccount-interface AccountManager--><!--Device-osAccount-interface AccountManager-End-->

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

<a id="activateosaccount"></a>
## activateOsAccount

```TypeScript
activateOsAccount(localId: number, callback: AsyncCallback<void>): void
```

激活指定系统账号。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

<!--Device-AccountManager-activateOsAccount(localId: int, callback: AsyncCallback<void>): void--><!--Device-AccountManager-activateOsAccount(localId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当账号激活成功时，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |
| [12300009](../../apis-basic-services-kit/errorcode-account.md#12300009-账号已激活) | Account has been activated.<br>**适用版本：** 7 - 11 |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Service busy. Possible causes: The target account is being operated.<br>**适用版本：** 12+ |
| [12300016](../../apis-basic-services-kit/errorcode-account.md#12300016-账号登录数已达上限) | The number of logged in accounts reaches the upper limit.<br>**适用版本：** 12+ |

**示例：**

激活ID为100的系统账号。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.activateOsAccount(localId, (err: BusinessError)=>{
    if (err) {
      console.error(`activateOsAccount failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('activateOsAccount successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`activateOsAccount failed, code is ${err.code}, message is ${err.message}`);
}

```

<a id="activateosaccount-1"></a>
## activateOsAccount

```TypeScript
activateOsAccount(localId: number): Promise<void>
```

激活指定系统账号。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

<!--Device-AccountManager-activateOsAccount(localId: int): Promise<void>--><!--Device-AccountManager-activateOsAccount(localId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |
| [12300009](../../apis-basic-services-kit/errorcode-account.md#12300009-账号已激活) | Account has been activated.<br>**适用版本：** 7 - 11 |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Service busy. Possible causes: The target account is being operated.<br>**适用版本：** 12+ |
| [12300016](../../apis-basic-services-kit/errorcode-account.md#12300016-账号登录数已达上限) | The number of logged in accounts reaches the upper limit.<br>**适用版本：** 12+ |

**示例：**

激活ID为100的系统账号。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.activateOsAccount(localId).then(() => {
    console.info('activateOsAccount successfully');
  }).catch((err: BusinessError) => {
    console.error(`activateOsAccount failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`activateOsAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="activateosaccount-2"></a>
## activateOsAccount

```TypeScript
activateOsAccount(localId: number, displayId: number): Promise<void>
```

在指定逻辑屏激活（前台启动或切换）目标系统账号。使用Promise异步回调。当前不支持跨逻辑屏激活，即在指定逻辑屏上激活另一个已在逻辑屏前台运行的系统账号。

**起始版本：** 23

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

<!--Device-AccountManager-activateOsAccount(localId: int, displayId: long): Promise<void>--><!--Device-AccountManager-activateOsAccount(localId: int, displayId: long): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| displayId | number | 是 | 逻辑屏ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Service busy. Possible causes: The target account is being operated. |
| [12300016](../../apis-basic-services-kit/errorcode-account.md#12300016-账号登录数已达上限) | The number of logged in accounts reaches the upper limit. |
| [12300018](../../apis-basic-services-kit/errorcode-account.md#12300018-逻辑屏未找到) | Display not found. |
| [12300019](../../apis-basic-services-kit/errorcode-account.md#12300019-不支持跨逻辑屏激活) | Cross-display activation not supported. |

**示例：**

在ID为0的逻辑屏上激活ID为100的系统账号。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
let displayId: number = 0;
try {
  accountManager.activateOsAccount(localId, displayId).then(() => {
    console.info('activateOsAccount with displayId successfully');
  }).catch((err: BusinessError) => {
    console.error(`activateOsAccount with displayId failed, err: ${err.code} ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`activateOsAccount with displayId exception: ${err.code} ${err.message}`);
}

```

<a id="binddomainaccount"></a>
## bindDomainAccount

```TypeScript
bindDomainAccount(localId: number, domainAccountInfo: DomainAccountInfo): Promise<void>
```

在指定系统账号上绑定指定域账号。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-bindDomainAccount(localId: int, domainAccountInfo: DomainAccountInfo): Promise<void>--><!--Device-AccountManager-bindDomainAccount(localId: int, domainAccountInfo: DomainAccountInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 要查询的系统账号ID。 |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 是 | 域账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid domain account information. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | The OS account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted OS account. Possible causes: The OS account cannot be bound. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Service busy. Possible causes: The target OS account or domain account is being operated. |
| [12300021](../../apis-basic-services-kit/errorcode-account.md#12300021-系统账号已绑定域账号) | The OS account is already bound. |
| [12300022](../../apis-basic-services-kit/errorcode-account.md#12300022-域账号已被绑定) | The domain account is already bound. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  let localId: number = 100;
  let domainInfo: osAccount.DomainAccountInfo =
    { domain: 'testDomain', accountName: 'testAccountName' };
  accountManager.bindDomainAccount(localId, domainInfo).then(() => {
    console.info('bindDomainAccount success.');
  }).catch((error: BusinessError) => {
    console.error(`bindDomainAccount failed, errCode=${error.code}, errMsg=${error.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`bindDomainAccount error, errCode=${err.code}, errMsg=${err.message}`);
}

```

<a id="createosaccount"></a>
## createOsAccount

```TypeScript
createOsAccount(localName: string, type: OsAccountType, callback: AsyncCallback<OsAccountInfo>): void
```

创建一个系统账号。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-createOsAccount(localName: string, type: OsAccountType, callback: AsyncCallback<OsAccountInfo>): void--><!--Device-AccountManager-createOsAccount(localName: string, type: OsAccountType, callback: AsyncCallback<OsAccountInfo>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localName | string | 是 | 创建的系统账号的名称。 |
| type | [OsAccountType](arkts-basicservices-osaccount-osaccounttype-e-sys.md) | 是 | 创建的系统账号的类型。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;OsAccountInfo&gt; | 是 | 回调函数。如果创建成功，err为null，data为新创建的系统账号的信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes:1. The operation is restricted by the OS-account constraint.2. The required privilege for the operation has not been granted.<br>**适用版本：** 24+ |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localName or type. |
| [12300004](../../apis-basic-services-kit/errorcode-account.md#12300004-账号已存在) | Local name already exists.<br>**适用版本：** 12+ |
| [12300005](../../apis-basic-services-kit/errorcode-account.md#12300005-不支持多用户) | Multi-user not supported. |
| [12300006](../../apis-basic-services-kit/errorcode-account.md#12300006-不支持的账号类型) | Unsupported account type. |
| [12300007](../../apis-basic-services-kit/errorcode-account.md#12300007-账号数量已达上限) | The number of accounts has reached the upper limit. |
| [12300023](../../apis-basic-services-kit/errorcode-account.md#12300023-指定类型的账号数量已达到上限) | The number of accounts of the specified type has reached the upper limit.<br>**适用版本：** 24+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.createOsAccount('testName', osAccount.OsAccountType.NORMAL,
    (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo)=>{
    if (err) {
      console.error(`createOsAccount exception:code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('createOsAccount osAccountInfo:' + JSON.stringify(osAccountInfo));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`createOsAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="createosaccount-1"></a>
## createOsAccount

```TypeScript
createOsAccount(localName: string, type: OsAccountType, options?: CreateOsAccountOptions): Promise<OsAccountInfo>
```

创建一个系统账号。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-createOsAccount(localName: string, type: OsAccountType, options?: CreateOsAccountOptions): Promise<OsAccountInfo>--><!--Device-AccountManager-createOsAccount(localName: string, type: OsAccountType, options?: CreateOsAccountOptions): Promise<OsAccountInfo>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localName | string | 是 | 创建的系统账号的名称。 |
| type | [OsAccountType](arkts-basicservices-osaccount-osaccounttype-e-sys.md) | 是 | 创建的系统账号的类型。 |
| options | [CreateOsAccountOptions](arkts-basicservices-osaccount-createosaccountoptions-i-sys.md) | 否 | 创建系统账号的选项，默认为空。<br/>从API version 12开始支持该可选参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;OsAccountInfo&gt; | Promise对象，返回新创建的系统账号的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes:1. The operation is restricted by the OS-account constraint.2. The required privilege for the operation has not been granted.<br>**适用版本：** 24+ |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localName, type or options. |
| [12300004](../../apis-basic-services-kit/errorcode-account.md#12300004-账号已存在) | Local name already exists.<br>**适用版本：** 12+ |
| [12300005](../../apis-basic-services-kit/errorcode-account.md#12300005-不支持多用户) | Multi-user not supported. |
| [12300006](../../apis-basic-services-kit/errorcode-account.md#12300006-不支持的账号类型) | Unsupported account type. |
| [12300007](../../apis-basic-services-kit/errorcode-account.md#12300007-账号数量已达上限) | The number of accounts has reached the upper limit. |
| [12300015](../../apis-basic-services-kit/errorcode-account.md#12300015-短名称已存在) | The short name already exists.<br>**适用版本：** 12+ |
| [12300023](../../apis-basic-services-kit/errorcode-account.md#12300023-指定类型的账号数量已达到上限) | The number of accounts of the specified type has reached the upper limit.<br>**适用版本：** 24+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let options: osAccount.CreateOsAccountOptions = {
  shortName: 'myShortName',
  disallowedPreinstalledBundles: [],
  allowedPreinstalledBundles: [],
}
try {
  accountManager.createOsAccount('testAccountName', osAccount.OsAccountType.NORMAL, options).then(
    (accountInfo: osAccount.OsAccountInfo) => {
    console.info('createOsAccount, accountInfo: ' + JSON.stringify(accountInfo));
  }).catch((err: BusinessError) => {
    console.error(`createOsAccount err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`createOsAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="createosaccountfordomain"></a>
## createOsAccountForDomain

```TypeScript
createOsAccountForDomain(
      type: OsAccountType,
      domainInfo: DomainAccountInfo,
      callback: AsyncCallback<OsAccountInfo>
    ): void
```

根据域账号信息，创建一个系统账号并将其与域账号关联。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-createOsAccountForDomain(
      type: OsAccountType,
      domainInfo: DomainAccountInfo,
      callback: AsyncCallback<OsAccountInfo>
    ): void--><!--Device-AccountManager-createOsAccountForDomain(
      type: OsAccountType,
      domainInfo: DomainAccountInfo,
      callback: AsyncCallback<OsAccountInfo>
    ): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [OsAccountType](arkts-basicservices-osaccount-osaccounttype-e-sys.md) | 是 | 创建的系统账号的类型。 |
| domainInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 是 | 域账号信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;OsAccountInfo&gt; | 是 | 回调函数。如果创建成功，err为null，data为新创建的系统账号的信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes:1. The operation is restricted by the OS-account constraint.2. The required privilege for the operation has not been granted.<br>**适用版本：** 24+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 12+ |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type or domainInfo. |
| [12300004](../../apis-basic-services-kit/errorcode-account.md#12300004-账号已存在) | Account already exists. |
| [12300005](../../apis-basic-services-kit/errorcode-account.md#12300005-不支持多用户) | Multi-user not supported. |
| [12300006](../../apis-basic-services-kit/errorcode-account.md#12300006-不支持的账号类型) | Unsupported account type. |
| [12300007](../../apis-basic-services-kit/errorcode-account.md#12300007-账号数量已达上限) | The number of accounts has reached the upper limit. |
| [12300023](../../apis-basic-services-kit/errorcode-account.md#12300023-指定类型的账号数量已达到上限) | The number of accounts of the specified type has reached the upper limit.<br>**适用版本：** 24+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let domainInfo: osAccount.DomainAccountInfo =
  {domain: 'testDomain', accountName: 'testAccountName'};
try {
  accountManager.createOsAccountForDomain(osAccount.OsAccountType.NORMAL, domainInfo,
    (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo)=>{
    if (err) {
      console.error(`createOsAccountForDomain exception:code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('createOsAccountForDomain osAccountInfo:' + JSON.stringify(osAccountInfo));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`createOsAccountForDomain exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="createosaccountfordomain-1"></a>
## createOsAccountForDomain

```TypeScript
createOsAccountForDomain(type: OsAccountType, domainInfo: DomainAccountInfo, options?: CreateOsAccountForDomainOptions): Promise<OsAccountInfo>
```

根据传入的域账号信息，创建与其关联的系统账号。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-createOsAccountForDomain(type: OsAccountType, domainInfo: DomainAccountInfo, options?: CreateOsAccountForDomainOptions): Promise<OsAccountInfo>--><!--Device-AccountManager-createOsAccountForDomain(type: OsAccountType, domainInfo: DomainAccountInfo, options?: CreateOsAccountForDomainOptions): Promise<OsAccountInfo>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [OsAccountType](arkts-basicservices-osaccount-osaccounttype-e-sys.md) | 是 | 创建的系统账号的类型。 |
| domainInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 是 | 域账号信息。 |
| options | [CreateOsAccountForDomainOptions](arkts-basicservices-osaccount-createosaccountfordomainoptions-i.md) | 否 | 创建账号的可选参数，默认为空。 <br/>从API version 12开始支持该可选参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;OsAccountInfo&gt; | Promise对象，返回新创建的系统账号的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes:1. The operation is restricted by the OS-account constraint.2. The required privilege for the operation has not been granted.<br>**适用版本：** 24+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 12+ |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type, domainInfo or options. |
| [12300004](../../apis-basic-services-kit/errorcode-account.md#12300004-账号已存在) | Account already exists. |
| [12300005](../../apis-basic-services-kit/errorcode-account.md#12300005-不支持多用户) | Multi-user not supported. |
| [12300006](../../apis-basic-services-kit/errorcode-account.md#12300006-不支持的账号类型) | Unsupported account type. |
| [12300007](../../apis-basic-services-kit/errorcode-account.md#12300007-账号数量已达上限) | The number of accounts has reached the upper limit. |
| [12300015](../../apis-basic-services-kit/errorcode-account.md#12300015-短名称已存在) | The short name already exists.<br>**适用版本：** 12+ |
| [12300023](../../apis-basic-services-kit/errorcode-account.md#12300023-指定类型的账号数量已达到上限) | The number of accounts of the specified type has reached the upper limit.<br>**适用版本：** 24+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let domainInfo: osAccount.DomainAccountInfo =
  {domain: 'testDomain', accountName: 'testAccountName'};
let options: osAccount.CreateOsAccountForDomainOptions = {
  shortName: 'myShortName'
}
try {
  accountManager.createOsAccountForDomain(osAccount.OsAccountType.NORMAL, domainInfo, options).then(
    (accountInfo: osAccount.OsAccountInfo) => {
    console.info('createOsAccountForDomain, account info: ' + JSON.stringify(accountInfo));
  }).catch((err: BusinessError) => {
    console.error(`createOsAccountForDomain err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`createOsAccountForDomain exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="deactivateosaccount"></a>
## deactivateOsAccount

```TypeScript
deactivateOsAccount(localId: number): Promise<void>
```

注销（退出登录）指定系统账号。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

<!--Device-AccountManager-deactivateOsAccount(localId: int): Promise<void>--><!--Device-AccountManager-deactivateOsAccount(localId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Service busy. Possible causes: The target account is being operated. |

**示例：**

注销ID为100的系统账号。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.deactivateOsAccount(localId).then(() => {
    console.info('deactivateOsAccount successfully');
  }).catch((err: BusinessError) => {
    console.error(`deactivateOsAccount failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`deactivateOsAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="getbundleidforuid"></a>
## getBundleIdForUid

```TypeScript
getBundleIdForUid(uid: number, callback: AsyncCallback<number>): void
```

通过uid查询对应的bundleId。使用callback异步回调。

**起始版本：** 9

<!--Device-AccountManager-getBundleIdForUid(uid: int, callback: AsyncCallback<int>): void--><!--Device-AccountManager-getBundleIdForUid(uid: int, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 进程uid。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果查询成功，err为null，data为与uid对应的bundleId；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid uid. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// uid为进程uid，请通过应用信息获取
let testUid: number = 1000000;
try {
  accountManager.getBundleIdForUid(testUid, (err: BusinessError, bundleId: number) => {
    if (err) {
      console.error(`getBundleIdForUid errInfo:code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getBundleIdForUid bundleId:' + JSON.stringify(bundleId));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getBundleIdForUid exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="getbundleidforuid-1"></a>
## getBundleIdForUid

```TypeScript
getBundleIdForUid(uid: number): Promise<number>
```

通过uid查询对应的bundleId。使用Promise异步回调。

**起始版本：** 9

<!--Device-AccountManager-getBundleIdForUid(uid: int): Promise<int>--><!--Device-AccountManager-getBundleIdForUid(uid: int): Promise<int>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 进程uid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回与uid对应的bundleId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid uid. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let testUid: number = 1000000;
try {
  accountManager.getBundleIdForUid(testUid).then((result: number) => {
    console.info('getBundleIdForUid bundleId:' + JSON.stringify(result));
  }).catch((err: BusinessError) => {
    console.error(`getBundleIdForUid errInfo:code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getBundleIdForUid exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="getbundleidforuidsync"></a>
## getBundleIdForUidSync

```TypeScript
getBundleIdForUidSync(uid: number): number
```

通过uid查询对应的bundleId。使用同步方式返回结果。

**起始版本：** 10

<!--Device-AccountManager-getBundleIdForUidSync(uid: int): int--><!--Device-AccountManager-getBundleIdForUidSync(uid: int): int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 进程uid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 表示与进程uid对应的bundleId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid uid. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let testUid: number = 1000000;
try {
  let bundleId : number = accountManager.getBundleIdForUidSync(testUid);
  console.info('getBundleIdForUidSync bundleId:' + bundleId);
} catch (e) {
  const err = e as BusinessError;
  console.error(`getBundleIdForUidSync exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="getenabledosaccountconstraints"></a>
## getEnabledOsAccountConstraints

```TypeScript
getEnabledOsAccountConstraints(localId: number): Promise<Array<string>>
```

获取指定系统账号已使能的全部约束。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-AccountManager-getEnabledOsAccountConstraints(localId: int): Promise<Array<string>>--><!--Device-AccountManager-getEnabledOsAccountConstraints(localId: int): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回指定系统账号已使能的全部[约束](docroot://reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

获取ID为100的系统账号的全部约束。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.getEnabledOsAccountConstraints(localId).then((constraints: string[]) => {
    console.info('getEnabledOsAccountConstraints, constraints: ' + constraints);
  }).catch((err: BusinessError) => {
    console.error(`getEnabledOsAccountConstraints err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getEnabledOsAccountConstraints exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="getforegroundosaccountdisplayid"></a>
## getForegroundOsAccountDisplayId

```TypeScript
getForegroundOsAccountDisplayId(localId: number): Promise<number>
```

获取指定前台系统账号所运行的逻辑屏ID。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-AccountManager-getForegroundOsAccountDisplayId(localId: int): Promise<long>--><!--Device-AccountManager-getForegroundOsAccountDisplayId(localId: int): Promise<long>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回逻辑屏ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300017](../../apis-basic-services-kit/errorcode-account.md#12300017-前台系统账号未找到) | The foreground OS account is not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.getForegroundOsAccountDisplayId(localId).then((displayId: number) => {
    console.info('account ' + localId + ' foreground displayId: ' + displayId);
  }).catch((err: BusinessError) => {
    console.error(`getForegroundOsAccountDisplayId failed: ${err.code} ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getForegroundOsAccountDisplayId exception: ${err.code} ${err.message}`);
}

```

<a id="getforegroundosaccountlocalid"></a>
## getForegroundOsAccountLocalId

```TypeScript
getForegroundOsAccountLocalId(displayId: number): Promise<number>
```

获取指定逻辑屏上运行的前台系统账号ID。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-AccountManager-getForegroundOsAccountLocalId(displayId: long): Promise<int>--><!--Device-AccountManager-getForegroundOsAccountLocalId(displayId: long): Promise<int>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 逻辑屏ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回系统账号ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300017](../../apis-basic-services-kit/errorcode-account.md#12300017-前台系统账号未找到) | The foreground OS account is not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let displayId: number = 0;
try {
  accountManager.getForegroundOsAccountLocalId(displayId).then((localId: number) => {
    console.info('foreground account on display ' + displayId + ' is ' + localId);
  }).catch((err: BusinessError) => {
    console.error(`getForegroundOsAccountLocalId failed: ${err.code} ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getForegroundOsAccountLocalId exception: ${err.code} ${err.message}`);
}

```

<a id="getosaccountconstraintsourcetypes"></a>
## getOsAccountConstraintSourceTypes

```TypeScript
getOsAccountConstraintSourceTypes(localId: number, constraint: string, callback: AsyncCallback<Array<ConstraintSourceTypeInfo>>): void
```

查询指定系统账号的指定约束来源信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-getOsAccountConstraintSourceTypes(localId: int, constraint: string, callback: AsyncCallback<Array<ConstraintSourceTypeInfo>>): void--><!--Device-AccountManager-getOsAccountConstraintSourceTypes(localId: int, constraint: string, callback: AsyncCallback<Array<ConstraintSourceTypeInfo>>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 要查询的系统账号ID。 |
| constraint | string | 是 | 要查询的[约束](docroot://reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)名称。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;ConstraintSourceTypeInfo&gt;&gt; | 是 | 回调函数。如果成功，err为null，data为指定系统账号的指定[约束](docroot://reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)来源信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or constraint. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountConstraintSourceTypes(100, 'constraint.wifi',
    (err: BusinessError,sourceTypeInfos: osAccount.ConstraintSourceTypeInfo[])=>{
    if (err) {
      console.error(`getOsAccountConstraintSourceTypes errInfo:code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountConstraintSourceTypes sourceTypeInfos:' + JSON.stringify(sourceTypeInfos));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountConstraintSourceTypes exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="getosaccountconstraintsourcetypes-1"></a>
## getOsAccountConstraintSourceTypes

```TypeScript
getOsAccountConstraintSourceTypes(localId: number, constraint: string): Promise<Array<ConstraintSourceTypeInfo>>
```

查询指定系统账号的指定约束来源信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-getOsAccountConstraintSourceTypes(localId: int, constraint: string): Promise<Array<ConstraintSourceTypeInfo>>--><!--Device-AccountManager-getOsAccountConstraintSourceTypes(localId: int, constraint: string): Promise<Array<ConstraintSourceTypeInfo>>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 要查询的系统账号ID。 |
| constraint | string | 是 | 要查询的[约束](docroot://reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ConstraintSourceTypeInfo&gt;&gt; | Promise对象，返回指定系统账号的指定[约束](docroot://reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)来源信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or constraint. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountConstraintSourceTypes(100, 'constraint.wifi').then(
    (result: osAccount.ConstraintSourceTypeInfo[]) => {
    console.info('getOsAccountConstraintSourceTypes sourceTypeInfos:' + JSON.stringify(result));
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountConstraintSourceTypes errInfo:code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountConstraintSourceTypes exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="getosaccountprofilephoto"></a>
## getOsAccountProfilePhoto

```TypeScript
getOsAccountProfilePhoto(localId: number, callback: AsyncCallback<string>): void
```

获取指定系统账号的头像信息。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-getOsAccountProfilePhoto(localId: int, callback: AsyncCallback<string>): void--><!--Device-AccountManager-getOsAccountProfilePhoto(localId: int, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。如果获取成功，err为null，data为指定系统账号的头像信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

获取ID为100的系统账号的头像。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.getOsAccountProfilePhoto(localId, (err: BusinessError, photo: string)=>{
    if (err) {
      console.error(`getOsAccountProfilePhoto exception:code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('get photo:' + photo + ' by localId: ' + localId);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountProfilePhoto exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="getosaccountprofilephoto-1"></a>
## getOsAccountProfilePhoto

```TypeScript
getOsAccountProfilePhoto(localId: number): Promise<string>
```

获取指定系统账号的头像信息。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-getOsAccountProfilePhoto(localId: int): Promise<string>--><!--Device-AccountManager-getOsAccountProfilePhoto(localId: int): Promise<string>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回指定系统账号的头像信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

获取ID为100的系统账号的头像。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.getOsAccountProfilePhoto(localId).then((photo: string) => {
    console.info('getOsAccountProfilePhoto: ' + photo);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountProfilePhoto err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountProfilePhoto exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="getosaccounttype"></a>
## getOsAccountType

```TypeScript
getOsAccountType(localId: number): Promise<OsAccountType>
```

查询指定系统账号的类型。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-AccountManager-getOsAccountType(localId: int): Promise<OsAccountType>--><!--Device-AccountManager-getOsAccountType(localId: int): Promise<OsAccountType>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 要查询的系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;OsAccountType&gt; | Promise对象，返回指定系统账号的类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  let localId: number = 100;
  accountManager.getOsAccountType(localId).then((type: osAccount.OsAccountType) => {
    console.info('getOsAccountType Type:' + type);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountType errInfo:code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountType exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="ismainosaccount"></a>
## isMainOsAccount

```TypeScript
isMainOsAccount(callback: AsyncCallback<boolean>): void
```

查询当前进程是否处于主用户。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-isMainOsAccount(callback: AsyncCallback<boolean>): void--><!--Device-AccountManager-isMainOsAccount(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数，返回true表示当前账号为主账号，返回false表示当前账号非主账号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.isMainOsAccount((err: BusinessError,result: boolean)=>{
    if (err) {
      console.error(`isMainOsAccount errInfo:code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('isMainOsAccount result:' + JSON.stringify(result));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`isMainOsAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="ismainosaccount-1"></a>
## isMainOsAccount

```TypeScript
isMainOsAccount(): Promise<boolean>
```

查询当前进程是否处于主用户。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-isMainOsAccount(): Promise<boolean>--><!--Device-AccountManager-isMainOsAccount(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回true表示当前账号为主账号，返回false表示当前账号非主账号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.isMainOsAccount().then((result: boolean) => {
    console.info('isMainOsAccount result:' + JSON.stringify(result));
  }).catch((err: BusinessError) => {
    console.error(`isMainOsAccount errInfo:code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`isMainOsAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="isosaccountactivated"></a>
## isOsAccountActivated

```TypeScript
isOsAccountActivated(localId: number): Promise<boolean>
```

判断指定系统账号是否处于激活状态。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-AccountManager-isOsAccountActivated(localId: int): Promise<boolean>--><!--Device-AccountManager-isOsAccountActivated(localId: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示账号已激活；返回false表示账号未激活。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

判断ID为100的系统账号是否处于激活状态。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.isOsAccountActivated(localId).then((isActivated: boolean) => {
    console.info('isOsAccountActivated successfully, isActivated: ' + isActivated);
  }).catch((err: BusinessError) => {
    console.error(`isOsAccountActivated failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`isOsAccountActivated exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="isosaccountconstraintenabled"></a>
## isOsAccountConstraintEnabled

```TypeScript
isOsAccountConstraintEnabled(localId: number, constraint: string): Promise<boolean>
```

判断指定系统账号是否使能指定约束。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-AccountManager-isOsAccountConstraintEnabled(localId: int, constraint: string): Promise<boolean>--><!--Device-AccountManager-isOsAccountConstraintEnabled(localId: int, constraint: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| constraint | string | 是 | 指定的[约束](docroot://reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示已使能指定的约束；返回false表示未使能指定的约束。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

判断ID为100的系统账号是否有禁止使用Wi-Fi的约束。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
let constraint: string = 'constraint.wifi';
try {
  accountManager.isOsAccountConstraintEnabled(localId, constraint).then((isEnabled: boolean) => {
    console.info('isOsAccountConstraintEnabled successfully, isEnabled: ' + isEnabled);
  }).catch((err: BusinessError) => {
    console.error(`isOsAccountConstraintEnabled failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`isOsAccountConstraintEnabled exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="isosaccountunlocked"></a>
## isOsAccountUnlocked

```TypeScript
isOsAccountUnlocked(localId: number): Promise<boolean>
```

检查指定系统账号是否已验证。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-AccountManager-isOsAccountUnlocked(localId: int): Promise<boolean>--><!--Device-AccountManager-isOsAccountUnlocked(localId: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。不填则检查当前系统账号是否已验证。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前账号已认证解锁；返回false表示当前账号未认证解锁。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.isOsAccountUnlocked(localId).then((isVerified: boolean) => {
    console.info('isOsAccountUnlocked successfully, isVerified: ' + isVerified);
  }).catch((err: BusinessError) => {
    console.error(`isOsAccountUnlocked failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`isOsAccountUnlocked exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="off"></a>
## off('activate' | 'activating')

```TypeScript
off(type: 'activate' | 'activating', name: string, callback?: Callback<number>): void
```

取消订阅系统账号的激活完成与激活中的事件。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

<!--Device-AccountManager-off(type: 'activate' | 'activating', name: string, callback?: Callback<int>): void--><!--Device-AccountManager-off(type: 'activate' | 'activating', name: string, callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activate' \| 'activating' | 是 | 取消订阅类型，activate表示取消订阅账号已激活完成的事件，activating取消订阅账号正在激活的事件。 |
| name | string | 是 | 订阅名称，可自定义，要求非空且长度不超过1024字节，需要与订阅接口传入的值保持一致。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;number&gt; | 否 | 取消订阅系统账号激活完成与激活中的事件回调，默认为空，表示取消该类型事件的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type or name. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();

function offCallback(){
  console.info('off enter')
}

try {
  accountManager.off('activating', 'osAccountOnOffNameA', offCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`off exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="off-1"></a>
## off('activate' | 'activating')

```TypeScript
off(type: 'activate' | 'activating', name: string, callback?: Callback<number>): void
```

取消订阅系统账号的激活完成与激活中的事件。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

<!--Device-AccountManager-off(type: 'activate' | 'activating', name: string, callback?: Callback<int>): void--><!--Device-AccountManager-off(type: 'activate' | 'activating', name: string, callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activate' \| 'activating' | 是 | 取消订阅类型，activate表示取消订阅账号已激活完成的事件，activating取消订阅账号正在激活的事件。 |
| name | string | 是 | 订阅名称，可自定义，要求非空且长度不超过1024字节，需要与订阅接口传入的值保持一致。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;number&gt; | 否 | 取消订阅系统账号激活完成与激活中的事件回调，默认为空，表示取消该类型事件的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type or name. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();

function offCallback(){
  console.info('off enter')
}

try {
  accountManager.off('activating', 'osAccountOnOffNameA', offCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`off exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="off-2"></a>
## off('switching')

```TypeScript
off(type: 'switching', callback?: Callback<OsAccountSwitchEventData>): void
```

取消订阅系统账号的前后台正在切换事件。使用callback异步回调。

**起始版本：** 12

**需要权限：** 
- API版本23+：ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS
- API版本12 - 22：ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-off(type: 'switching', callback?: Callback<OsAccountSwitchEventData>): void--><!--Device-AccountManager-off(type: 'switching', callback?: Callback<OsAccountSwitchEventData>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'switching' | 是 | 取消订阅类型，switching表示取消订阅的是系统账号的前后台正在切换事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;OsAccountSwitchEventData&gt; | 否 | 取消订阅系统账号的前后台正在切换事件回调，默认为空，表示取消该类型事件的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.off('switching');
} catch (e) {
  const err = e as BusinessError;
  console.error(`off exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="off-3"></a>
## off('switched')

```TypeScript
off(type: 'switched', callback?: Callback<OsAccountSwitchEventData>): void
```

取消订阅系统账号的前后台切换结束事件。使用callback异步回调。

**起始版本：** 12

**需要权限：** 
- API版本23+：ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS
- API版本12 - 22：ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-off(type: 'switched', callback?: Callback<OsAccountSwitchEventData>): void--><!--Device-AccountManager-off(type: 'switched', callback?: Callback<OsAccountSwitchEventData>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'switched' | 是 | 取消订阅类型，switched表示取消订阅的是系统账号的前后台切换结束事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;OsAccountSwitchEventData&gt; | 否 | 取消订阅系统账号的前后台切换结束事件回调，默认为空，表示取消该类型事件的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.off('switched');
} catch (e) {
  const err = e as BusinessError;
  console.error(`off exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="offconstraintchanged"></a>
## offConstraintChanged

```TypeScript
offConstraintChanged(callback?: Callback<ConstraintChangeInfo>): void
```

取消与指定回调关联的约束变更订阅记录。若未指定回调，则取消所有订阅记录。

**起始版本：** 23

<!--Device-AccountManager-offConstraintChanged(callback?: Callback<ConstraintChangeInfo>): void--><!--Device-AccountManager-offConstraintChanged(callback?: Callback<ConstraintChangeInfo>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ConstraintChangeInfo&gt; | 否 | 表示用于接收约束变更事件的回调函数。<br>默认为undefined，表示清除所有订阅记录。<br>非undefined时，表示清除与该回调函数关联的订阅记录。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let constraint: string = 'constraint.wifi';
const callback:Callback<osAccount.ConstraintChangeInfo> = (data: osAccount.ConstraintChangeInfo): void => {
  console.info(`ConstraintChangeInfo received, constraint: ${data.constraint} isEnabled: ${data.isEnabled}`);
};

try {
  accountManager.onConstraintChanged([constraint], callback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`onConstraintChanged exception: code is ${err.code}, message is ${err.message}`);
}

try {
  accountManager.offConstraintChanged(callback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`offConstraintChanged exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="on"></a>
## on('activate' | 'activating')

```TypeScript
on(type: 'activate' | 'activating', name: string, callback: Callback<number>): void
```

订阅系统账号的激活完成与激活中的事件。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

<!--Device-AccountManager-on(type: 'activate' | 'activating', name: string, callback: Callback<int>): void--><!--Device-AccountManager-on(type: 'activate' | 'activating', name: string, callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activate' \| 'activating' | 是 | 订阅类型，activate表示订阅的是账号已激活完成的事件，activating表示订阅的是账号正在激活的事件。 |
| name | string | 是 | 订阅名称，可自定义，要求非空且长度不超过1024字节。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;number&gt; | 是 | 订阅系统账号激活完成与激活中的事件回调，表示激活完成后或正在激活中的系统账号ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type or name. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();

function onCallback(receiveLocalId: number){
  console.info('receive localId:' + receiveLocalId);
}

try {
  accountManager.on('activating', 'osAccountOnOffNameA', onCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`receive localId exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="on-1"></a>
## on('activate' | 'activating')

```TypeScript
on(type: 'activate' | 'activating', name: string, callback: Callback<number>): void
```

订阅系统账号的激活完成与激活中的事件。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

<!--Device-AccountManager-on(type: 'activate' | 'activating', name: string, callback: Callback<int>): void--><!--Device-AccountManager-on(type: 'activate' | 'activating', name: string, callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activate' \| 'activating' | 是 | 订阅类型，activate表示订阅的是账号已激活完成的事件，activating表示订阅的是账号正在激活的事件。 |
| name | string | 是 | 订阅名称，可自定义，要求非空且长度不超过1024字节。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;number&gt; | 是 | 订阅系统账号激活完成与激活中的事件回调，表示激活完成后或正在激活中的系统账号ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type or name. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();

function onCallback(receiveLocalId: number){
  console.info('receive localId:' + receiveLocalId);
}

try {
  accountManager.on('activating', 'osAccountOnOffNameA', onCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`receive localId exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="on-2"></a>
## on('switching')

```TypeScript
on(type: 'switching', callback: Callback<OsAccountSwitchEventData>): void
```

订阅系统账号的前后台正在切换事件。使用callback异步回调。

**起始版本：** 12

**需要权限：** 
- API版本23+：ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS
- API版本12 - 22：ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-on(type: 'switching', callback: Callback<OsAccountSwitchEventData>): void--><!--Device-AccountManager-on(type: 'switching', callback: Callback<OsAccountSwitchEventData>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'switching' | 是 | 订阅类型，switching表示订阅的是系统账号的前后台正在切换事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;OsAccountSwitchEventData&gt; | 是 | 订阅系统账号的前后台正在切换事件回调，包含切换来源和切换目标的系统账号ID。<br/>**说明：** 从API version23开始，事件数据中新增可选字段displayId，表示发生切换事件的逻辑屏ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();

function onSwitchingCallback(eventData: osAccount.OsAccountSwitchEventData){
  console.info('receive eventData:' + JSON.stringify(eventData));
}

try {
  accountManager.on('switching', onSwitchingCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`receive eventData exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="on-3"></a>
## on('switched')

```TypeScript
on(type: 'switched', callback: Callback<OsAccountSwitchEventData>): void
```

订阅系统账号的前后台切换结束事件。使用callback异步回调。

**起始版本：** 12

**需要权限：** 
- API版本23+：ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS
- API版本12 - 22：ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-on(type: 'switched', callback: Callback<OsAccountSwitchEventData>): void--><!--Device-AccountManager-on(type: 'switched', callback: Callback<OsAccountSwitchEventData>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'switched' | 是 | 订阅类型，switched表示订阅的是系统账号的前后台切换结束事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;OsAccountSwitchEventData&gt; | 是 | 订阅系统账号的前后台切换结束事件回调，包含切换来源和切换目标的系统账号ID。<br/>**说明：** 从API version23开始，事件数据中新增可选字段displayId，表示发生切换事件的逻辑屏ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();

function onSwitchedCallback(eventData: osAccount.OsAccountSwitchEventData){
  console.info('receive eventData:' + JSON.stringify(eventData));
}

try {
  accountManager.on('switched', onSwitchedCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`receive eventData exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="onconstraintchanged"></a>
## onConstraintChanged

```TypeScript
onConstraintChanged(constraints: string[], callback: Callback<ConstraintChangeInfo>): void
```

订阅调用方所属系统账号的一种或多种约束变更事件。使用callback异步回调。

**起始版本：** 23

<!--Device-AccountManager-onConstraintChanged(constraints: string[], callback: Callback<ConstraintChangeInfo>): void--><!--Device-AccountManager-onConstraintChanged(constraints: string[], callback: Callback<ConstraintChangeInfo>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraints | string[] | 是 | 表示待订阅的[约束](docroot://reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)列表。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ConstraintChangeInfo&gt; | 是 | 表示用于接收约束变更事件的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | One or more constraints are invalid. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let constraint: string = 'constraint.wifi';
const callback:Callback<osAccount.ConstraintChangeInfo> = (data: osAccount.ConstraintChangeInfo): void => {
  console.info(`ConstraintChangeInfo received, constraint: ${data.constraint} isEnabled: ${data.isEnabled}`);
};

try {
  accountManager.onConstraintChanged([constraint], callback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`onConstraintChanged exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="queryallcreatedosaccounts"></a>
## queryAllCreatedOsAccounts

```TypeScript
queryAllCreatedOsAccounts(callback: AsyncCallback<Array<OsAccountInfo>>): void
```

查询已创建的所有系统账号的信息列表。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-queryAllCreatedOsAccounts(callback: AsyncCallback<Array<OsAccountInfo>>): void--><!--Device-AccountManager-queryAllCreatedOsAccounts(callback: AsyncCallback<Array<OsAccountInfo>>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;OsAccountInfo&gt;&gt; | 是 | 回调函数。如果查询成功，err为null，data为已创建的所有系统账号的信息列表；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.queryAllCreatedOsAccounts((err: BusinessError, accountArr: osAccount.OsAccountInfo[])=>{
    if (err) {
      console.error(`queryAllCreatedOsAccounts exception:code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('queryAllCreatedOsAccounts accountArr:' + JSON.stringify(accountArr));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryAllCreatedOsAccounts exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="queryallcreatedosaccounts-1"></a>
## queryAllCreatedOsAccounts

```TypeScript
queryAllCreatedOsAccounts(): Promise<Array<OsAccountInfo>>
```

查询已创建的所有系统账号的信息列表。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-queryAllCreatedOsAccounts(): Promise<Array<OsAccountInfo>>--><!--Device-AccountManager-queryAllCreatedOsAccounts(): Promise<Array<OsAccountInfo>>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;OsAccountInfo&gt;&gt; | Promise对象，返回已创建的所有系统账号的信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.queryAllCreatedOsAccounts().then((accountArr: osAccount.OsAccountInfo[]) => {
    console.info('queryAllCreatedOsAccounts, accountArr: ' + JSON.stringify(accountArr));
  }).catch((err: BusinessError) => {
    console.error(`queryAllCreatedOsAccounts err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryAllCreatedOsAccounts exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="querymaxloggedinosaccountnumber"></a>
## queryMaxLoggedInOsAccountNumber

```TypeScript
queryMaxLoggedInOsAccountNumber(): Promise<number>
```

查询允许同时登录的系统账号的最大数量。使用Promise异步回调。

**起始版本：** 12

<!--Device-AccountManager-queryMaxLoggedInOsAccountNumber(): Promise<int>--><!--Device-AccountManager-queryMaxLoggedInOsAccountNumber(): Promise<int>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回允许登录的系统账号的最大数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.queryMaxLoggedInOsAccountNumber().then((maxNum: number) => {
    console.info('queryMaxLoggedInOsAccountNumber successfully, maxNum: ' + maxNum);
  }).catch((err: BusinessError) => {
    console.error(`queryMaxLoggedInOsAccountNumber failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryMaxLoggedInOsAccountNumber exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="querymaxosaccountnumber"></a>
## queryMaxOsAccountNumber

```TypeScript
queryMaxOsAccountNumber(callback: AsyncCallback<number>): void
```

查询允许创建的系统账号的最大数量。使用callback异步回调。

**起始版本：** 7

<!--Device-AccountManager-queryMaxOsAccountNumber(callback: AsyncCallback<int>): void--><!--Device-AccountManager-queryMaxOsAccountNumber(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，如果查询成功，err为null，data为允许创建的系统账号的最大数量；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.queryMaxOsAccountNumber((err: BusinessError, maxCnt: number) => {
    if (err) {
      console.error(`queryMaxOsAccountNumber failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('queryMaxOsAccountNumber successfully, maxCnt:' + maxCnt);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryMaxOsAccountNumber exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="querymaxosaccountnumber-1"></a>
## queryMaxOsAccountNumber

```TypeScript
queryMaxOsAccountNumber(): Promise<number>
```

查询允许创建的系统账号的最大数量。使用Promise异步回调。

**起始版本：** 7

<!--Device-AccountManager-queryMaxOsAccountNumber(): Promise<int>--><!--Device-AccountManager-queryMaxOsAccountNumber(): Promise<int>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回允许创建的系统账号的最大数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.queryMaxOsAccountNumber().then((maxCnt: number) => {
    console.info('queryMaxOsAccountNumber successfully, maxCnt: ' + maxCnt);
  }).catch((err: BusinessError) => {
    console.error(`queryMaxOsAccountNumber failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryMaxOsAccountNumber exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="queryosaccount"></a>
## queryOsAccount

```TypeScript
queryOsAccount(): Promise<OsAccountInfo>
```

查询当前进程所属的系统账号的信息。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.GET_LOCAL_ACCOUNTS

<!--Device-AccountManager-queryOsAccount(): Promise<OsAccountInfo>--><!--Device-AccountManager-queryOsAccount(): Promise<OsAccountInfo>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;OsAccountInfo&gt; | Promise对象，返回当前进程所属的系统账号信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.queryOsAccount().then((accountInfo: osAccount.OsAccountInfo) => {
    console.info('queryOsAccount, accountInfo: ' + JSON.stringify(accountInfo));
  }).catch((err: BusinessError) => {
    console.error(`queryOsAccount err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryOsAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="queryosaccountbyid"></a>
## queryOsAccountById

```TypeScript
queryOsAccountById(localId: number, callback: AsyncCallback<OsAccountInfo>): void
```

查询指定系统账号的信息。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

<!--Device-AccountManager-queryOsAccountById(localId: int, callback: AsyncCallback<OsAccountInfo>): void--><!--Device-AccountManager-queryOsAccountById(localId: int, callback: AsyncCallback<OsAccountInfo>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 要查询的系统账号的ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;OsAccountInfo&gt; | 是 | 回调函数。如果查询成功，err为null，data为查到的系统账号的信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

查询ID为100的系统账号信息。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.queryOsAccountById(localId, (err: BusinessError, accountInfo: osAccount.OsAccountInfo)=>{
    if (err) {
      console.error(`queryOsAccountById exception:code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('queryOsAccountById accountInfo:' + JSON.stringify(accountInfo));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryOsAccountById exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="queryosaccountbyid-1"></a>
## queryOsAccountById

```TypeScript
queryOsAccountById(localId: number): Promise<OsAccountInfo>
```

查询指定系统账号的信息。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

<!--Device-AccountManager-queryOsAccountById(localId: int): Promise<OsAccountInfo>--><!--Device-AccountManager-queryOsAccountById(localId: int): Promise<OsAccountInfo>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 要查询的系统账号的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;OsAccountInfo&gt; | Promise对象，返回查到的系统账号的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

查询ID为100的系统账号信息。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.queryOsAccountById(localId).then((accountInfo: osAccount.OsAccountInfo) => {
    console.info('queryOsAccountById, accountInfo: ' + JSON.stringify(accountInfo));
  }).catch((err: BusinessError) => {
    console.error(`queryOsAccountById err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryOsAccountById exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="removeosaccount"></a>
## removeOsAccount

```TypeScript
removeOsAccount(localId: number, callback: AsyncCallback<void>): void
```

删除指定系统账号。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-removeOsAccount(localId: int, callback: AsyncCallback<void>): void--><!--Device-AccountManager-removeOsAccount(localId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。如果删除账号成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes:1. The operation is restricted by the OS-account constraint.2. The required privilege for the operation has not been granted.<br>**适用版本：** 24+ |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Service busy. Possible causes: The target account is being operated on. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let accountName: string = 'testAccountName';
try {
  accountManager.createOsAccount(accountName, osAccount.OsAccountType.NORMAL,
    (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo) => {
      accountManager.removeOsAccount(osAccountInfo.localId, (err: BusinessError)=>{
        if (err) {
          console.error(`removeOsAccount failed, code is ${err.code}, message is ${err.message}`);
        } else {
          console.info('removeOsAccount successfully');
        }
    });
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`removeOsAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="removeosaccount-1"></a>
## removeOsAccount

```TypeScript
removeOsAccount(localId: number): Promise<void>
```

删除指定系统账号。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-removeOsAccount(localId: int): Promise<void>--><!--Device-AccountManager-removeOsAccount(localId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes:1. The operation is restricted by the OS-account constraint.2. The required privilege for the operation has not been granted.<br>**适用版本：** 24+ |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Service busy. Possible causes: The target account is being operated. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let accountName: string = 'testAccountName';
try {
  accountManager.createOsAccount(accountName, osAccount.OsAccountType.NORMAL,
    (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo)=>{
      accountManager.removeOsAccount(osAccountInfo.localId).then(() => {
        console.info('removeOsAccount successfully');
      }).catch((err: BusinessError) => {
        console.error(`removeOsAccount failed, code is ${err.code}, message is ${err.message}`);
      });
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`removeOsAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="removeosaccount-2"></a>
## removeOsAccount

```TypeScript
removeOsAccount(localId: number, options: RemoveOsAccountOptions): Promise<void>
```

根据删除选项，删除指定系统账号。使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-removeOsAccount(localId: int, options: RemoveOsAccountOptions): Promise<void>--><!--Device-AccountManager-removeOsAccount(localId: int, options: RemoveOsAccountOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| options | [RemoveOsAccountOptions](arkts-basicservices-osaccount-removeosaccountoptions-i-sys.md) | 是 | 删除系统账号的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes:1. The operation is restricted by the OS-account constraint.2. The required privilege for the operation has not been granted. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId or options. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Service busy. Possible causes: The target account is being operated on. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let accountName: string = 'testAccountName';
let token: Uint8Array = new Uint8Array([0]);
let options: osAccount.RemoveOsAccountOptions = {
  token: token,
}
try {
  accountManager.createOsAccount(accountName, osAccount.OsAccountType.NORMAL,
    (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo)=>{
      accountManager.removeOsAccount(osAccountInfo.localId, options).then(() => {
        console.info('removeOsAccount successfully');
      }).catch((err: BusinessError) => {
        console.error(`removeOsAccount failed, code is ${err.code}, message is ${err.message}`);
      });
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`removeOsAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="setosaccountconstraints"></a>
## setOsAccountConstraints

```TypeScript
setOsAccountConstraints(localId: number, constraints: Array<string>, enable: boolean, callback: AsyncCallback<void>): void
```

为指定系统账号设置/删除约束。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-setOsAccountConstraints(localId: int, constraints: Array<string>, enable: boolean, callback: AsyncCallback<void>): void--><!--Device-AccountManager-setOsAccountConstraints(localId: int, constraints: Array<string>, enable: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| constraints | Array&lt;string&gt; | 是 | 待设置/删除的[约束](docroot://reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)列表。 |
| enable | boolean | 是 | 设置(true)/删除(false) 。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。如果设置成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId or constraints. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |

**示例：**

给ID为100的系统账号设置禁止使用Wi-Fi的约束。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
let constraint: string = 'constraint.wifi';
try {
  accountManager.setOsAccountConstraints(localId, [constraint], true, (err: BusinessError) => {
    if (err) {
      console.error(`setOsAccountConstraints failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setOsAccountConstraints successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountConstraints exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="setosaccountconstraints-1"></a>
## setOsAccountConstraints

```TypeScript
setOsAccountConstraints(localId: number, constraints: Array<string>, enable: boolean): Promise<void>
```

为指定系统账号设置/删除约束。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-setOsAccountConstraints(localId: int, constraints: Array<string>, enable: boolean): Promise<void>--><!--Device-AccountManager-setOsAccountConstraints(localId: int, constraints: Array<string>, enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| constraints | Array&lt;string&gt; | 是 | 待设置/删除的[约束](docroot://reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)列表。 |
| enable | boolean | 是 | 设置(true)/删除(false)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId or constraints. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |

**示例：**

删除ID为100的系统账号的禁止使用Wi-Fi的约束。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
try {
  accountManager.setOsAccountConstraints(localId, ['constraint.location.set'], false).then(() => {
    console.info('setOsAccountConstraints successfully');
  }).catch((err: BusinessError) => {
    console.error(`setOsAccountConstraints failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountConstraints exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="setosaccountname"></a>
## setOsAccountName

```TypeScript
setOsAccountName(localId: number, localName: string, callback: AsyncCallback<void>): void
```

设置指定系统账号的账号名。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-setOsAccountName(localId: int, localName: string, callback: AsyncCallback<void>): void--><!--Device-AccountManager-setOsAccountName(localId: int, localName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| localName | string | 是 | 账号名，最大长度为1024个字符。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。如果设置成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId or localName. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |

**示例：**

将ID为100的系统账号的账号名设置成demoName。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
let name: string = 'demoName';
try {
  accountManager.setOsAccountName(localId, name, (err: BusinessError) => {
    if (err) {
      console.error(`setOsAccountName failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setOsAccountName successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountName exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="setosaccountname-1"></a>
## setOsAccountName

```TypeScript
setOsAccountName(localId: number, localName: string): Promise<void>
```

设置指定系统账号的账号名。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-setOsAccountName(localId: int, localName: string): Promise<void>--><!--Device-AccountManager-setOsAccountName(localId: int, localName: string): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| localName | string | 是 | 账号名，最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId or localName. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |

**示例：**

将ID为100的系统账号的账号名设置成demoName。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
let name: string = 'testName';
try {
  accountManager.setOsAccountName(localId, name).then(() => {
    console.info('setOsAccountName successfully');
  }).catch((err: BusinessError) => {
    console.error(`setOsAccountName failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountName exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="setosaccountprofilephoto"></a>
## setOsAccountProfilePhoto

```TypeScript
setOsAccountProfilePhoto(localId: number, photo: string, callback: AsyncCallback<void>): void
```

为指定系统账号设置头像信息。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-setOsAccountProfilePhoto(localId: int, photo: string, callback: AsyncCallback<void>): void--><!--Device-AccountManager-setOsAccountProfilePhoto(localId: int, photo: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| photo | string | 是 | 头像信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。如果设置成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId or photo. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |

**示例：**

给ID为100的系统账号设置头像。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
let photo: string = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAAPCAYAAAA/I0V3AAAAAXNSR0IArs4c6QAAAARnQU1BAA'+
'Cxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAACwSURBVDhPvZLBDYMwDEV/ugsXRjAT0EHCOuFIBwkbdIRewi6unbiAyoGgSn1SFH85+Y'+
'q/4ljARW62X+LHS8uIzjm4dXUYF+utzBikB52Jo5e5iEPKqpACk7R9NM2RvWm5tIkD2czLCUFNKLD6IjdMHFHDzws285MgGrT0xCtp3WOKHo'+
'+7q0mP0DZW9pNmoEFUzrQjp5cCnaen2kSJXLFD8ghbXyZCMQf/8e8Ns1XVAG/XAgqKzVnJFAAAAABJRU5ErkJggg=='
try {
  accountManager.setOsAccountProfilePhoto(localId, photo, (err: BusinessError)=>{
    if (err) {
      console.error(`setOsAccountProfilePhoto exception:code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setOsAccountProfilePhoto successful.');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountProfilePhoto exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="setosaccountprofilephoto-1"></a>
## setOsAccountProfilePhoto

```TypeScript
setOsAccountProfilePhoto(localId: number, photo: string): Promise<void>
```

为指定系统账号设置头像信息。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-setOsAccountProfilePhoto(localId: int, photo: string): Promise<void>--><!--Device-AccountManager-setOsAccountProfilePhoto(localId: int, photo: string): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| photo | string | 是 | 头像信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId or photo. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted Account. |

**示例：**

给ID为100的系统账号设置头像。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
let photo: string = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAAPCAYAAAA/I0V3AAAAAXNSR0IArs4c6QAAAARnQU1BAA'+
'Cxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAACwSURBVDhPvZLBDYMwDEV/ugsXRjAT0EHCOuFIBwkbdIRewi6unbiAyoGgSn1SFH85+Y'+
'q/4ljARW62X+LHS8uIzjm4dXUYF+utzBikB52Jo5e5iEPKqpACk7R9NM2RvWm5tIkD2czLCUFNKLD6IjdMHFHDzws285MgGrT0xCtp3WOKHo'+
'+7q0mP0DZW9pNmoEFUzrQjp5cCnaen2kSJXLFD8ghbXyZCMQf/8e8Ns1XVAG/XAgqKzVnJFAAAAABJRU5ErkJggg=='
try {
  accountManager.setOsAccountProfilePhoto(localId, photo).then(() => {
    console.info('setOsAccountProfilePhoto success');
  }).catch((err: BusinessError) => {
    console.error(`setOsAccountProfilePhoto err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountProfilePhoto exception: code is ${err.code}, message is ${err.message}`);
}

```

<a id="setosaccounttype"></a>
## setOsAccountType

```TypeScript
setOsAccountType(localId: number, type: OsAccountType, options?: SetOsAccountTypeOptions): Promise<void>
```

设置指定系统账号的账号类型。使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-AccountManager-setOsAccountType(localId: int, type: OsAccountType, options?: SetOsAccountTypeOptions): Promise<void>--><!--Device-AccountManager-setOsAccountType(localId: int, type: OsAccountType, options?: SetOsAccountTypeOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| type | [OsAccountType](arkts-basicservices-osaccount-osaccounttype-e-sys.md) | 是 | 系统账号类型。 |
| options | [SetOsAccountTypeOptions](arkts-basicservices-osaccount-setosaccounttypeoptions-i-sys.md) | 否 | 设置系统账号类型的选项。默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [204](../../errorcode-universal.md#204-用户访问控制策略拒绝此访问) | Access denied due to user access control policy. Possible causes:1. The operation is restricted by the OS-account constraint.2. The required privilege for the operation has not been granted. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type or options. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted OS account. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Service busy. Possible causes: The target account is being operated. |
| [12300023](../../apis-basic-services-kit/errorcode-account.md#12300023-指定类型的账号数量已达到上限) | The number of accounts of the specified type has reached the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let localId: number = 100;
let type: osAccount.OsAccountType = osAccount.OsAccountType.ADMIN;
let options: osAccount.SetOsAccountTypeOptions = {
  token: new Uint8Array([0, 1, 2, 3])
};
try {
  accountManager.setOsAccountType(localId, type, options).then(() => {
    console.info('setOsAccountType successfully');
  }).catch((err: BusinessError) => {
    console.error(`setOsAccountType failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountType exception: code is ${err.code}, message is ${err.message}`);
}

```

