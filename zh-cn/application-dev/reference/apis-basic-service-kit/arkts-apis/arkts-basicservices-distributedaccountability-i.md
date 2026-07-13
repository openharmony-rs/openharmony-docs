# DistributedAccountAbility

提供查询和更新分布式账号登录状态方法（需要先获取分布式账号的单实例对象）。

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## getOsAccountDistributedInfo

```TypeScript
getOsAccountDistributedInfo(callback: AsyncCallback<DistributedInfo>): void
```

获取分布式账号信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or ohos.permission.GET_DISTRIBUTED_ACCOUNTS or ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;DistributedInfo&gt; | 是 | 回调参数。当获取分布式账号信息成功，err为undefined，data为获取到的分布式账号信息对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取分布式账号的单实例对象
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
try {
  accountAbility.getOsAccountDistributedInfo(
    (err: BusinessError, data: distributedAccount.DistributedInfo) => {
      if (err) {
        console.error(`getOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('distributed information: ' + JSON.stringify(data));
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
}

```

## getOsAccountDistributedInfo

```TypeScript
getOsAccountDistributedInfo(): Promise<DistributedInfo>
```

获取分布式账号信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or ohos.permission.GET_DISTRIBUTED_ACCOUNTS or ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DistributedInfo&gt; | Promise对象，返回分布式账号信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取分布式账号的单实例对象
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
try {
  accountAbility.getOsAccountDistributedInfo().then((data: distributedAccount.DistributedInfo) => {
    console.info('distributed information: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
}

```

## queryOsAccountDistributedInfo

```TypeScript
queryOsAccountDistributedInfo(callback: AsyncCallback<DistributedInfo>): void
```

获取分布式账号信息。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getOsAccountDistributedInfo](arkts-basicservices-distributedaccountability-i.md#getosaccountdistributedinfo-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getOsAccountDistributedInfo(callback:

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;DistributedInfo&gt; | 是 | 回调函数。当获取分布式账号信息成功，err为undefined，data为获取到的分布式账号信息对象；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取分布式账号的单实例对象
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
accountAbility.queryOsAccountDistributedInfo(
  (err: BusinessError, data: distributedAccount.DistributedInfo) => {
    if (err) {
      console.error(`queryOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('distributed information: ' + JSON.stringify(data));
    }
  });

```

## queryOsAccountDistributedInfo

```TypeScript
queryOsAccountDistributedInfo(): Promise<DistributedInfo>
```

获取分布式账号信息。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getOsAccountDistributedInfo](arkts-basicservices-distributedaccountability-i.md#getosaccountdistributedinfo-2)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getOsAccountDistributedInfo()](arkts-basicservices-distributedaccountability-i.md#getosaccountdistributedinfo-2)

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DistributedInfo&gt; | Promise对象，返回分布式账号信息对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取分布式账号的单实例对象
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
accountAbility.queryOsAccountDistributedInfo().then((data: distributedAccount.DistributedInfo) => {
  console.info('distributed information: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`queryOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
});

```

## setOsAccountDistributedInfo

```TypeScript
setOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback<void>): void
```

更新分布式账号信息。使用callback异步回调。
该接口仅限系统应用调用。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountInfo | DistributedInfo | 是 | 分布式账号信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当更新分布式账号信息成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid accountInfo. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取分布式账号的单实例对象
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
// 示例值，实际使用时请通过getOsAccountDistributedInfo获取真实分布式账号信息
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
try {
  accountAbility.setOsAccountDistributedInfo(accountInfo, (err: BusinessError) => {
    if (err) {
      console.error(`setOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setOsAccountDistributedInfo successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
}

```

## setOsAccountDistributedInfo

```TypeScript
setOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise<void>
```

更新分布式账号信息。使用Promise异步回调。
该接口仅限系统应用调用。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountInfo | DistributedInfo | 是 | 分布式账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid accountInfo. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取分布式账号的单实例对象
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
// 示例值，实际使用时请通过getOsAccountDistributedInfo获取真实分布式账号信息
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
try {
  accountAbility.setOsAccountDistributedInfo(accountInfo).then(() => {
    console.info('setOsAccountDistributedInfo successfully');
  }).catch((err: BusinessError) => {
    console.error(`setOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
}

```

## updateOsAccountDistributedInfo

```TypeScript
updateOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback<void>): void
```

更新分布式账号信息。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setOsAccountDistributedInfo](arkts-basicservices-distributedaccountability-i.md#setosaccountdistributedinfo-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setOsAccountDistributedInfo(accountInfo:

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountInfo | DistributedInfo | 是 | 分布式账号信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当更新分布式账号信息成功时，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取分布式账号的单实例对象
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
// 示例值，实际使用时请通过getOsAccountDistributedInfo获取真实分布式账号信息
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
accountAbility.updateOsAccountDistributedInfo(accountInfo, (err: BusinessError) => {
  if (err) {
    console.error(`updateOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('updateOsAccountDistributedInfo successfully');
  }
});

```

## updateOsAccountDistributedInfo

```TypeScript
updateOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise<void>
```

更新分布式账号信息。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setOsAccountDistributedInfo](arkts-basicservices-distributedaccountability-i.md#setosaccountdistributedinfo-2)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setOsAccountDistributedInfo(accountInfo:

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountInfo | DistributedInfo | 是 | 分布式账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 获取分布式账号的单实例对象
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
// 示例值，实际使用时请通过getOsAccountDistributedInfo获取真实分布式账号信息
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
accountAbility.updateOsAccountDistributedInfo(accountInfo).then(() => {
  console.info('updateOsAccountDistributedInfo successfully');
}).catch((err: BusinessError) => {
  console.error(`updateOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
});

```

