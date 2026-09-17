# AccountManager

系统账号管理类。

**起始版本：** 7

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## checkMultiOsAccountEnabled

```TypeScript
checkMultiOsAccountEnabled(callback: AsyncCallback<boolean>): void
```

判断是否支持多系统账号。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示支持多系统账号；返回false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.checkMultiOsAccountEnabled((err: BusinessError, isEnabled: boolean) => {
    if (err) {
      console.error(`checkMultiOsAccountEnabled failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkMultiOsAccountEnabled successfully, isEnabled: ' + isEnabled);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkMultiOsAccountEnabled failed, code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  accountManager.checkMultiOsAccountEnabled().then((isEnabled: boolean) => {
    console.info('checkMultiOsAccountEnabled successfully, isEnabled: ' + isEnabled);
  }).catch((err: BusinessError) => {
    console.error(`checkMultiOsAccountEnabled failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkMultiOsAccountEnabled failed, code is ${err.code}, message is ${err.message}`);
}
```

## checkMultiOsAccountEnabled

```TypeScript
checkMultiOsAccountEnabled(): Promise<boolean>
```

判断是否支持多系统账号。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示支持多系统账号；返回false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

参见 [checkMultiOsAccountEnabled](#checkmultiosaccountenabled)

## checkOsAccountActivated

```TypeScript
checkOsAccountActivated(localId: number, callback: AsyncCallback<boolean>): void
```

判断指定系统账号是否处于激活状态。使用callback异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。替代方法仅向系统应用开放。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示账号已激活；返回false表示账号未激活。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

```TypeScript
判断ID为100的系统账号是否处于激活状态。
```

## checkOsAccountActivated

```TypeScript
checkOsAccountActivated(localId: number): Promise<boolean>
```

判断指定系统账号是否处于激活状态。使用Promise异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。替代方法仅向系统应用开放。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

参见 [checkOsAccountActivated](#checkosaccountactivated)

## checkOsAccountConstraintEnabled

```TypeScript
checkOsAccountConstraintEnabled(localId: number, constraint: string, callback: AsyncCallback<boolean>): void
```

判断指定系统账号是否具有指定约束。使用callback异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。替代方法仅向系统应用开放。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| constraint | string | 是 | 指定的[约束](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md)名称。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示已使能指定的约束；返回false表示未使能指定的约束。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid localId or constraint. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

```TypeScript
判断ID为100的系统账号是否有禁止使用Wi-Fi的约束。
```

## checkOsAccountConstraintEnabled

```TypeScript
checkOsAccountConstraintEnabled(localId: number, constraint: string): Promise<boolean>
```

判断指定系统账号是否具有指定约束。使用Promise异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。替代方法仅向系统应用开放。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| constraint | string | 是 | 指定的[约束](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md)名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示已使能指定的约束；返回false表示未使能指定的约束。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid localId or constraint. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

参见 [checkOsAccountConstraintEnabled](#checkosaccountconstraintenabled)

## checkOsAccountTestable

```TypeScript
checkOsAccountTestable(callback: AsyncCallback<boolean>): void
```

检查当前系统账号是否为测试账号。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示当前账号为测试账号；返回false表示当前账号非测试账号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.checkOsAccountTestable((err: BusinessError, isTestable: boolean) => {
    if (err) {
      console.error(`checkOsAccountTestable failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkOsAccountTestable successfully, isTestable: ' + isTestable);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountTestable code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.checkOsAccountTestable().then((isTestable: boolean) => {
    console.info('checkOsAccountTestable successfully, isTestable: ' + isTestable);
  }).catch((err: BusinessError) => {
    console.error(`checkOsAccountTestable failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountTestable exception: code is ${err.code}, message is ${err.message}`);
}
```

## checkOsAccountTestable

```TypeScript
checkOsAccountTestable(): Promise<boolean>
```

检查当前系统账号是否为测试账号。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前账号为测试账号；返回false表示当前账号非测试账号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

参见 [checkOsAccountTestable](#checkosaccounttestable)

## checkOsAccountVerified

```TypeScript
checkOsAccountVerified(callback: AsyncCallback<boolean>): void
```

检查当前系统账号是否已认证解锁。使用callback异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。建议使用
> [isOsAccountUnlocked](#isosaccountunlocked)替代。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [isOsAccountUnlocked](#isosaccountunlocked)()

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示当前账号已认证解锁；返回false表示当前账号未认证解锁。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.checkOsAccountVerified((err: BusinessError, isVerified: boolean) => {
    if (err) {
      console.error(`checkOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkOsAccountVerified successfully, isVerified: ' + isVerified);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountVerified exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.checkOsAccountVerified().then((isVerified: boolean) => {
    console.info('checkOsAccountVerified successfully, isVerified: ' + isVerified);
  }).catch((err: BusinessError) => {
    console.error(`checkOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountVerified exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId为系统账号ID，请通过getOsAccountLocalId接口获取
let localId: number = 100;
try {
  accountManager.checkOsAccountVerified(localId, (err: BusinessError, isVerified: boolean) => {
    if (err) {
      console.error(`checkOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkOsAccountVerified successfully, isVerified: ' + isVerified);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountVerified exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId为系统账号ID，请通过getOsAccountLocalId接口获取
let localId: number = 100;
try {
  accountManager.checkOsAccountVerified(localId).then((isVerified: boolean) => {
    console.info('checkOsAccountVerified successfully, isVerified: ' + isVerified);
  }).catch((err: BusinessError) => {
    console.error(`checkOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountVerified exception: code is ${err.code}, message is ${err.message}`);
}
```

## checkOsAccountVerified

```TypeScript
checkOsAccountVerified(): Promise<boolean>
```

检查当前系统账号是否已认证解锁。使用Promise异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。建议使用
> [isOsAccountUnlocked](#isosaccountunlocked)替代。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [isOsAccountUnlocked](#isosaccountunlocked)()

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前账号已认证解锁；返回false表示当前账号未认证解锁。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

参见 [checkOsAccountVerified](#checkosaccountverified)

## checkOsAccountVerified

```TypeScript
checkOsAccountVerified(localId: number, callback: AsyncCallback<boolean>): void
```

检查指定系统账号是否已验证。使用callback异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。替代方法仅向系统应用开放。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示指定账号已认证解锁；返回false表示指定账号未认证解锁。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

参见 [checkOsAccountVerified](#checkosaccountverified)

## checkOsAccountVerified

```TypeScript
checkOsAccountVerified(localId: number): Promise<boolean>
```

检查指定系统账号是否已验证。使用Promise异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。替代方法仅向系统应用开放。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

参见 [checkOsAccountVerified](#checkosaccountverified)

## getActivatedOsAccountLocalIds

```TypeScript
getActivatedOsAccountLocalIds(callback: AsyncCallback<Array<number>>): void
```

查询当前处于激活状态的系统账号的ID列表。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | 回调函数。如果查询成功，err为null，data为当前处于激活状态的系统账号的ID列表；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getActivatedOsAccountLocalIds((err: BusinessError, idArray: number[])=>{
    if (err) {
      console.error(`getActivatedOsAccountLocalIds code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getActivatedOsAccountLocalIds idArray length:' + idArray.length);
      for(let i=0;i<idArray.length;i++) {
        console.info('activated os account id: ' + idArray[i]);
      }
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getActivatedOsAccountLocalIds exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getActivatedOsAccountLocalIds().then((idArray: number[]) => {
    console.info('getActivatedOsAccountLocalIds, idArray: ' + idArray);
  }).catch((err: BusinessError) => {
    console.error(`getActivatedOsAccountLocalIds err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getActivatedOsAccountLocalIds exception: code is ${err.code}, message is ${err.message}`);
}
```

## getActivatedOsAccountLocalIds

```TypeScript
getActivatedOsAccountLocalIds(): Promise<Array<number>>
```

查询当前处于激活状态的系统账号的ID列表。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise对象，返回当前处于激活状态的系统账号的ID列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

参见 [getActivatedOsAccountLocalIds](#getactivatedosaccountlocalids)

## getCreatedOsAccountsCount

```TypeScript
getCreatedOsAccountsCount(callback: AsyncCallback<number>): void
```

获取已创建的系统账号数量。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getOsAccountCount](#getosaccountcount)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getOsAccountCount](#getosaccountcount)(callback: AsyncCallback&lt;number&gt;)

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果获取成功，err为null，data为已创建的系统账号的数量；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getCreatedOsAccountsCount((err: BusinessError, count: number)=>{
  if (err) {
    console.error(`getCreatedOsAccountsCount failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getCreatedOsAccountsCount successfully, count: ' + count);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getCreatedOsAccountsCount().then((count: number) => {
  console.info('getCreatedOsAccountsCount successfully, count: ' + count);
}).catch((err: BusinessError) => {
  console.error(`getCreatedOsAccountsCount failed, code is ${err.code}, message is ${err.message}`);
});
```

## getCreatedOsAccountsCount

```TypeScript
getCreatedOsAccountsCount(): Promise<number>
```

获取已创建的系统账号数量。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getOsAccountCount](#getosaccountcount)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getOsAccountCount](#getosaccountcount)()

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回已创建的系统账号的数量。 |

**示例**

参见 [getCreatedOsAccountsCount](#getcreatedosaccountscount)

## getCurrentOsAccount

```TypeScript
getCurrentOsAccount(callback: AsyncCallback<OsAccountInfo>): void
```

查询当前进程所属的系统账号的信息。使用callback异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。替代方法仅向系统应用开放。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** 
- API版本10+：ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.GET_LOCAL_ACCOUNTS
- API版本9：ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i.md)&gt; | 是 | 回调函数。如果查询成功，err为null，data为当前进程所属的系统账号信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getCurrentOsAccount((err: BusinessError, curAccountInfo: osAccount.OsAccountInfo)=>{
    if (err) {
      console.error(`getCurrentOsAccount code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getCurrentOsAccount curAccountInfo:' + JSON.stringify(curAccountInfo));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCurrentOsAccount exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getCurrentOsAccount().then((accountInfo: osAccount.OsAccountInfo) => {
    console.info('getCurrentOsAccount, accountInfo: ' + JSON.stringify(accountInfo));
  }).catch((err: BusinessError) => {
    console.error(`getCurrentOsAccount err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCurrentOsAccount exception: code is ${err.code}, message is ${err.message}`);
}
```

## getCurrentOsAccount

```TypeScript
getCurrentOsAccount(): Promise<OsAccountInfo>
```

查询当前进程所属的系统账号的信息。使用Promise异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。替代方法仅向系统应用开放。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** 
- API版本10+：ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.GET_LOCAL_ACCOUNTS
- API版本9：ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i.md)&gt; | Promise对象，返回当前进程所属的系统账号信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

参见 [getCurrentOsAccount](#getcurrentosaccount)

## getDistributedVirtualDeviceId

```TypeScript
getDistributedVirtualDeviceId(callback: AsyncCallback<string>): void
```

获取分布式虚拟设备ID。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [queryDistributedVirtualDeviceId](#querydistributedvirtualdeviceid)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [queryDistributedVirtualDeviceId](#querydistributedvirtualdeviceid)(callback: AsyncCallback&lt;string&gt;)

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC or ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。如果获取成功，err为null，data为分布式虚拟设备ID；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getDistributedVirtualDeviceId((err: BusinessError, virtualID: string) => {
  if (err) {
    console.error(`getDistributedVirtualDeviceId err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getDistributedVirtualDeviceId virtualID: ' + virtualID);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getDistributedVirtualDeviceId().then((virtualID: string) => {
  console.info('getDistributedVirtualDeviceId, virtualID: ' + virtualID);
}).catch((err: BusinessError) => {
  console.error(`getDistributedVirtualDeviceId err: code is ${err.code}, message is ${err.message}`);
});
```

## getDistributedVirtualDeviceId

```TypeScript
getDistributedVirtualDeviceId(): Promise<string>
```

获取分布式虚拟设备ID。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [queryDistributedVirtualDeviceId](#querydistributedvirtualdeviceid)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [queryDistributedVirtualDeviceId](#querydistributedvirtualdeviceid)()

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC or ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回分布式虚拟设备ID。 |

**示例**

参见 [getDistributedVirtualDeviceId](#getdistributedvirtualdeviceid)

## getForegroundOsAccountLocalId

```TypeScript
getForegroundOsAccountLocalId(): Promise<number>
```

获取前台系统账号的ID。使用Promise异步回调。

**起始版本：** 15

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回前台系统账号的ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getForegroundOsAccountLocalId().then((localId: number) => {
    console.info('getForegroundOsAccountLocalId, localId: ' + localId);
  }).catch((err: BusinessError) => {
    console.error(`getForegroundOsAccountLocalId err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getForegroundOsAccountLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

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

## getOsAccountAllConstraints

```TypeScript
getOsAccountAllConstraints(localId: number, callback: AsyncCallback<Array<string>>): void
```

获取指定系统账号的全部约束。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。替代方法仅向系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。如果获取成功，err为null，data为指定系统账号的全部[约束](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md)；否则为错误对象。 |

**示例**

```TypeScript
获取ID为100的系统账号的全部约束。
```

## getOsAccountAllConstraints

```TypeScript
getOsAccountAllConstraints(localId: number): Promise<Array<string>>
```

获取指定系统账号的全部约束。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。替代方法仅向系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回指定系统账号的全部[约束](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md)。 |

**示例**

参见 [getOsAccountAllConstraints](#getosaccountallconstraints)

## getOsAccountConstraints

```TypeScript
getOsAccountConstraints(localId: number, callback: AsyncCallback<Array<string>>): void
```

获取指定系统账号的全部约束。使用callback异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。替代方法仅向系统应用开放。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，如果获取成功，err为null，data为该系统账号的全部[约束](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md)；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

```TypeScript
获取ID为100的系统账号的全部约束。
```

## getOsAccountConstraints

```TypeScript
getOsAccountConstraints(localId: number): Promise<Array<string>>
```

获取指定系统账号的全部约束。使用Promise异步回调。

> **说明：** 
> 
> 从API version 9开始支持，从API version 11开始废弃。替代方法仅向系统应用开放。

**起始版本：** 9

**废弃版本：** 11

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回指定系统账号的全部[约束](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

参见 [getOsAccountConstraints](#getosaccountconstraints)

## getOsAccountCount

```TypeScript
getOsAccountCount(callback: AsyncCallback<number>): void
```

获取已创建的系统账号数量。使用callback异步回调。该接口仅限系统应用调用。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果获取成功，err为null，data为已创建的系统账号的数量；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountCount((err: BusinessError, count: number) => {
    if (err) {
      console.error(`getOsAccountCount failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountCount successfully, count: ' + count);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountCount exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountCount().then((count: number) => {
    console.info('getOsAccountCount successfully, count: ' + count);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountCount failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountCount exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountCount

```TypeScript
getOsAccountCount(): Promise<number>
```

获取已创建的系统账号数量。使用Promise异步回调。该接口仅限系统应用调用。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回已创建的系统账号的数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

参见 [getOsAccountCount](#getosaccountcount)

## getOsAccountDomainInfo

```TypeScript
getOsAccountDomainInfo(localId: number): Promise<DomainAccountInfo>
```

获取指定系统账号关联的域账号信息。使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.GET_DOMAIN_ACCOUNTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md)&gt; | Promise对象，返回与指定系统账号关联的域账号信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | OS account not found. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId为系统账号ID，请通过getOsAccountLocalId接口获取
let localId: number = 100;
accountManager.getOsAccountDomainInfo(localId).then((domainAccountInfo: osAccount.DomainAccountInfo) => {
  if (domainAccountInfo === null) {
    console.info('The target OS account is not a domain account.')
  } else {
    console.info('getOsAccountDomainInfo domain: ' + domainAccountInfo.domain);
    console.info('getOsAccountDomainInfo accountName: ' + domainAccountInfo.accountName);
  }
}).catch((err: BusinessError) => {
  console.error(`getOsAccountDomainInfo err: code is ${err.code}, message is ${err.message}`);
})
```

## getOsAccountLocalId

```TypeScript
getOsAccountLocalId(callback: AsyncCallback<number>): void
```

获取当前进程所属的系统账号ID。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果获取成功，err为null，data为当前进程所属的系统账号ID；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountLocalId((err: BusinessError, localId: number) => {
    if (err) {
      console.error(`getOsAccountLocalId failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountLocalId successfully, localId: ' + localId);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountLocalId().then((localId: number) => {
    console.info('getOsAccountLocalId successfully, localId: ' + localId);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountLocalId failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountLocalId

```TypeScript
getOsAccountLocalId(): Promise<number>
```

获取当前进程所属的系统账号ID。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回当前进程所属的系统账号ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

参见 [getOsAccountLocalId](#getosaccountlocalid)

## getOsAccountLocalIdBySerialNumber

```TypeScript
getOsAccountLocalIdBySerialNumber(serialNumber: number, callback: AsyncCallback<number>): void
```

通过SN码查询与其关联的系统账号的账号ID。使用callback异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getOsAccountLocalIdForSerialNumber](#getosaccountlocalidforserialnumber)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getOsAccountLocalIdForSerialNumber](#getosaccountlocalidforserialnumber)(serialNumber: number, callback: AsyncCallback&lt;number&gt;)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serialNumber | number | 是 | 账号SN码。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果查询成功，err为null，data为与SN码关联的系统账号的账号ID；否则为错误对象。 |

**示例**

```TypeScript
查询与SN码12345关联的系统账号的ID。
```

## getOsAccountLocalIdBySerialNumber

```TypeScript
getOsAccountLocalIdBySerialNumber(serialNumber: number): Promise<number>
```

通过SN码查询与其关联的系统账号的账号ID。使用Promise异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getOsAccountLocalIdForSerialNumber](#getosaccountlocalidforserialnumber)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getOsAccountLocalIdForSerialNumber](#getosaccountlocalidforserialnumber)(serialNumber: number)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serialNumber | number | 是 | 账号SN码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回与SN码关联的系统账号的账号ID。 |

**示例**

参见 [getOsAccountLocalIdBySerialNumber](#getosaccountlocalidbyserialnumber)

## getOsAccountLocalIdForDomain

```TypeScript
getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback<number>): void
```

根据域账号信息，获取与其关联的系统账号ID。使用callback异步回调。该接口仅限系统应用调用。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | 是 | 域账号信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果查询成功，err为null，data为域账号关联的系统账号ID；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid domainInfo. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Domain account not found. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainInfo: osAccount.DomainAccountInfo = {domain: 'testDomain', accountName: 'testAccountName'};
let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountLocalIdForDomain(domainInfo, (err: BusinessError, localId: number) => {
    if (err) {
      console.error(`getOsAccountLocalIdForDomain failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountLocalIdForDomain successfully, localId: ' + localId);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalIdForDomain exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let domainInfo: osAccount.DomainAccountInfo = {domain: 'testDomain', accountName: 'testAccountName'};
try {
  accountManager.getOsAccountLocalIdForDomain(domainInfo).then((localId: number) => {
    console.info('getOsAccountLocalIdForDomain successfully, localId: ' + localId);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountLocalIdForDomain failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalIdForDomain exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountLocalIdForDomain

```TypeScript
getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo): Promise<number>
```

根据域账号信息，获取与其关联的系统账号的账号ID。使用Promise异步回调。该接口仅限系统应用调用。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | 是 | 域账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回域账号关联的系统账号ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid domainInfo. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Domain account not found. |

**示例**

参见 [getOsAccountLocalIdForDomain](#getosaccountlocalidfordomain)

## getOsAccountLocalIdForSerialNumber

```TypeScript
getOsAccountLocalIdForSerialNumber(serialNumber: number, callback: AsyncCallback<number>): void
```

通过SN码查询与其关联的系统账号的账号ID。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serialNumber | number | 是 | 账号SN码。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果成功，err为null，data为与SN码关联的系统账号的账号ID；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid serialNumber. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | The account indicated by serialNumber does not exist. |

**示例**

```TypeScript
查询与SN码12345关联的系统账号的ID。
```

## getOsAccountLocalIdForSerialNumber

```TypeScript
getOsAccountLocalIdForSerialNumber(serialNumber: number): Promise<number>
```

通过SN码查询与其关联的系统账号的账号ID。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serialNumber | number | 是 | 账号SN码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回与SN码关联的系统账号的账号ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid serialNumber. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | The account indicated by serialNumber does not exist. |

**示例**

参见 [getOsAccountLocalIdForSerialNumber](#getosaccountlocalidforserialnumber)

## getOsAccountLocalIdForUid

```TypeScript
getOsAccountLocalIdForUid(uid: number, callback: AsyncCallback<number>): void
```

根据uid查询对应的系统账号ID。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 进程uid。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果查询成功，err为null，data为对应的系统账号ID；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid uid. |

**示例**

```TypeScript
查询值为12345678的uid所属的系统账号的账号ID。
```

```TypeScript
查询值为12345678的uid所属的系统账号ID。
```

## getOsAccountLocalIdForUid

```TypeScript
getOsAccountLocalIdForUid(uid: number): Promise<number>
```

根据uid查询对应的系统账号ID。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 进程uid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回指定uid对应的系统账号ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid uid. |

**示例**

参见 [getOsAccountLocalIdForUid](#getosaccountlocalidforuid)

## getOsAccountLocalIdForUidSync

```TypeScript
getOsAccountLocalIdForUidSync(uid: number): number
```

根据uid查询对应的系统账号ID。使用同步方式返回结果。

**起始版本：** 10

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 进程uid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定uid对应的系统账号ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid uid. |

**示例**

```TypeScript
查询值为12345678的uid所属的系统账号ID。
```

## getOsAccountLocalIdFromDomain

```TypeScript
getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback<number>): void
```

根据域账号信息，获取与其关联的系统账号的账号ID。使用callback异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getOsAccountLocalIdForDomain](#getosaccountlocalidfordomain)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getOsAccountLocalIdForDomain](#getosaccountlocalidfordomain)(domainInfo: DomainAccountInfo, callback: AsyncCallback&lt;number&gt;)

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | 是 | 域账号信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，如果获取成功，err为null，data为域账号关联的系统账号ID；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainInfo: osAccount.DomainAccountInfo = {domain: 'testDomain', accountName: 'testAccountName'};
let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getOsAccountLocalIdFromDomain(domainInfo, (err: BusinessError, localId: number) => {
  if (err) {
    console.error(`getOsAccountLocalIdFromDomain failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getOsAccountLocalIdFromDomain successfully, localId: ' + localId);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let domainInfo: osAccount.DomainAccountInfo = {domain: 'testDomain', accountName: 'testAccountName'};
accountManager.getOsAccountLocalIdFromDomain(domainInfo).then((localId: number) => {
  console.info('getOsAccountLocalIdFromDomain successfully, localId: ' + localId);
}).catch((err: BusinessError) => {
  console.error(`getOsAccountLocalIdFromDomain failed, code is ${err.code}, message is ${err.message}`);
});
```

## getOsAccountLocalIdFromDomain

```TypeScript
getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo): Promise<number>
```

根据域账号信息，获取与其关联的系统账号的账号ID。使用Promise异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getOsAccountLocalIdForDomain](#getosaccountlocalidfordomain-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getOsAccountLocalIdForDomain](#getosaccountlocalidfordomain-1)(domainInfo: DomainAccountInfo)

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | 是 | 域账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回域账号关联的系统账号ID。 |

**示例**

参见 [getOsAccountLocalIdFromDomain](#getosaccountlocalidfromdomain)

## getOsAccountLocalIdFromProcess

```TypeScript
getOsAccountLocalIdFromProcess(callback: AsyncCallback<number>): void
```

获取当前进程所属的系统账号ID。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getOsAccountLocalId](#getosaccountlocalid)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getOsAccountLocalId](#getosaccountlocalid)(callback: AsyncCallback&lt;number&gt;)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果获取成功，err为null，data为当前进程所属的系统账号ID；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getOsAccountLocalIdFromProcess((err: BusinessError, localId: number) => {
  if (err) {
    console.error(`getOsAccountLocalIdFromProcess failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getOsAccountLocalIdFromProcess id:: ' + localId);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getOsAccountLocalIdFromProcess().then((localId: number) => {
  console.info('getOsAccountLocalIdFromProcess successfully, localId: ' + localId);
}).catch((err: BusinessError) => {
  console.error(`getOsAccountLocalIdFromProcess failed, code is ${err.code}, message is ${err.message}`);
});
```

## getOsAccountLocalIdFromProcess

```TypeScript
getOsAccountLocalIdFromProcess(): Promise<number>
```

获取当前进程所属的系统账号ID。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getOsAccountLocalId](#getosaccountlocalid)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getOsAccountLocalId](#getosaccountlocalid)()

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回当前进程所属的系统账号ID。 |

**示例**

参见 [getOsAccountLocalIdFromProcess](#getosaccountlocalidfromprocess)

## getOsAccountLocalIdFromUid

```TypeScript
getOsAccountLocalIdFromUid(uid: number, callback: AsyncCallback<number>): void
```

根据uid查询对应的系统账号ID。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getOsAccountLocalIdForUid](#getosaccountlocalidforuid)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getOsAccountLocalIdForUid](#getosaccountlocalidforuid)(uid: number, callback: AsyncCallback&lt;number&gt;)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 进程uid。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果查询成功，err为null，data为对应的系统账号ID；否则为错误对象。 |

**示例**

```TypeScript
查询值为12345678的uid所属的系统账号ID。
```

## getOsAccountLocalIdFromUid

```TypeScript
getOsAccountLocalIdFromUid(uid: number): Promise<number>
```

根据uid查询对应的系统账号ID。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getOsAccountLocalIdForUid](#getosaccountlocalidforuid)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getOsAccountLocalIdForUid](#getosaccountlocalidforuid)(uid: number)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 进程uid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回uid对应的系统账号ID。 |

**示例**

参见 [getOsAccountLocalIdFromUid](#getosaccountlocalidfromuid)

## getOsAccountLocalIds

```TypeScript
getOsAccountLocalIds(): Promise<number[]>
```

获取所有非系统级的操作系统账号的本地ID。非系统级的操作系统账号对用户可见，通常用于登录等操作。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_LOCAL_ACCOUNT_IDENTIFIERS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number[]&gt; | Promise对象，返回所有非系统级的操作系统账号的本地ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountLocalIds().then((localIds: number[]) => {
    console.info('getOsAccountLocalIds localIds: ' + localIds);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountLocalIds failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalIds exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountName

```TypeScript
getOsAccountName(): Promise<string>
```

查询调用方所属系统账号的名称。使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回调用方所属系统账号的名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountName().then((name: string) => {
    console.info('getOsAccountName, name: ' + name);
  }).catch((err: BusinessError) => {
    console.error('getOsAccountName err: ' + err);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountName exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountNameByLocalId

```TypeScript
getOsAccountNameByLocalId(localId: number): Promise<string>
```

根据系统账号的本地ID获取系统账号的名称。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_LOCAL_ACCOUNT_IDENTIFIERS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 目标系统账号的本地ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回目标系统账号的名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300008](../errorcode-account.md#12300008-受限的账号) | Restricted Account. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountNameByLocalId(100).then((name: string) => {
    console.info('getOsAccountNameByLocalId, name: ' + name);
  }).catch((err: BusinessError) => {
    console.error('getOsAccountNameByLocalId err: ' + err);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountNameByLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountType

```TypeScript
getOsAccountType(callback: AsyncCallback<OsAccountType>): void
```

查询当前进程所属的系统账号的账号类型。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md)&gt; | 是 | 回调函数。如果查询成功，err为null，data为当前进程所属的系统账号的账号类型；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountType((err: BusinessError, accountType: osAccount.OsAccountType) => {
    if (err) {
      console.error(`getOsAccountType err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountType accountType: ' + accountType);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountType exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountType().then((accountType: osAccount.OsAccountType) => {
    console.info('getOsAccountType, accountType: ' + accountType);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountType err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountType exception: code is ${err.code}, message is ${err.message}`);
}
```

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

## getOsAccountType

```TypeScript
getOsAccountType(): Promise<OsAccountType>
```

查询当前进程所属的系统账号的账号类型。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md)&gt; | Promise对象，返回当前进程所属的系统账号的账号类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

参见 [getOsAccountType](#getosaccounttype)

## getOsAccountTypeFromProcess

```TypeScript
getOsAccountTypeFromProcess(callback: AsyncCallback<OsAccountType>): void
```

查询当前进程所属的系统账号的账号类型。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getOsAccountType](#getosaccounttype)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getOsAccountType](#getosaccounttype)(callback: AsyncCallback&lt;OsAccountType&gt;)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md)&gt; | 是 | 回调函数。如果查询成功，err为null，data为当前进程所属的系统账号的账号类型；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getOsAccountTypeFromProcess((err: BusinessError, accountType: osAccount.OsAccountType) => {
  if (err) {
    console.error(`getOsAccountTypeFromProcess err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getOsAccountTypeFromProcess accountType: ' + accountType);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getOsAccountTypeFromProcess().then((accountType: osAccount.OsAccountType) => {
  console.info('getOsAccountTypeFromProcess, accountType: ' + accountType);
}).catch((err: BusinessError) => {
  console.error(`getOsAccountTypeFromProcess err: code is ${err.code}, message is ${err.message}`);
});
```

## getOsAccountTypeFromProcess

```TypeScript
getOsAccountTypeFromProcess(): Promise<OsAccountType>
```

查询当前进程所属的系统账号的账号类型。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用[getOsAccountType](#getosaccounttype)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getOsAccountType](#getosaccounttype)()

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md)&gt; | Promise对象，返回当前进程所属的系统账号的账号类型。 |

**示例**

参见 [getOsAccountTypeFromProcess](#getosaccounttypefromprocess)

## getSerialNumberByOsAccountLocalId

```TypeScript
getSerialNumberByOsAccountLocalId(localId: number, callback: AsyncCallback<number>): void
```

通过系统账号ID获取与该系统账号关联的SN码。使用callback异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getSerialNumberForOsAccountLocalId](#getserialnumberforosaccountlocalid)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getSerialNumberForOsAccountLocalId](#getserialnumberforosaccountlocalid)(localId: number, callback: AsyncCallback&lt;number&gt;)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果获取成功，err为null，data为与该系统账号关联的SN码；否则为错误对象。 |

**示例**

```TypeScript
获取ID为100的系统账号关联的SN码。
```

## getSerialNumberByOsAccountLocalId

```TypeScript
getSerialNumberByOsAccountLocalId(localId: number): Promise<number>
```

通过系统账号ID获取与该系统账号关联的SN码。使用Promise异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getSerialNumberForOsAccountLocalId](#getserialnumberforosaccountlocalid)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getSerialNumberForOsAccountLocalId](#getserialnumberforosaccountlocalid)(localId: number)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回与该系统账号关联的SN码。 |

**示例**

参见 [getSerialNumberByOsAccountLocalId](#getserialnumberbyosaccountlocalid)

## getSerialNumberForOsAccountLocalId

```TypeScript
getSerialNumberForOsAccountLocalId(localId: number, callback: AsyncCallback<number>): void
```

通过系统账号ID获取与该系统账号关联的SN码。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。如果获取成功，err为null，data为与该系统账号关联的SN码；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

```TypeScript
获取ID为100的系统账号关联的SN码。
```

## getSerialNumberForOsAccountLocalId

```TypeScript
getSerialNumberForOsAccountLocalId(localId: number): Promise<number>
```

通过系统账号ID获取与该系统账号关联的SN码。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回与该系统账号关联的SN码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例**

参见 [getSerialNumberForOsAccountLocalId](#getserialnumberforosaccountlocalid)

## isMultiOsAccountEnable

```TypeScript
isMultiOsAccountEnable(callback: AsyncCallback<boolean>): void
```

判断是否支持多系统账号。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [checkMultiOsAccountEnabled](#checkmultiosaccountenabled)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [checkMultiOsAccountEnabled](#checkmultiosaccountenabled)(callback: AsyncCallback&lt;boolean&gt;)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示支持多系统账号；返回false表示不支持。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.isMultiOsAccountEnable((err: BusinessError, isEnabled: boolean) => {
  if (err) {
    console.error(`isMultiOsAccountEnable failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('isMultiOsAccountEnable successfully, isEnabled: ' + isEnabled);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.isMultiOsAccountEnable().then((isEnabled: boolean) => {
  console.info('isMultiOsAccountEnable successfully, isEnabled: ' + isEnabled);
}).catch((err: BusinessError) => {
  console.error(`isMultiOsAccountEnable failed, code is ${err.code}, message is ${err.message}`);
});
```

## isMultiOsAccountEnable

```TypeScript
isMultiOsAccountEnable(): Promise<boolean>
```

判断是否支持多系统账号。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [checkMultiOsAccountEnabled](#checkmultiosaccountenabled)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [checkMultiOsAccountEnabled](#checkmultiosaccountenabled)()

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示支持多系统账号；返回false表示不支持。 |

**示例**

参见 [isMultiOsAccountEnable](#ismultiosaccountenable)

## isOsAccountActived

```TypeScript
isOsAccountActived(localId: number, callback: AsyncCallback<boolean>): void
```

判断指定系统账号是否处于激活状态。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。替代方法仅向系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示账号已激活；返回false表示账号未激活。 |

**示例**

```TypeScript
判断ID为100的系统账号是否处于激活状态。
```

## isOsAccountActived

```TypeScript
isOsAccountActived(localId: number): Promise<boolean>
```

判断指定系统账号是否处于激活状态。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。替代方法仅向系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示账号已激活；返回false表示账号未激活。 |

**示例**

参见 [isOsAccountActived](#isosaccountactived)

## isOsAccountConstraintEnable

```TypeScript
isOsAccountConstraintEnable(localId: number, constraint: string, callback: AsyncCallback<boolean>): void
```

判断指定系统账号是否具有指定约束。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。替代方法仅向系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| constraint | string | 是 | 指定的[约束](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md)名称。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示已使能指定的约束；返回false表示未使能指定的约束。 |

**示例**

```TypeScript
判断ID为100的系统账号是否有禁止使用Wi-Fi的约束。
```

## isOsAccountConstraintEnable

```TypeScript
isOsAccountConstraintEnable(localId: number, constraint: string): Promise<boolean>
```

判断指定系统账号是否具有指定约束。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。替代方法仅向系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| constraint | string | 是 | 指定的[约束](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md)名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示已使能指定的约束；返回false表示未使能指定的约束。 |

**示例**

参见 [isOsAccountConstraintEnable](#isosaccountconstraintenable)

## isOsAccountConstraintEnabled

```TypeScript
isOsAccountConstraintEnabled(constraint: string): Promise<boolean>
```

判断当前系统账号是否使能指定约束。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraint | string | 是 | 指定的[约束](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md)名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示已使能指定的约束；返回false表示未使能指定的约束。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
判断当前系统账号是否有禁止使用Wi-Fi的约束。
```

```TypeScript
判断ID为100的系统账号是否有禁止使用Wi-Fi的约束。
```

## isOsAccountUnlocked

```TypeScript
isOsAccountUnlocked(): Promise<boolean>
```

检查当前系统账号是否已解锁。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前账号已解锁；返回false表示当前账号未解锁。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.isOsAccountUnlocked().then((isVerified: boolean) => {
    console.info('isOsAccountUnlocked successfully, isVerified: ' + isVerified);
  }).catch((err: BusinessError) => {
    console.error(`isOsAccountUnlocked failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`isOsAccountUnlocked exception: code is ${err.code}, message is ${err.message}`);
}
```

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

## isOsAccountVerified

```TypeScript
isOsAccountVerified(callback: AsyncCallback<boolean>): void
```

检查当前系统账号是否已验证。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [checkOsAccountVerified](#checkosaccountverified)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [checkOsAccountVerified](#checkosaccountverified)(callback: AsyncCallback&lt;boolean&gt;)

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示当前账号已验证；返回false表示当前账号未验证。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.isOsAccountVerified((err: BusinessError, isVerified: boolean) => {
  if (err) {
    console.error(`isOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('isOsAccountVerified successfully, isVerified: ' + isVerified);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId为系统账号ID，请通过getOsAccountLocalId接口获取
let localId: number = 100;
accountManager.isOsAccountVerified(localId, (err: BusinessError, isVerified: boolean) => {
  if (err) {
    console.error(`isOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('isOsAccountVerified successfully, isVerified: ' + isVerified);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.isOsAccountVerified().then((isVerified: boolean) => {
  console.info('isOsAccountVerified successfully, isVerified: ' + isVerified);
}).catch((err: BusinessError) => {
  console.error(`isOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
});
```

## isOsAccountVerified

```TypeScript
isOsAccountVerified(localId: number, callback: AsyncCallback<boolean>): void
```

检查指定系统账号是否已验证。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。替代方法仅向系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 系统账号ID。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示指定账号已验证；返回false表示指定账号未验证。 |

**示例**

参见 [isOsAccountVerified](#isosaccountverified)

## isOsAccountVerified

```TypeScript
isOsAccountVerified(localId?: number): Promise<boolean>
```

检查指定系统账号是否已验证。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。替代方法仅向系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 否 | 系统账号ID。不填则检查当前系统账号是否已验证，默认为-1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示指定账号已验证；返回false表示指定账号未验证。 |

**示例**

参见 [isOsAccountVerified](#isosaccountverified)

## isTestOsAccount

```TypeScript
isTestOsAccount(callback: AsyncCallback<boolean>): void
```

检查当前系统账号是否为测试账号。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [checkOsAccountTestable](#checkosaccounttestable)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [checkOsAccountTestable](#checkosaccounttestable)(callback: AsyncCallback&lt;boolean&gt;)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示当前账号为测试账号；返回false表示当前账号非测试账号。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.isTestOsAccount((err: BusinessError, isTestable: boolean) => {
  if (err) {
    console.error(`isTestOsAccount failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('isTestOsAccount successfully, isTestable: ' + isTestable);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  accountManager.isTestOsAccount().then((isTestable: boolean) => {
    console.info('isTestOsAccount successfully, isTestable: ' + isTestable);
  }).catch((err: BusinessError) => {
    console.error(`isTestOsAccount failed, code is ${err.code}, message is ${err.message}`);
});
```

## isTestOsAccount

```TypeScript
isTestOsAccount(): Promise<boolean>
```

检查当前系统账号是否为测试账号。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [checkOsAccountTestable](#checkosaccounttestable)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [checkOsAccountTestable](#checkosaccounttestable)()

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前账号为测试账号；返回false表示当前账号非测试账号。 |

**示例**

参见 [isTestOsAccount](#istestosaccount)

## queryActivatedOsAccountIds

```TypeScript
queryActivatedOsAccountIds(callback: AsyncCallback<Array<number>>): void
```

查询当前处于激活状态的系统账号的ID列表。使用callback异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getActivatedOsAccountLocalIds](#getactivatedosaccountlocalids)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getActivatedOsAccountLocalIds](#getactivatedosaccountlocalids)(callback: AsyncCallback&lt;Array&lt;number&gt;&gt;)

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | 回调函数。如果查询成功，err为null，data为当前处于激活状态的系统账号的ID列表；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.queryActivatedOsAccountIds((err: BusinessError, idArray: number[]) => {
  if (err) {
    console.error(`queryActivatedOsAccountIds code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('queryActivatedOsAccountIds idArray length:' + idArray.length);
    for (let i = 0; i < idArray.length; i++) {
      console.info('activated os account id: ' + idArray[i]);
    }
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.queryActivatedOsAccountIds().then((idArray: number[]) => {
  console.info('queryActivatedOsAccountIds, idArray: ' + idArray);
}).catch((err: BusinessError) => {
  console.error(`queryActivatedOsAccountIds err: code is ${err.code}, message is ${err.message}`);
});
```

## queryActivatedOsAccountIds

```TypeScript
queryActivatedOsAccountIds(): Promise<Array<number>>
```

查询当前处于激活状态的系统账号的ID列表。使用Promise异步回调。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getActivatedOsAccountLocalIds](#getactivatedosaccountlocalids)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getActivatedOsAccountLocalIds](#getactivatedosaccountlocalids)()

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise对象，返回当前处于激活状态的系统账号的ID列表。 |

**示例**

参见 [queryActivatedOsAccountIds](#queryactivatedosaccountids)

## queryCurrentOsAccount

```TypeScript
queryCurrentOsAccount(callback: AsyncCallback<OsAccountInfo>): void
```

查询当前进程所属的系统账号的信息。使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。替代方法仅向系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i.md)&gt; | 是 | 回调函数。如果查询成功，err为null，data为当前进程所属的系统账号信息；否则为错误对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.queryCurrentOsAccount((err: BusinessError, curAccountInfo: osAccount.OsAccountInfo)=>{
  if (err) {
    console.error(`queryCurrentOsAccount code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('queryCurrentOsAccount curAccountInfo:' + JSON.stringify(curAccountInfo));
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.queryCurrentOsAccount().then((accountInfo: osAccount.OsAccountInfo) => {
  console.info('queryCurrentOsAccount, accountInfo: ' + JSON.stringify(accountInfo));
}).catch((err: BusinessError) => {
  console.error(`queryCurrentOsAccount err: code is ${err.code}, message is ${err.message}`);
});
```

## queryCurrentOsAccount

```TypeScript
queryCurrentOsAccount(): Promise<OsAccountInfo>
```

查询当前进程所属的系统账号的信息。使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。替代方法仅向系统应用开放。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i.md)&gt; | Promise对象，返回当前进程所属的系统账号信息。 |

**示例**

参见 [queryCurrentOsAccount](#querycurrentosaccount)

## queryDistributedVirtualDeviceId

```TypeScript
queryDistributedVirtualDeviceId(callback: AsyncCallback<string>): void
```

获取分布式虚拟设备ID。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC or ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。如果获取成功，err为null，data为分布式虚拟设备ID；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.queryDistributedVirtualDeviceId((err: BusinessError, virtualID: string) => {
    if (err) {
      console.error(`queryDistributedVirtualDeviceId err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('queryDistributedVirtualDeviceId virtualID: ' + virtualID);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryDistributedVirtualDeviceId exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.queryDistributedVirtualDeviceId().then((virtualID: string) => {
    console.info('queryDistributedVirtualDeviceId, virtualID: ' + virtualID);
  }).catch((err: BusinessError) => {
    console.error(`queryDistributedVirtualDeviceId err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryDistributedVirtualDeviceId exception: code is ${err.code}, message is ${err.message}`);
}
```

## queryDistributedVirtualDeviceId

```TypeScript
queryDistributedVirtualDeviceId(): Promise<string>
```

获取分布式虚拟设备ID。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC or ohos.permission.MANAGE_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.Account.OsAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回分布式虚拟设备ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例**

参见 [queryDistributedVirtualDeviceId](#querydistributedvirtualdeviceid)
