# DistributedAccountAbility

提供查询和更新分布式账号登录状态方法（使用前需要先获取分布式账号的单实例对象）。

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { distributedAccount } from '@kit.BasicServicesKit';
```

## getOsAccountDistributedInfoByLocalId

```TypeScript
getOsAccountDistributedInfoByLocalId(localId: number, callback: AsyncCallback<DistributedInfo>): void
```

获取指定系统账号的分布式账号信息。使用callback异步回调。

**起始版本：** 10

**需要权限：** 
- API版本20+：ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or (ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.GET_DISTRIBUTED_ACCOUNTS)
- API版本10 - 19：ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;DistributedInfo&gt; | 是 | 回调函数。当获取分布式账号信息成功时，err为undefined，data为获取到的分布式账号信息对象；否则err为错误 对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
try {
  let localId: number = 100; // 示例值，实际使用时请获取真实的系统账号ID
  accountAbility.getOsAccountDistributedInfoByLocalId(localId,
    (err: BusinessError, data: distributedAccount.DistributedInfo) => {
      if (err) {
        console.error(`getOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('distributed information: ' + JSON.stringify(data));
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountDistributedInfoByLocalId

```TypeScript
getOsAccountDistributedInfoByLocalId(localId: number): Promise<DistributedInfo>
```

获取指定系统账号的分布式账号信息。使用Promise异步回调。

**起始版本：** 10

**需要权限：** 
- API版本20+：ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or (ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.GET_DISTRIBUTED_ACCOUNTS)
- API版本10 - 19：ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;DistributedInfo & gt; | Promise对象，返回分布式账号信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
try {
  let localId: number = 100; // 示例值，实际使用时请获取真实的系统账号ID
  accountAbility.getOsAccountDistributedInfoByLocalId(localId).then((
    data: distributedAccount.DistributedInfo) => {
    console.info('distributed information: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## setOsAccountDistributedInfoByLocalId

```TypeScript
setOsAccountDistributedInfoByLocalId(localId: number, distributedInfo: DistributedInfo, callback: AsyncCallback<void>): void
```

设置指定系统账号的分布式账号信息。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| distributedInfo | DistributedInfo | 是 | 分布式账号信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置指定系统账号的分布式账号信息成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.   2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid distributedInfo. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account identified by localId or by distributedInfo not found. |
| [12300008](../errorcode-account.md#12300008-受限的账号) | Restricted OS account. |
| [12300406](../errorcode-account.md#12300406-该分布式账号信息已经与目标系统账号的其他子身份资料绑定) | The distributed account information has already been bound to a sub-profile of the target OS account.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
try {
  let localId: number = 100; // 示例值，实际使用时请获取真实的系统账号ID
  accountAbility.setOsAccountDistributedInfoByLocalId(localId, accountInfo, (err: BusinessError) => {
    if (err) {
      console.error(`setOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setOsAccountDistributedInfoByLocalId successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## setOsAccountDistributedInfoByLocalId

```TypeScript
setOsAccountDistributedInfoByLocalId(localId: number, distributedInfo: DistributedInfo): Promise<void>
```

设置指定系统账号的分布式账号信息。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| distributedInfo | DistributedInfo | 是 | 分布式账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.   2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid distributedInfo. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account identified by localId or by distributedInfo not found. |
| [12300008](../errorcode-account.md#12300008-受限的账号) | Restricted OS account. |
| [12300406](../errorcode-account.md#12300406-该分布式账号信息已经与目标系统账号的其他子身份资料绑定) | The distributed account information has already been bound to a sub-profile of the target OS account.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
try {
  let localId: number = 100; // 示例值，实际使用时请获取真实的系统账号ID
  accountAbility.setOsAccountDistributedInfoByLocalId(localId, accountInfo).then(() => {
    console.info('setOsAccountDistributedInfoByLocalId successfully');
  }).catch((err: BusinessError) => {
    console.error(`setOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```
