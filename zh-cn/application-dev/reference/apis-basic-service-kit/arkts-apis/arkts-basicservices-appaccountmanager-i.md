# AppAccountManager

应用账号管理器，可用于管理应用自身的账号信息。

**起始版本：** 7

**系统能力：** SystemCapability.Account.AppAccount

## addAccount

```TypeScript
addAccount(name: string, callback: AsyncCallback<void>): void
```

根据账号名添加应用账号。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [createAccount](arkts-basicservices-appaccountmanager-i.md#createaccount-1)替
> 代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** createAccount(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当创建成功时，err为null，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.addAccount('WangWu', (err: BusinessError) => { 
  console.error(`addAccount err: code is ${err.code}, message is ${err.message}`);
});

```

## addAccount

```TypeScript
addAccount(name: string, extraInfo: string, callback: AsyncCallback<void>): void
```

根据账号名和额外信息添加应用账号。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [createAccount](arkts-basicservices-appaccountmanager-i.md#createaccount-2)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** createAccount(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| extraInfo | string | 是 | 额外信息(能转换string类型的其它信息)，额外信息不能是应用账号的敏感信息（如应用账号密码、token等）。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当创建成功时，err为null，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.addAccount('LiSi', 'token101', (err: BusinessError) => { 
  console.error(`addAccount err: code is ${err.code}, message is ${err.message}`);
});

```

## addAccount

```TypeScript
addAccount(name: string, extraInfo?: string): Promise<void>
```

根据账号名和额外信息添加应用账号。使用Promise异步回调。

> **说明：**
> > 从API version 7开始支持，从API version 9开始废弃。建议使用
> [createAccount](arkts-basicservices-appaccountmanager-i.md#createaccount-3)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** createAccount(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| extraInfo | string | 否 | 额外信息(能转换string类型的其它信息)，额外信息不能是应用账号的敏感信息（如应用账号密码、token等），默认为空，表示创建的该账号无额外信息需要添加。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.addAccount('LiSi', 'token101').then(()=> { 
  console.info('addAccount Success');
}).catch((err: BusinessError) => {
  console.error(`addAccount err: code is ${err.code}, message is ${err.message}`);
});

```

## addAccountImplicitly

```TypeScript
addAccountImplicitly(
      owner: string,
      authType: string,
      options: { [key: string]: any },
      callback: AuthenticatorCallback
    ): void
```

根据指定的账号所有者隐式地添加应用账号。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [createAccountImplicitly](arkts-basicservices-appaccountmanager-i.md#createaccountimplicitly-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** createAccountImplicitly(owner:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| options | { [key: string]: any } | 是 | 鉴权所需要的可选项。可选项可根据自己需要设置。 |
| callback | AuthenticatorCallback | 是 | 认证器回调对象，返回添加结果。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, result: Record<string, Object>): void {
    console.info('resultCode: ' + code);
    console.info('result: ' + JSON.stringify(result));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
    })
  }

  aboutToAppear(): void {
    appAccountManager.addAccountImplicitly('com.example.accountjsdemo', 'getSocialData', {}, {
      onResult: this.onResultCallback,
      onRequestRedirected: this.onRequestRedirectedCallback
    });
  }

  build() {}
}

```

## auth

```TypeScript
auth(name: string, owner: string, authType: string, callback: AuthCallback): void
```

对应用账号进行鉴权以获取授权令牌。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| callback | AuthCallback | 是 | 回调对象，返回鉴权结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, owner or authType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, authResult?: appAccount.AuthResult): void {
    console.info('resultCode: ' + code);
    console.info('authResult: ' + JSON.stringify(authResult));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
    })
  }

  aboutToAppear(): void {
    try {
      appAccountManager.auth('LiSi', 'com.example.accountjsdemo', 'getSocialData', {
        onResult: this.onResultCallback,
        onRequestRedirected: this.onRequestRedirectedCallback
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`auth exception: code is ${err.code}, message is ${err.message}`);
    }
  }

  build() {}
}

```

## auth

```TypeScript
auth(
      name: string,
      owner: string,
      authType: string,
      options: Record<string, Object>,
      callback: AuthCallback
    ): void
```

对应用账号进行鉴权以获取授权令牌。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| options | Record&lt;string, Object&gt; | 是 | 鉴权所需的可选项。 |
| callback | AuthCallback | 是 | 回调对象，返回鉴权结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, owner, authType or options. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, authResult?: appAccount.AuthResult): void {
    console.info('resultCode: ' + code);
    console.info('authResult: ' + JSON.stringify(authResult));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
    })
  }

  aboutToAppear(): void {
    let options: Record<string, Object> = {
      'password': 'xxxx',
    };
    try {
      appAccountManager.auth('LiSi', 'com.example.accountjsdemo', 'getSocialData', options, {
        onResult: this.onResultCallback,
        onRequestRedirected: this.onRequestRedirectedCallback
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`auth exception: code is ${err.code}, message is ${err.message}`);
    }
  }

  build() {}
}

```

## authenticate

```TypeScript
authenticate(
      name: string,
      owner: string,
      authType: string,
      options: { [key: string]: any },
      callback: AuthenticatorCallback
    ): void
```

对应用账号进行鉴权以获取授权令牌。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [auth](arkts-basicservices-appaccountmanager-i.md#auth-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** auth(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| options | { [key: string]: any } | 是 | 鉴权所需的可选项。 |
| callback | AuthenticatorCallback | 是 | 回调对象，返回鉴权结果。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, result: Record<string, Object>): void {
    console.info('resultCode: ' + code);
    console.info('result: ' + JSON.stringify(result));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
    })
  }

  aboutToAppear(): void {
    appAccountManager.authenticate('LiSi', 'com.example.accountjsdemo', 'getSocialData', {}, {
      onResult: this.onResultCallback,
      onRequestRedirected: this.onRequestRedirectedCallback
    });
  }

  build() {}
}

```

## checkAccountLabels

```TypeScript
checkAccountLabels(name: string, owner: string, labels: Array<string>, callback: AsyncCallback<boolean>): void
```

检查指定应用账号是否满足特定的标签集合。使用callback异步回调。该方法依赖目标应用的认证器提供标签检查的能力。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| labels | Array&lt;string&gt; | 是 | 标签数组。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当检查成功时，err为null，data为true表示满足特定的标签集合，data为false表示不满足；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, owner or labels. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let labels = ['student'];
try {
  appAccountManager.checkAccountLabels('zhangsan', 'com.example.accountjsdemo', labels,
    (err: BusinessError, hasAllLabels: boolean) => {
      if (err) {
        console.error(`checkAccountLabels failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('checkAccountLabels successfully, hasAllLabels: ' + hasAllLabels);
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAccountLabels exception: code is ${err.code}, message is ${err.message}`);
}

```

## checkAccountLabels

```TypeScript
checkAccountLabels(name: string, owner: string, labels: Array<string>): Promise<boolean>
```

检查指定应用账号是否满足特定的标签集合。使用Promise异步回调。该方法依赖目标应用的认证器提供标签检查的能力。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| labels | Array&lt;string&gt; | 是 | 标签数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示指定账号满足特定的标签集合，返回false表示不满足。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, owner or labels. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let labels = ['student'];
try {
  appAccountManager.checkAccountLabels('zhangsan', 'com.example.accountjsdemo', labels).then((
    hasAllLabels: boolean) => {
    console.info('checkAccountLabels successfully: ' + hasAllLabels);
  }).catch((err: BusinessError) => {
    console.error(`checkAccountLabels failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAccountLabels exception: code is ${err.code}, message is ${err.message}`);
}

```

## checkAppAccess

```TypeScript
checkAppAccess(name: string, bundleName: string, callback: AsyncCallback<boolean>): void
```

检查指定应用对特定账号的数据是否可访问。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| bundleName | string | 是 | 第三方应用的包名。最大长度为512个字符。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。返回true表示指定应用可访问特定账号的数据；返回false表示不可访问。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or bundleName. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkAppAccess('ZhangSan', 'com.example.accountjsdemo',
    (err: BusinessError, isAccessible: boolean) => {
      if (err) {
        console.error(`checkAppAccess failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('checkAppAccess successfully');
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAppAccess exception: code is ${err.code}, message is ${err.message}`);
}

```

## checkAppAccess

```TypeScript
checkAppAccess(name: string, bundleName: string): Promise<boolean>
```

检查指定应用对特定账号的数据是否可访问。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| bundleName | string | 是 | 第三方应用的包名。最大长度为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示指定应用可访问特定账号的数据；返回false表示不可访问。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or bundleName. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkAppAccess('ZhangSan', 'com.example.accountjsdemo').then((isAccessible: boolean) => {
    console.info('checkAppAccess successfully, isAccessible: ' + isAccessible);
  }).catch((err: BusinessError) => {
    console.error(`checkAppAccess failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAppAccess exception: code is ${err.code}, message is ${err.message}`);
}

```

## checkAppAccountSyncEnable

```TypeScript
checkAppAccountSyncEnable(name: string, callback: AsyncCallback<boolean>): void
```

检查指定应用账号是否开启数据同步功能。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [checkDataSyncEnabled](arkts-basicservices-appaccountmanager-i.md#checkdatasyncenabled-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** checkDataSyncEnabled(name:

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。返回true表示指定应用账号已开启数据同步功能；返回false表示未开启。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.checkAppAccountSyncEnable('ZhangSan', (err: BusinessError, result: boolean) => { 
  if (err) {
    console.error(`checkAppAccountSyncEnable code: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('checkAppAccountSyncEnable result: ' + result);
  }
});

```

## checkAppAccountSyncEnable

```TypeScript
checkAppAccountSyncEnable(name: string): Promise<boolean>
```

检查指定应用账号是否开启数据同步功能。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [checkDataSyncEnabled](arkts-basicservices-appaccountmanager-i.md#checkdatasyncenabled-2)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** checkDataSyncEnabled(name:

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示指定应用账号已开启数据同步功能；返回false表示未开启。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.checkAppAccountSyncEnable('ZhangSan').then((data: boolean) => { 
  console.info('checkAppAccountSyncEnable, result: ' + data);
}).catch((err: BusinessError) => {
  console.error(`checkAppAccountSyncEnable err: code is ${err.code}, message is ${err.message}`);
});

```

## checkAuthTokenVisibility

```TypeScript
checkAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback<boolean>): void
```

检查指定应用账号的特定鉴权类型的授权令牌对指定应用的可见性。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| bundleName | string | 是 | 检查可见性的应用包名。最大长度为512个字符。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当检查成功时，err为null，data为true表示可见，data为false表示不可见；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, authType or bundleName. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300107](../../apis-basic-services-kit/errorcode-account.md#12300107-认证类型不存在) | AuthType not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo',
    (err: BusinessError, isVisible: boolean) => {
      if (err) {
        console.error(`checkAuthTokenVisibility failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('checkAuthTokenVisibility successfully, isVisible: ' + isVisible);
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAuthTokenVisibility exception: code is ${err.code}, message is ${err.message}`);
}

```

## checkAuthTokenVisibility

```TypeScript
checkAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise<boolean>
```

检查指定应用账号的特定鉴权类型的授权令牌对指定应用的可见性。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| bundleName | string | 是 | 用于检查可见性的应用包名。最大长度为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示授权令牌对指定应用的可见，返回false表示不可见。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, authType or bundleName. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300107](../../apis-basic-services-kit/errorcode-account.md#12300107-认证类型不存在) | AuthType not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo').then((
    isVisible: boolean) => {
    console.info('checkAuthTokenVisibility successfully, isVisible: ' + isVisible);
  }).catch((err: BusinessError) => {
    console.error(`checkAuthTokenVisibility failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAuthTokenVisibility exception: code is ${err.code}, message is ${err.message}`);
}

```

## checkDataSyncEnabled

```TypeScript
checkDataSyncEnabled(name: string, callback: AsyncCallback<boolean>): void
```

检查指定应用账号是否开启数据同步功能。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。返回true表示指定应用账号已开启数据同步功能；返回false表示未开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkDataSyncEnabled('ZhangSan', (err: BusinessError, isEnabled: boolean) => {
    if (err) {
      console.error(`checkDataSyncEnabled failed, err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkDataSyncEnabled successfully, isEnabled: ' + isEnabled);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
}

```

## checkDataSyncEnabled

```TypeScript
checkDataSyncEnabled(name: string): Promise<boolean>
```

检查指定应用账号是否开启数据同步功能。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示指定应用账号已开启数据同步功能；返回false表示未开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkDataSyncEnabled('ZhangSan').then((isEnabled: boolean) => {
      console.info('checkDataSyncEnabled successfully, isEnabled: ' + isEnabled);
  }).catch((err: BusinessError) => {
    console.error(`checkDataSyncEnabled failed, err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
}

```

## checkOAuthTokenVisibility

```TypeScript
checkOAuthTokenVisibility(
      name: string,
      authType: string,
      bundleName: string,
      callback: AsyncCallback<boolean>
    ): void
```

检查指定应用账号的特定鉴权类型的授权令牌对指定应用的可见性。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [checkAuthTokenVisibility](arkts-basicservices-appaccountmanager-i.md#checkauthtokenvisibility-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** checkAuthTokenVisibility(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| bundleName | string | 是 | 检查可见性的应用包名。最大长度为512个字符。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当检查成功时，err为null，data为true表示可见，data为false表示不可见；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.checkOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo',
  (err: BusinessError, data: boolean) => {
    if (err) {
      console.error(`checkOAuthTokenVisibility err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkOAuthTokenVisibility isVisible: ' + data);
    }
  });

```

## checkOAuthTokenVisibility

```TypeScript
checkOAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise<boolean>
```

检查指定应用账号的特定鉴权类型的授权令牌对指定应用的可见性。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [checkAuthTokenVisibility](arkts-basicservices-appaccountmanager-i.md#checkauthtokenvisibility-2)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** checkAuthTokenVisibility(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| bundleName | string | 是 | 用于检查可见性的应用包名。最大长度为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示指定鉴权类型的OAuth令牌对特定应用的可见，返回false表示不可见。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.checkOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo').then((
  data: boolean) => {
  console.info('checkOAuthTokenVisibility isVisible: ' + data);
}).catch((err: BusinessError) => {
  console.error(`checkOAuthTokenVisibility err: code is ${err.code}, message is ${err.message}`);
});

```

## createAccount

```TypeScript
createAccount(name: string, callback: AsyncCallback<void>): void
```

根据账号名创建应用账号。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当创建成功时，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name. |
| [12300004](../../apis-basic-services-kit/errorcode-account.md#12300004-账号已存在) | Account already exists. |
| [12300007](../../apis-basic-services-kit/errorcode-account.md#12300007-账号数量已达上限) | The number of accounts reaches the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.createAccount('WangWu', (err: BusinessError) => { 
    if (err) {
      console.error(`createAccount code: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('createAccount successful.');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`createAccount err: code is ${err.code}, message is ${err.message}`);
}

```

## createAccount

```TypeScript
createAccount(name: string, options: CreateAccountOptions, callback: AsyncCallback<void>): void
```

根据账号名和可选项创建应用账号。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| options | CreateAccountOptions | 是 | 创建应用账号的选项，可提供自定义数据，但不建议包含敏感数据（如密码、Token等）。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当创建成功时，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or options. |
| [12300004](../../apis-basic-services-kit/errorcode-account.md#12300004-账号已存在) | Account already exists. |
| [12300007](../../apis-basic-services-kit/errorcode-account.md#12300007-账号数量已达上限) | The number of accounts reaches the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.CreateAccountOptions = {
  customData: {
    age: '10'
  }
}
try {
  appAccountManager.createAccount('LiSi', options, (err: BusinessError) => {
    if (err) {
      console.error(`createAccount failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('createAccount successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`createAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

## createAccount

```TypeScript
createAccount(name: string, options?: CreateAccountOptions): Promise<void>
```

根据账号名和可选项创建应用账号。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| options | CreateAccountOptions | 否 | 创建应用账号的选项，可提供自定义数据，但不建议包含敏感数据（如密码、Token等）。不填无影响，默认为空，表示创建的该账号无额外信息需要添加。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or options. |
| [12300004](../../apis-basic-services-kit/errorcode-account.md#12300004-账号已存在) | Account already exists. |
| [12300007](../../apis-basic-services-kit/errorcode-account.md#12300007-账号数量已达上限) | The number of accounts reaches the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.CreateAccountOptions = {
  customData: {
    age: '10'
  }
}
try {
  appAccountManager.createAccount('LiSi', options).then(() => {
    console.info('createAccount successfully');
  }).catch((err: BusinessError) => {
    console.error(`createAccount failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`createAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

## createAccountImplicitly

```TypeScript
createAccountImplicitly(owner: string, callback: AuthCallback): void
```

根据指定的账号所有者隐式地创建应用账号。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| callback | AuthCallback | 是 | 认证器回调对象，返回创建结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid owner. |
| [12300007](../../apis-basic-services-kit/errorcode-account.md#12300007-账号数量已达上限) | The number of accounts reaches the upper limit. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, result?: appAccount.AuthResult): void {
    console.info('resultCode: ' + code);
    console.info('result: ' + JSON.stringify(result));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
    })
  }

  aboutToAppear(): void {
    try {
      appAccountManager.createAccountImplicitly('com.example.accountjsdemo', {
        onResult: this.onResultCallback,
        onRequestRedirected: this.onRequestRedirectedCallback
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`createAccountImplicitly exception: code is ${err.code}, message is ${err.message}`);
    }
  }
  build() {}
}

```

## createAccountImplicitly

```TypeScript
createAccountImplicitly(owner: string, options: CreateAccountImplicitlyOptions, callback: AuthCallback): void
```

根据指定的账号所有者和可选项隐式地创建应用账号。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| options | CreateAccountImplicitlyOptions | 是 | 隐式创建账号的选项。 |
| callback | AuthCallback | 是 | 认证器回调对象，返回创建结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid owner or options. |
| [12300007](../../apis-basic-services-kit/errorcode-account.md#12300007-账号数量已达上限) | The number of accounts reaches the upper limit. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, result?: appAccount.AuthResult): void {
    console.info('resultCode: ' + code);
    console.info('result: ' + JSON.stringify(result));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
    })
  }

  aboutToAppear(): void {
    let options: appAccount.CreateAccountImplicitlyOptions = {
      authType: 'getSocialData',
      requiredLabels: ['student']
    };
    try {
      appAccountManager.createAccountImplicitly('com.example.accountjsdemo', options, {
        onResult: this.onResultCallback,
        onRequestRedirected: this.onRequestRedirectedCallback
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`createAccountImplicitly exception: code is ${err.code}, message is ${err.message}`);
    }
  }
  build() {}
}

```

## deleteAccount

```TypeScript
deleteAccount(name: string, callback: AsyncCallback<void>): void
```

删除应用账号。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [removeAccount](arkts-basicservices-appaccountmanager-i.md#removeaccount-1)替
> 代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** removeAccount(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当删除成功时，err为null，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.deleteAccount('ZhaoLiu', (err: BusinessError) => { 
  console.error(`deleteAccount err: code is ${err.code}, message is ${err.message}`);
});

```

## deleteAccount

```TypeScript
deleteAccount(name: string): Promise<void>
```

删除应用账号。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [removeAccount](arkts-basicservices-appaccountmanager-i.md#removeaccount-2)替
> 代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** removeAccount(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.deleteAccount('ZhaoLiu').then(() => { 
  console.info('deleteAccount Success');
}).catch((err: BusinessError) => {
  console.error(`deleteAccount err: code is ${err.code}, message is ${err.message}`);
});

```

## deleteAuthToken

```TypeScript
deleteAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback<void>): void
```

删除指定应用账号的特定鉴权类型的授权令牌。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| token | string | 是 | 授权令牌。最大长度为1024个字符。如果授权令牌不存在，则不执行任何操作。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当删除成功时，err为null；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, owner, authType or token. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300107](../../apis-basic-services-kit/errorcode-account.md#12300107-认证类型不存在) | AuthType not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.deleteAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx',
    (err: BusinessError) => {
      if (err) {
        console.error(`deleteAuthToken failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('deleteAuthToken successfully');
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`deleteAuthToken exception: code is ${err.code}, message is ${err.message}`);
}

```

## deleteAuthToken

```TypeScript
deleteAuthToken(name: string, owner: string, authType: string, token: string): Promise<void>
```

删除指定应用账号的特定鉴权类型的授权令牌。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| token | string | 是 | 授权令牌。最大长度为1024个字符。如果授权令牌不存在，则不执行任何操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, owner, authType or token. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300107](../../apis-basic-services-kit/errorcode-account.md#12300107-认证类型不存在) | AuthType not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.deleteAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx').then(() => {
    console.info('deleteAuthToken successfully');
  }).catch((err: BusinessError) => {
    console.error(`deleteAuthToken failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`deleteAuthToken exception: code is ${err.code}, message is ${err.message}`);
}

```

## deleteCredential

```TypeScript
deleteCredential(name: string, credentialType: string, callback: AsyncCallback<void>): void
```

删除指定应用账号的特定类型的凭据信息。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| credentialType | string | 是 | 凭据类型。自定义的类型，最大长度为1024个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当删除成功时，err为null；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or credentialType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | Credential not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.deleteCredential('zhangsan', 'PIN_SIX', (err: BusinessError) => {
    if (err) {
      console.error(`deleteCredential failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('deleteCredential successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`deleteCredential exception: code is ${err.code}, message is ${err.message}`);
}

```

## deleteCredential

```TypeScript
deleteCredential(name: string, credentialType: string): Promise<void>
```

删除指定应用账号的特定类型的凭据信息。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| credentialType | string | 是 | 凭据类型。自定义的类型，最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or credentialType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | Credential not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.deleteCredential('zhangsan', 'PIN_SIX').then(() => {
    console.info('deleteCredential successfully');
  }).catch((err: BusinessError) => {
    console.error(`deleteCredential failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`deleteCredential exception: code is ${err.code}, message is ${err.message}`);
}

```

## deleteOAuthToken

```TypeScript
deleteOAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback<void>): void
```

删除指定应用账号的特定鉴权类型的授权令牌。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [deleteAuthToken](arkts-basicservices-appaccountmanager-i.md#deleteauthtoken-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteAuthToken(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| token | string | 是 | 授权令牌。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当删除成功时，err为null；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.deleteOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx',
  (err: BusinessError) => {
    if (err) {
      console.error(`deleteOAuthToken err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('deleteOAuthToken successful.');
    }
  });

```

## deleteOAuthToken

```TypeScript
deleteOAuthToken(name: string, owner: string, authType: string, token: string): Promise<void>
```

删除指定应用账号的特定鉴权类型的授权令牌。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [deleteAuthToken](arkts-basicservices-appaccountmanager-i.md#deleteauthtoken-2)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteAuthToken(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| token | string | 是 | 授权令牌。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.deleteOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx').then(() => {
  console.info('deleteOAuthToken successfully');
}).catch((err: BusinessError) => {
  console.error(`deleteOAuthToken err: code is ${err.code}, message is ${err.message}`);
});

```

## disableAppAccess

```TypeScript
disableAppAccess(name: string, bundleName: string, callback: AsyncCallback<void>): void
```

禁止指定第三方应用账号名称对指定的第三方应用进行访问。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setAppAccess](arkts-basicservices-appaccountmanager-i.md#setappaccess-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setAppAccess(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| bundleName | string | 是 | 第三方应用的包名。最大长度为512个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当禁止指定第三方应用账号名称对指定包名称的第三方应用进行访问设置成功时，err为null，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.disableAppAccess('ZhangSan', 'com.example.accountjsdemo', (err: BusinessError) => { 
  console.error(`disableAppAccess err: code is ${err.code}, message is ${err.message}`);
});

```

## disableAppAccess

```TypeScript
disableAppAccess(name: string, bundleName: string): Promise<void>
```

禁止指定第三方应用账号名称对指定包名称的第三方应用进行访问。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setAppAccess](arkts-basicservices-appaccountmanager-i.md#setappaccess-2)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setAppAccess(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要禁用访问的第三方应用账号的名称。最大长度为512个字符。 |
| bundleName | string | 是 | 第三方应用的包名。最大长度为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.disableAppAccess('ZhangSan', 'com.example.accountjsdemo').then(() => { 
  console.info('disableAppAccess Success');
}).catch((err: BusinessError) => {
  console.error(`disableAppAccess err: code is ${err.code}, message is ${err.message}`);
});

```

## enableAppAccess

```TypeScript
enableAppAccess(name: string, bundleName: string, callback: AsyncCallback<void>): void
```

允许指定第三方应用账号名称对指定包名称的第三方应用进行访问。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setAppAccess](arkts-basicservices-appaccountmanager-i.md#setappaccess-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setAppAccess(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| bundleName | string | 是 | 第三方应用的包名。最大长度为512个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当允许指定第三方应用账号名称对指定包名称的第三方应用进行访问设置成功时，err为null，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.enableAppAccess('ZhangSan', 'com.example.accountjsdemo', (err: BusinessError) => {
  if (err) {
    console.error(`enableAppAccess err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('enableAppAccess successful.');
  }
});

```

## enableAppAccess

```TypeScript
enableAppAccess(name: string, bundleName: string): Promise<void>
```

允许指定第三方应用账号的名称对指定包名称的第三方应用进行访问。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setAppAccess](arkts-basicservices-appaccountmanager-i.md#setappaccess-2)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setAppAccess(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| bundleName | string | 是 | 第三方应用的包名。最大长度为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.enableAppAccess('ZhangSan', 'com.example.accountjsdemo').then(() => { 
  console.info('enableAppAccess Success');
}).catch((err: BusinessError) => {
  console.error(`enableAppAccess err: code is ${err.code}, message is ${err.message}`);
});

```

## getAccountCredential

```TypeScript
getAccountCredential(name: string, credentialType: string, callback: AsyncCallback<string>): void
```

获取指定应用账号的凭据。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getCredential](arkts-basicservices-appaccountmanager-i.md#getcredential-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getCredential(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| credentialType | string | 是 | 凭据类型。自定义的类型，最大长度为1024个字符。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取凭据成功时，err为null，data为指定应用账号的凭据；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAccountCredential('ZhangSan', 'credentialType001', (err: BusinessError, result: string) => { 
  if (err) {
    console.error(`getAccountCredential err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getAccountCredential result: ' + result);
  }
});

```

## getAccountCredential

```TypeScript
getAccountCredential(name: string, credentialType: string): Promise<string>
```

获取指定应用账号的凭据。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getCredential](arkts-basicservices-appaccountmanager-i.md#getcredential-2)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getCredential(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| credentialType | string | 是 | 凭据类型。自定义的类型，最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回指定应用账号的凭据。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAccountCredential('ZhangSan', 'credentialType001').then((data: string) => { 
  console.info('getAccountCredential, result: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getAccountCredential err: code is ${err.code}, message is ${err.message}`);
});

```

## getAccountExtraInfo

```TypeScript
getAccountExtraInfo(name: string, callback: AsyncCallback<string>): void
```

获取指定应用账号的额外信息（能转换成string类型的其它信息）。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getCustomData](arkts-basicservices-appaccountmanager-i.md#getcustomdata-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getCustomData(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取此应用账号的额外信息成功时，err为null，data返回此应用账号的额外信息对象；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAccountExtraInfo('ZhangSan', (err: BusinessError, result: string) => { 
  if (err) {
    console.error(`getAccountExtraInfo err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getAccountExtraInfo result: ' + result);
  }
});

```

## getAccountExtraInfo

```TypeScript
getAccountExtraInfo(name: string): Promise<string>
```

获取指定应用账号的额外信息（能转换成string类型的其它信息）。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getCustomData](arkts-basicservices-appaccountmanager-i.md#getcustomdata-2)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getCustomData(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回此应用程序账号的额外信息对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAccountExtraInfo('ZhangSan').then((data: string) => { 
  console.info('getAccountExtraInfo, result: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getAccountExtraInfo err: code is ${err.code}, message is ${err.message}`);
});

```

## getAccountsByOwner

```TypeScript
getAccountsByOwner(owner: string, callback: AsyncCallback<Array<AppAccountInfo>>): void
```

根据应用账号所有者获取调用方可访问的应用账号列表。使用callback异步回调。
此方法适用于以下账户：
<br> 本应用的账户。
<br> 第三方应用的账户。要获取此类信息，
<br> 您的应用必须已获得第三方应用的授权，或
<br> 已获得ohos.permission.GET_ALL_APP_ACCOUNTS权限。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt; | 是 | 回调函数。如果获取成功，err为null，data为获取到的应用账号列表；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid owner. |
| [12400001](../../apis-basic-services-kit/errorcode-account.md#12400001-应用不存在) | Application not found.<br>**适用版本：** 9 - 13 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAccountsByOwner('com.example.accountjsdemo2',
    (err: BusinessError, data: appAccount.AppAccountInfo[]) => {
      if (err) {
        console.error(`getAccountsByOwner failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getAccountsByOwner successfully, data:' + JSON.stringify(data));
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAccountsByOwner exception:code is ${err.code}, message is ${err.message}`);
}

```

## getAccountsByOwner

```TypeScript
getAccountsByOwner(owner: string): Promise<Array<AppAccountInfo>>
```

根据应用账号所有者获取调用方可访问的应用账号列表。使用Promise异步回调。
此方法适用于以下账户：
<br> 本应用的账户。
<br> 第三方应用的账户。要获取此类信息，
<br> 您的应用必须已获得第三方应用的授权，或
<br> 已获得ohos.permission.GET_ALL_APP_ACCOUNTS权限。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AppAccountInfo&gt;&gt; | Promise对象，返回获取到的应用账号列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid owner. |
| [12400001](../../apis-basic-services-kit/errorcode-account.md#12400001-应用不存在) | Application not found.<br>**适用版本：** 9 - 13 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAccountsByOwner('com.example.accountjsdemo2').then((
    data: appAccount.AppAccountInfo[]) => {
    console.info('getAccountsByOwner successfully, data: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`getAccountsByOwner failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAccountsByOwner exception: code is ${err.code}, message is ${err.message}`);
}

```

## getAllAccessibleAccounts

```TypeScript
getAllAccessibleAccounts(callback: AsyncCallback<Array<AppAccountInfo>>): void
```

获取所有可访问的应用账号信息。使用callback异步回调。
此方法适用于以下账户：
<br> 本应用的账户。
<br> 第三方应用的账户。要获取此类信息，
<br> 您的应用必须已获得第三方应用的授权。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getAllAccounts](arkts-basicservices-appaccountmanager-i.md#getallaccounts-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getAllAccounts(callback:

**需要权限：** ohos.permission.GET_ALL_APP_ACCOUNTS

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt; | 是 | 回调函数。当查询成功时，err为null，data为获取到的应用账号信息列表；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAllAccessibleAccounts((err: BusinessError, data: appAccount.AppAccountInfo[])=>{
  if (err) {
    console.error(`getAllAccessibleAccounts err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getAllAccessibleAccounts data: ' + JSON.stringify(data));
  }
});

```

## getAllAccessibleAccounts

```TypeScript
getAllAccessibleAccounts(): Promise<Array<AppAccountInfo>>
```

获取所有可访问的应用账号信息。使用Promise异步回调。
此方法适用于以下账户：
<br> 本应用的账户。
<br> 第三方应用的账户。要获取此类信息，
<br> 您的应用必须已获得第三方应用的授权。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用[getAllAccounts](arkts-basicservices-appaccountmanager-i.md#getallaccounts-2)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getAllAccounts()](arkts-basicservices-appaccountmanager-i.md#getallaccounts-2)

**需要权限：** ohos.permission.GET_ALL_APP_ACCOUNTS

**系统能力：** SystemCapability.Account.AppAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AppAccountInfo&gt;&gt; | Promise对象，返回全部应用已授权账号信息对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAllAccessibleAccounts().then((data: appAccount.AppAccountInfo[]) => { 
  console.info('getAllAccessibleAccounts: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getAllAccessibleAccounts err: code is ${err.code}, message is ${err.message}`);
});

```

## getAllAccounts

```TypeScript
getAllAccounts(callback: AsyncCallback<Array<AppAccountInfo>>): void
```

获取所有可访问的应用账号信息。使用callback异步回调。
此方法适用于以下账户：
<br> 本应用的账户。
<br> 第三方应用的账户。要获取此类信息，
<br> 您的应用必须已获得第三方应用的授权，或
<br> 已获得ohos.permission.GET_ALL_APP_ACCOUNTS权限。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt; | 是 | 回调函数。当查询成功时，err为null，data为获取到的应用账号信息列表；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAllAccounts((err: BusinessError, data: appAccount.AppAccountInfo[]) => {
    if (err) {
      console.error(`getAllAccounts failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAllAccounts successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAllAccounts exception: code is ${err.code}, message is ${err.message}`);
}

```

## getAllAccounts

```TypeScript
getAllAccounts(): Promise<Array<AppAccountInfo>>
```

获取所有可访问的应用账号信息。使用Promise异步回调。
此方法适用于以下账户：
<br> 本应用的账户。
<br> 第三方应用的账户。要获取此类信息，
<br> 您的应用必须已获得第三方应用的授权，或
<br> 已获得ohos.permission.GET_ALL_APP_ACCOUNTS权限。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AppAccountInfo&gt;&gt; | Promise对象，返回全部应用已授权账号信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAllAccounts().then((data: appAccount.AppAccountInfo[]) => {
    console.info('getAllAccounts successfully');
  }).catch((err: BusinessError) => {
    console.error(`getAllAccounts failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAllAccounts exception: code is ${err.code}, message is ${err.message}`);
}

```

## getAllAccounts

```TypeScript
getAllAccounts(owner: string, callback: AsyncCallback<Array<AppAccountInfo>>): void
```

根据应用账号所有者获取调用方可访问的应用账号列表。使用callback异步回调。
此方法适用于以下账户：
<br> 本应用的账户。
<br> 第三方应用的账户。要获取此类信息，
<br> 您的应用必须已获得第三方应用的授权。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getAccountsByOwner](arkts-basicservices-appaccountmanager-i.md#getaccountsbyowner-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getAccountsByOwner(owner:

**需要权限：** ohos.permission.GET_ALL_APP_ACCOUNTS

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt; | 是 | 应用账号信息列表。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const selfBundle = 'com.example.actsgetallaaccounts';
appAccountManager.getAllAccounts(selfBundle, (err: BusinessError, data: appAccount.AppAccountInfo[])=>{
  if (err) {
    console.error(`getAllAccounts err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getAllAccounts data:' + JSON.stringify(data));
  }
});

```

## getAllAccounts

```TypeScript
getAllAccounts(owner: string): Promise<Array<AppAccountInfo>>
```

根据应用账号所有者获取调用方可访问的应用账号列表。使用Promise异步回调。
此方法适用于以下账户：
<br> 本应用的账户。
<br> 第三方应用的账户。要获取此类信息，
<br> 您的应用必须已获得第三方应用的授权。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getAccountsByOwner](arkts-basicservices-appaccountmanager-i.md#getaccountsbyowner-2)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getAccountsByOwner(owner:

**需要权限：** ohos.permission.GET_ALL_APP_ACCOUNTS

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AppAccountInfo&gt;&gt; | Promise对象，返回指定应用全部账号信息对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const selfBundle = 'com.example.actsgetallaaccounts';
appAccountManager.getAllAccounts(selfBundle).then((data: appAccount.AppAccountInfo[]) => { 
  console.info('getAllAccounts: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getAllAccounts err: code is ${err.code}, message is ${err.message}`);
});

```

## getAllAuthTokens

```TypeScript
getAllAuthTokens(name: string, owner: string, callback: AsyncCallback<Array<AuthTokenInfo>>): void
```

获取指定账号对调用方可见的所有授权令牌。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;Array&lt;AuthTokenInfo&gt;&gt; | 是 | 回调函数。当获取成功时，err为null，data为授权令牌数组；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or owner. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAllAuthTokens('LiSi', 'com.example.accountjsdemo',
    (err: BusinessError, tokenArr: appAccount.AuthTokenInfo[]) => {
      if (err) {
        console.error(`getAllAuthTokens failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getAllAuthTokens successfully, tokenArr: ' + tokenArr);
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAllAuthTokens exception: code is ${err.code}, message is ${err.message}`);
}

```

## getAllAuthTokens

```TypeScript
getAllAuthTokens(name: string, owner: string): Promise<Array<AuthTokenInfo>>
```

获取指定账号对调用方可见的所有授权令牌。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AuthTokenInfo&gt;&gt; | Promise对象，返回授权令牌数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or owner. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAllAuthTokens('LiSi', 'com.example.accountjsdemo').then((
    tokenArr: appAccount.AuthTokenInfo[]) => {
    console.info('getAllAuthTokens successfully, tokenArr: ' + JSON.stringify(tokenArr));
  }).catch((err: BusinessError) => {
    console.error(`getAllAuthTokens failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAllAuthTokens exception: code is ${err.code}, message is ${err.message}`);
}

```

## getAllOAuthTokens

```TypeScript
getAllOAuthTokens(name: string, owner: string, callback: AsyncCallback<Array<OAuthTokenInfo>>): void
```

获取指定账号对调用方可见的所有授权令牌。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getAllAuthTokens](arkts-basicservices-appaccountmanager-i.md#getallauthtokens-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAllAuthTokens(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;Array&lt;OAuthTokenInfo&gt;&gt; | 是 | 回调函数。当获取成功时，err为null，data为授权令牌数组；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAllOAuthTokens('LiSi', 'com.example.accountjsdemo',
  (err: BusinessError, data: appAccount.OAuthTokenInfo[]) => {
    if (err) {
      console.error(`getAllOAuthTokens err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAllOAuthTokens data: ' + JSON.stringify(data));
    }
  });

```

## getAllOAuthTokens

```TypeScript
getAllOAuthTokens(name: string, owner: string): Promise<Array<OAuthTokenInfo>>
```

获取指定账号对调用方可见的所有授权令牌。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getAllAuthTokens](arkts-basicservices-appaccountmanager-i.md#getallauthtokens-2)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAllAuthTokens(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;OAuthTokenInfo&gt;&gt; | Promise对象，返回授权令牌数组。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAllOAuthTokens('LiSi', 'com.example.accountjsdemo').then((
  data: appAccount.OAuthTokenInfo[]) => {
  console.info('getAllOAuthTokens data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`getAllOAuthTokens err: code is ${err.code}, message is ${err.message}`);
});

```

## getAssociatedData

```TypeScript
getAssociatedData(name: string, key: string, callback: AsyncCallback<string>): void
```

根据指定键名获取特定应用账号的关联数据。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getCustomData](arkts-basicservices-appaccountmanager-i.md#getcustomdata-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getCustomData(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| key | string | 是 | 关联数据的键名。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取成功时，err为null，data为关联数据的取值；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAssociatedData('ZhangSan', 'k001', (err: BusinessError, result: string) => { 
  if (err) {
    console.error(`getAssociatedData err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getAssociatedData result: ' + result);
  }
});

```

## getAssociatedData

```TypeScript
getAssociatedData(name: string, key: string): Promise<string>
```

获取与此应用程序账号关联的数据。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [getCustomData](arkts-basicservices-appaccountmanager-i.md#getcustomdata-2)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getCustomData(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| key | string | 是 | 关联数据的键名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回关联数据的取值。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAssociatedData('ZhangSan', 'k001').then((data: string) => { 
  console.info('getAssociatedData: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getAssociatedData err: code is ${err.code}, message is ${err.message}`);
});

```

## getAuthCallback

```TypeScript
getAuthCallback(sessionId: string, callback: AsyncCallback<AuthCallback>): void
```

获取鉴权会话的认证器回调对象。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 鉴权会话的标识。 |
| callback | AsyncCallback&lt;AuthCallback&gt; | 是 | 回调函数。当获取成功时，err为null，data为鉴权会话的认证器回调对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid sessionId. |
| [12300108](../../apis-basic-services-kit/errorcode-account.md#12300108-认证会话不存在) | Session not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, param: AbilityConstant.LaunchParam) { // ability 生命周期函数
    let sessionId: string = want.parameters![appAccount.Constants.KEY_SESSION_ID] as string;
    try {
      appAccountManager.getAuthCallback(sessionId, (err: BusinessError, callback: appAccount.AuthCallback) => {
        if (err != null) {
          console.error(`getAuthCallback err: code is ${err.code}, message is ${err.message}`);
          return;
        }
        let result: appAccount.AuthResult = {
          account: {
            name: 'Lisi',
            owner: 'com.example.accountjsdemo',
          },
          tokenInfo: {
            token: 'xxxxxx',
            authType: 'getSocialData'
          }
        }; 
        callback.onResult(0, result);
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`getAuthCallback exception: code is ${err.code}, message is ${err.message}`);
    }
  }
}

```

## getAuthCallback

```TypeScript
getAuthCallback(sessionId: string): Promise<AuthCallback>
```

获取鉴权会话的认证器回调对象。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 鉴权会话的标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AuthCallback&gt; | Promise对象，返回鉴权会话的认证器回调对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid sessionId. |
| [12300108](../../apis-basic-services-kit/errorcode-account.md#12300108-认证会话不存在) | Session not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, param: AbilityConstant.LaunchParam) { // ability 生命周期函数
    let sessionId: string = want.parameters![appAccount.Constants.KEY_SESSION_ID] as string;
    try {
      appAccountManager.getAuthCallback(sessionId).then((callback: appAccount.AuthCallback) => {
      let result: appAccount.AuthResult = {
        account: {
          name: 'Lisi',
          owner: 'com.example.accountjsdemo',
        },
        tokenInfo: {
          token: 'xxxxxx',
          authType: 'getSocialData'
        }
      };
      callback.onResult(0, result);
      }).catch((err: BusinessError) => {
        console.error(`getAuthCallback err: code is ${err.code}, message is ${err.message}`);
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`getAuthCallback exception: code is ${err.code}, message is ${err.message}`);
    }
  }
}

```

## getAuthList

```TypeScript
getAuthList(name: string, authType: string, callback: AsyncCallback<Array<string>>): void
```

获取指定应用账号的特定鉴权类型的授权列表，即被授权的包名数组（令牌的授权列表通过
[setAuthTokenVisibility](arkts-basicservices-appaccountmanager-i.md#setauthtokenvisibility-1)
来设置）。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。当获取成功时，err为null，data为被授权的包名数组；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or authType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300107](../../apis-basic-services-kit/errorcode-account.md#12300107-认证类型不存在) | AuthType not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAuthList('LiSi', 'getSocialData', (err: BusinessError, authList: string[]) => {
    if (err) {
      console.error(`getAuthList failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAuthList successfully, authList: ' + authList);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthList exception: code is ${err.code}, message is ${err.message}`);
}

```

## getAuthList

```TypeScript
getAuthList(name: string, authType: string): Promise<Array<string>>
```

获取指定应用账号的特定鉴权类型的授权列表，即被授权的包名数组（令牌的授权列表通过
[setAuthTokenVisibility](arkts-basicservices-appaccountmanager-i.md#setauthtokenvisibility-1)
来设置）。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回被授权的包名数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or authType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300107](../../apis-basic-services-kit/errorcode-account.md#12300107-认证类型不存在) | AuthType not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAuthList('LiSi', 'getSocialData').then((authList: string[]) => {
    console.info('getAuthList successfully, authList: ' + authList);
  }).catch((err: BusinessError) => {
    console.error(`getAuthList failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthList exception: code is ${err.code}, message is ${err.message}`);
}

```

## getAuthToken

```TypeScript
getAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback<string>): void
```

获取指定应用账号的特定鉴权类型的授权令牌。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取成功时，err为null，data为授权令牌值；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, owner or authType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300107](../../apis-basic-services-kit/errorcode-account.md#12300107-认证类型不存在) | AuthType not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData',
    (err: BusinessError, token: string) => {
      if (err) {
        console.error(`getAuthToken failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getAuthToken successfully, token: ' + token);
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthToken exception: code is ${err.code}, message is ${err.message}`);
}

```

## getAuthToken

```TypeScript
getAuthToken(name: string, owner: string, authType: string): Promise<string>
```

获取指定应用账号的特定鉴权类型的授权令牌。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回授权令牌。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, owner or authType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300107](../../apis-basic-services-kit/errorcode-account.md#12300107-认证类型不存在) | AuthType not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData').then((token: string) => {
    console.info('getAuthToken successfully, token: ' + token);
  }).catch((err: BusinessError) => {
    console.error(`getAuthToken failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthToken exception: code is ${err.code}, message is ${err.message}`);
}

```

## getAuthenticatorCallback

```TypeScript
getAuthenticatorCallback(sessionId: string, callback: AsyncCallback<AuthenticatorCallback>): void
```

获取鉴权会话的认证器回调。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getAuthCallback](arkts-basicservices-appaccountmanager-i.md#getauthcallback-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAuthCallback(sessionId:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 鉴权会话的标识。 |
| callback | AsyncCallback&lt;AuthenticatorCallback&gt; | 是 | 回调函数。当获取鉴权会话的认证器回调函数成功时，err为null，data为认证器回调函数；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, param: AbilityConstant.LaunchParam) { // ability 生命周期函数
    let sessionId: string = want.parameters![appAccount.Constants.KEY_SESSION_ID] as string;
    appAccountManager.getAuthenticatorCallback(sessionId,
        (err: BusinessError, callback: appAccount.AuthenticatorCallback) => {
        if (err.code != appAccount.ResultCode.SUCCESS) {
            console.error(`getAuthenticatorCallback err: code is ${err.code}, message is ${err.message}`);
            return;
        }
        callback.onResult(appAccount.ResultCode.SUCCESS, {
          name: 'LiSi',
          owner: 'com.example.accountjsdemo',
          authType: 'getSocialData',
          token: 'xxxxxx'
        });
      });
  }
}

```

## getAuthenticatorCallback

```TypeScript
getAuthenticatorCallback(sessionId: string): Promise<AuthenticatorCallback>
```

获取鉴权会话的认证器回调。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getAuthCallback](arkts-basicservices-appaccountmanager-i.md#getauthcallback-2)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAuthCallback(sessionId:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | string | 是 | 鉴权会话的标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AuthenticatorCallback&gt; | Promise对象，返回鉴权会话的认证器回调对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, param: AbilityConstant.LaunchParam) { // ability 生命周期函数
    let sessionId: string = want.parameters![appAccount.Constants.KEY_SESSION_ID] as string;
    appAccountManager.getAuthenticatorCallback(sessionId).then((
      callback: appAccount.AuthenticatorCallback) => {
      callback.onResult(appAccount.ResultCode.SUCCESS, {
        name: 'LiSi',
        owner: 'com.example.accountjsdemo',
        authType: 'getSocialData',
        token: 'xxxxxx'
      });
    }).catch((err: BusinessError) => {
      console.error(`getAuthenticatorCallback err: code is ${err.code}, message is ${err.message}`);
    });
  }
}

```

## getAuthenticatorInfo

```TypeScript
getAuthenticatorInfo(owner: string, callback: AsyncCallback<AuthenticatorInfo>): void
```

获取指定应用的认证器信息。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [queryAuthenticatorInfo](arkts-basicservices-appaccountmanager-i.md#queryauthenticatorinfo-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** queryAuthenticatorInfo(owner:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;AuthenticatorInfo&gt; | 是 | 回调函数。当获取成功时，err为null，data为认证器信息对象；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAuthenticatorInfo('com.example.accountjsdemo',
  (err: BusinessError, data: appAccount.AuthenticatorInfo) => {
    if (err) {
      console.error(`getAuthenticatorInfo err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAuthenticatorInfo data: ' + JSON.stringify(data));
    }
  });

```

## getAuthenticatorInfo

```TypeScript
getAuthenticatorInfo(owner: string): Promise<AuthenticatorInfo>
```

获取指定应用的认证器信息。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [queryAuthenticatorInfo](arkts-basicservices-appaccountmanager-i.md#queryauthenticatorinfo-2)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** queryAuthenticatorInfo(owner:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AuthenticatorInfo&gt; | Promise对象，返回指定应用的认证器信息对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAuthenticatorInfo('com.example.accountjsdemo').then((
  data: appAccount.AuthenticatorInfo) => { 
  console.info('getAuthenticatorInfo: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`getAuthenticatorInfo err: code is ${err.code}, message is ${err.message}`);
});

```

## getCredential

```TypeScript
getCredential(name: string, credentialType: string, callback: AsyncCallback<string>): void
```

获取指定应用账号的凭据。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| credentialType | string | 是 | 凭据类型。自定义的类型，最大长度为1024个字符。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取凭据成功时，err为null，data为指定应用账号的凭据；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or credentialType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | Credential not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getCredential('ZhangSan', 'PIN_SIX', (err: BusinessError, result: string) => {
    if (err) {
      console.error(`getCredential failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getCredential successfully, result: ' + result);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCredential err: code is ${err.code}, message is ${err.message}`);
}

```

## getCredential

```TypeScript
getCredential(name: string, credentialType: string): Promise<string>
```

获取指定应用账号的凭据。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| credentialType | string | 是 | 凭据类型。自定义的类型，最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回指定应用账号的凭据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or credentialType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | Credential not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getCredential('ZhangSan', 'PIN_SIX').then((credential: string) => {
    console.info('getCredential successfully, credential: ' + credential);
  }).catch((err: BusinessError) => {
    console.error(`getCredential failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCredential exception: code is ${err.code}, message is ${err.message}`);
}

```

## getCustomData

```TypeScript
getCustomData(name: string, key: string, callback: AsyncCallback<string>): void
```

根据指定键名获取特定应用账号的自定义数据。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| key | string | 是 | 自定义数据的键名。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取成功时，err为null，data为自定义数据的取值；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or key. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12400002](../../apis-basic-services-kit/errorcode-account.md#12400002-自定义数据不存在) | Custom data not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getCustomData('ZhangSan', 'age', (err: BusinessError, data: string) => {
    if (err) {
      console.error('getCustomData failed, error: ' + err);
    } else {
      console.info('getCustomData successfully, data: ' + data);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCustomData exception: code is ${err.code}, message is ${err.message}`);
}

```

## getCustomData

```TypeScript
getCustomData(name: string, key: string): Promise<string>
```

根据指定键名获取特定应用账号的自定义数据。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| key | string | 是 | 自定义数据的键名。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回自定义数据的取值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or key. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12400002](../../apis-basic-services-kit/errorcode-account.md#12400002-自定义数据不存在) | Custom data not found |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getCustomData('ZhangSan', 'age').then((data: string) => {
    console.info('getCustomData successfully, data: ' + data);
  }).catch((err: BusinessError) => {
    console.error(`getCustomData failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCustomData exception: code is ${err.code}, message is ${err.message}`);
}

```

## getCustomDataSync

```TypeScript
getCustomDataSync(name: string, key: string): string
```

根据指定键名获取特定应用账号的自定义数据。使用同步方式返回结果。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| key | string | 是 | 自定义数据的键名。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 自定义数据的取值，默认为空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or key. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12400002](../../apis-basic-services-kit/errorcode-account.md#12400002-自定义数据不存在) | Custom data not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let value = appAccountManager.getCustomDataSync('ZhangSan', 'age');
  console.info('getCustomDataSync successfully, value: ' + value);
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCustomDataSync failed, code is ${err.code}, message is ${err.message}`);
}

```

## getOAuthList

```TypeScript
getOAuthList(name: string, authType: string, callback: AsyncCallback<Array<string>>): void
```

获取指定应用账号的特定鉴权类型的授权列表，即被授权的包名数组（令牌的授权列表通过
[setOAuthTokenVisibility](arkts-basicservices-appaccountmanager-i.md#setoauthtokenvisibility-1)
来设置）。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getAuthList](arkts-basicservices-appaccountmanager-i.md#getauthlist-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAuthList(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。当获取成功时，err为null，data为被授权的包名数组；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getOAuthList('LiSi', 'getSocialData', (err: BusinessError, data: string[]) => {
  if (err) {
    console.error(`getOAuthList err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getOAuthList data: ' + JSON.stringify(data));
  }
});

```

## getOAuthList

```TypeScript
getOAuthList(name: string, authType: string): Promise<Array<string>>
```

获取指定应用账号的特定鉴权类型的授权列表，即被授权的包名数组（令牌的授权列表通过
[setOAuthTokenVisibility](arkts-basicservices-appaccountmanager-i.md#setoauthtokenvisibility-1)
来设置）。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getAuthList](arkts-basicservices-appaccountmanager-i.md#getauthlist-2)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAuthList(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回被授权的包名数组。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getOAuthList('LiSi', 'getSocialData').then((data: string[]) => {
  console.info('getOAuthList data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`getOAuthList err: code is ${err.code}, message is ${err.message}`);
});

```

## getOAuthToken

```TypeScript
getOAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback<string>): void
```

获取指定应用账号的特定鉴权类型的授权令牌。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getAuthToken](arkts-basicservices-appaccountmanager-i.md#getauthtoken-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAuthToken(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取成功时，err为null，data为授权令牌值；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData',
  (err: BusinessError, data: string) => {
    if (err) {
      console.error(`getOAuthToken err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOAuthToken token: ' + data);
    }
  });

```

## getOAuthToken

```TypeScript
getOAuthToken(name: string, owner: string, authType: string): Promise<string>
```

获取指定应用账号的特定鉴权类型的授权令牌。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [getAuthToken](arkts-basicservices-appaccountmanager-i.md#getauthtoken-2)替
> 代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAuthToken(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回授权令牌。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData').then((data: string) => {
  console.info('getOAuthToken token: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getOAuthToken err: code is ${err.code}, message is ${err.message}`);
});

```

## off('change')

```TypeScript
off(type: 'change', callback?: Callback<Array<AppAccountInfo>>): void
```

取消订阅账号信息变更事件。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [off('accountChange')](arkts-basicservices-appaccountmanager-i.md#off-2)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** off(type:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 事件回调类型，支持的事件为'change'，当账号所有者更新账号信息时，触发该事件。 |
| callback | Callback&lt;Array&lt;AppAccountInfo&gt;&gt; | 否 | 需要注销的回调函数，默认为空，表示取消该类型事件的所有回调。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function changeOnCallback(data: appAccount.AppAccountInfo[]): void {
  console.info('receive change data: ' + JSON.stringify(data));
  appAccountManager.off('change', () => {
    console.info('off finish');
  })
}

try {
  appAccountManager.on('change', ['com.example.actsaccounttest'], changeOnCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`on accountOnOffDemo err: code is ${err.code}, message is ${err.message}`);
}

```

## off('accountChange')

```TypeScript
off(type: 'accountChange', callback?: Callback<Array<AppAccountInfo>>): void
```

取消订阅账号信息变更事件。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'accountChange' | 是 | 事件回调类型，支持的事件为'accountChange'，当账号所有者更新账号信息时，触发该事件。 |
| callback | Callback&lt;Array&lt;AppAccountInfo&gt;&gt; | 否 | 需要注销的回调函数，默认为空，表示取消该类型事件所有的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function changeOnCallback(data: appAccount.AppAccountInfo[]): void {
  console.info('receive change data:' + JSON.stringify(data));
}

try {
  appAccountManager.on('accountChange', ['com.example.actsaccounttest'], changeOnCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`on accountChange failed, code is ${err.code}, message is ${err.message}`);
}
try {
  appAccountManager.off('accountChange', changeOnCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`off accountChange failed, code is ${err.code}, message is ${err.message}`);
}

```

## on('change')

```TypeScript
on(type: 'change', owners: Array<string>, callback: Callback<Array<AppAccountInfo>>): void
```

订阅指定应用的账号信息变更事件。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [on('accountChange')](arkts-basicservices-appaccountmanager-i.md#on-2)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** on(type:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 事件回调类型，支持的事件为'change'，当账号所有者更新账号信息时，触发该事件。 |
| owners | Array&lt;string&gt; | 是 | 应用账号所有者的包名列表。 |
| callback | Callback&lt;Array&lt;AppAccountInfo&gt;&gt; | 是 | 需要注册的回调函数，返回信息发生变更的应用账号列表。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function changeOnCallback(data: appAccount.AppAccountInfo[]): void {
  console.info('receive change data:' + JSON.stringify(data));
}

try {
  appAccountManager.on('change', ['com.example.actsaccounttest'], changeOnCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`on accountOnOffDemo code is ${err.code}, message is ${err.message}`);
}

```

## on('accountChange')

```TypeScript
on(type: 'accountChange', owners: Array<string>, callback: Callback<Array<AppAccountInfo>>): void
```

订阅指定应用的账号信息变更事件。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'accountChange' | 是 | 事件回调类型，支持的事件为'accountChange'，当目标应用更新账号信息时，触发该事件。 |
| owners | Array&lt;string&gt; | 是 | 应用账号所有者的包名列表。 |
| callback | Callback&lt;Array&lt;AppAccountInfo&gt;&gt; | 是 | 需要注册的回调函数，返回信息为发生变更的应用账号列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid type or owners. |
| [12400001](../../apis-basic-services-kit/errorcode-account.md#12400001-应用不存在) | Application not found.<br>**适用版本：** 9 - 13 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function changeOnCallback(data: appAccount.AppAccountInfo[]): void {
  console.info('receive change data:' + JSON.stringify(data));
}

try {
  appAccountManager.on('accountChange', ['com.example.actsaccounttest'], changeOnCallback);
} catch (e) {
  const err = e as BusinessError;
  console.error(`on accountChange failed, code is ${err.code}, message is ${err.message}`);
}

```

## queryAuthenticatorInfo

```TypeScript
queryAuthenticatorInfo(owner: string, callback: AsyncCallback<AuthenticatorInfo>): void
```

获取指定应用的认证器信息。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;AuthenticatorInfo&gt; | 是 | 回调函数。当获取成功时，err为null，data为认证器信息对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid owner. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.queryAuthenticatorInfo('com.example.accountjsdemo',
    (err: BusinessError, info: appAccount.AuthenticatorInfo) => {
      if (err) {
        console.error(`queryAuthenticatorInfo failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('queryAuthenticatorInfo successfully, info: ' + JSON.stringify(info));
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryAuthenticatorInfo exception: code is ${err.code}, message is ${err.message}`);
}

```

## queryAuthenticatorInfo

```TypeScript
queryAuthenticatorInfo(owner: string): Promise<AuthenticatorInfo>
```

获取指定应用的认证器信息。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AuthenticatorInfo&gt; | Promise对象，返回指定应用的认证器信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid owner. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.queryAuthenticatorInfo('com.example.accountjsdemo').then((
    info: appAccount.AuthenticatorInfo) => { 
    console.info('queryAuthenticatorInfo successfully, info: ' + JSON.stringify(info));
  }).catch((err: BusinessError) => {
    console.error(`queryAuthenticatorInfo failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryAuthenticatorInfo exception: code is ${err.code}, message is ${err.message}`);
}

```

## removeAccount

```TypeScript
removeAccount(name: string, callback: AsyncCallback<void>): void
```

删除应用账号。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当删除成功时，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.removeAccount('ZhaoLiu', (err: BusinessError) => {
    if (err) {
      console.error(`removeAccount failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('removeAccount successfully');
    }
 });
} catch (e) {
  const err = e as BusinessError;
  console.error(`removeAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

## removeAccount

```TypeScript
removeAccount(name: string): Promise<void>
```

删除应用账号。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.removeAccount('Lisi').then(() => {
    console.info('removeAccount successfully');
  }).catch((err: BusinessError) => {
    console.error(`removeAccount failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`removeAccount exception: code is ${err.code}, message is ${err.message}`);
}

```

## selectAccountsByOptions

```TypeScript
selectAccountsByOptions(options: SelectAccountsOptions, callback: AsyncCallback<Array<AppAccountInfo>>): void
```

根据选项选择调用方可访问的账号列表。使用callback异步回调。如果选项中包含标签约束，则该方法依赖目标应用的认证器提供标签检查的能力。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | SelectAccountsOptions | 是 | 选择账号的选项。 |
| callback | AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt; | 是 | 回调函数。当根据选项选择请求方可访问的账号列表时，err为null，data为可访问的账号信息对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid options. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.SelectAccountsOptions = {
  allowedOwners: ['com.example.accountjsdemo'],
  requiredLabels: ['student']
};
try {
  appAccountManager.selectAccountsByOptions(options,
    (err: BusinessError, accountArr: appAccount.AppAccountInfo[]) => {
      if (err) {
        console.error(`selectAccountsByOptions failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('selectAccountsByOptions successfully, accountArr: ' + JSON.stringify(accountArr));
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`selectAccountsByOptions exception: code is ${err.code}, message is ${err.message}`);
}

```

## selectAccountsByOptions

```TypeScript
selectAccountsByOptions(options: SelectAccountsOptions): Promise<Array<AppAccountInfo>>
```

根据选项选择调用方可访问的账号列表。使用Promise异步回调。如果选项中包含标签约束，则该方法依赖目标应用的认证器提供标签检查的能力。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | SelectAccountsOptions | 是 | 选择账号的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AppAccountInfo&gt;&gt; | Promise对象，返回调用方可访问的账号列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid options. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.SelectAccountsOptions = {
  allowedOwners: ['com.example.accountjsdemo']
};
try {
  appAccountManager.selectAccountsByOptions(options).then((accountArr: appAccount.AppAccountInfo[]) => {
    console.info('selectAccountsByOptions successfully, accountArr: ' + JSON.stringify(accountArr));
  }).catch((err: BusinessError) => {
    console.error(`selectAccountsByOptions failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`selectAccountsByOptions exception: code is ${err.code}, message is ${err.message}`);
}

```

## setAccountCredential

```TypeScript
setAccountCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback<void>): void
```

设置指定应用账号的凭据。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，建议使用
> [setCredential](arkts-basicservices-appaccountmanager-i.md#setcredential-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setCredential(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| credentialType | string | 是 | 凭据类型。自定义的类型，最大长度为1024个字符。 |
| credential | string | 是 | 凭据取值。自定义的数据，最大长度为1024个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置此应用程序账号的凭据成功时，err为null，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAccountCredential('ZhangSan', 'credentialType001', 'credential001', (err: BusinessError) => { 
  if (err) {
    console.error(`setAccountCredential err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('setAccountCredential successful.');
  }
});

```

## setAccountCredential

```TypeScript
setAccountCredential(name: string, credentialType: string, credential: string): Promise<void>
```

设置指定应用账号的凭据。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，建议使用
> [setCredential](arkts-basicservices-appaccountmanager-i.md#setcredential-2)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setCredential(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| credentialType | string | 是 | 凭据类型。自定义的类型，最大长度为1024个字符。 |
| credential | string | 是 | 凭据取值。自定义的数据，最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAccountCredential('ZhangSan', 'credentialType001', 'credential001').then(() => { 
  console.info('setAccountCredential Success');
}).catch((err: BusinessError) => {
  console.error(`setAccountCredential err: code is ${err.code}, message is ${err.message}`);
});

```

## setAccountExtraInfo

```TypeScript
setAccountExtraInfo(name: string, extraInfo: string, callback: AsyncCallback<void>): void
```

设置指定应用账号的额外信息。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setCustomData](arkts-basicservices-appaccountmanager-i.md#setcustomdata-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setCustomData(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| extraInfo | string | 是 | 额外信息(能转换string类型的其它信息)，额外信息不能是应用账号的敏感信息（如应用账号密码、token等）。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置成功时，err为null，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAccountExtraInfo('ZhangSan', 'Tk002', (err: BusinessError) => { 
  if (err) {
    console.error(`setAccountExtraInfo err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('setAccountExtraInfo successful.');
  }
});

```

## setAccountExtraInfo

```TypeScript
setAccountExtraInfo(name: string, extraInfo: string): Promise<void>
```

设置此应用程序账号的额外信息。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setCustomData](arkts-basicservices-appaccountmanager-i.md#setcustomdata-2)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setCustomData(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| extraInfo | string | 是 | 额外信息(能转换string类型的其它信息)，额外信息不能是应用账号的敏感信息（如应用账号密码、token等）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAccountExtraInfo('ZhangSan', 'Tk002').then(() => { 
  console.info('setAccountExtraInfo Success');
}).catch((err: BusinessError) => {
  console.error(`setAccountExtraInfo err: code is ${err.code}, message is ${err.message}`);
});

```

## setAppAccess

```TypeScript
setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback<void>): void
```

设置指定应用对特定账号的访问权限。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| bundleName | string | 是 | 第三方应用的包名。最大长度为512个字符。 |
| isAccessible | boolean | 是 | 是否可访问。true表示允许访问，false表示禁止访问。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，如果设置成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or bundleName. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12400001](../../apis-basic-services-kit/errorcode-account.md#12400001-应用不存在) | Application not found.<br>**适用版本：** 9 - 13 |
| [12400005](../../apis-basic-services-kit/errorcode-account.md#12400005-授权列表已达上限) | The size of authorization list reaches the upper limit.<br>**适用版本：** 14+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAppAccess('ZhangSan', 'com.example.accountjsdemo', true, (err: BusinessError) => {
    if (err) {
      console.error(`setAppAccess failed: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setAppAccess successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAppAccess exception: code is ${err.code}, message is ${err.message}`);
}

```

## setAppAccess

```TypeScript
setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise<void>
```

设置指定应用对特定账号的数据访问权限。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| bundleName | string | 是 | 第三方应用的包名。最大长度为512个字符。 |
| isAccessible | boolean | 是 | 是否可访问。true表示允许访问，false表示禁止访问。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or bundleName. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12400001](../../apis-basic-services-kit/errorcode-account.md#12400001-应用不存在) | Application not found.<br>**适用版本：** 9 - 13 |
| [12400005](../../apis-basic-services-kit/errorcode-account.md#12400005-授权列表已达上限) | The size of authorization list reaches the upper limit.<br>**适用版本：** 14+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAppAccess('ZhangSan', 'com.example.accountjsdemo', true).then(() => {
    console.info('setAppAccess successfully');
  }).catch((err: BusinessError) => {
    console.error(`setAppAccess failed: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAppAccess exception: code is ${err.code}, message is ${err.message}`);
}

```

## setAppAccountSyncEnable

```TypeScript
setAppAccountSyncEnable(name: string, isEnable: boolean, callback: AsyncCallback<void>): void
```

开启或禁止指定应用账号的数据同步功能。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setDataSyncEnabled](arkts-basicservices-appaccountmanager-i.md#setdatasyncenabled-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setDataSyncEnabled(name:

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| isEnable | boolean | 是 | 是否开启数据同步。true表示开启数据同步，false表示关闭数据同步。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当开启或禁止成功时，err为null，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAppAccountSyncEnable('ZhangSan', true, (err: BusinessError) => {
  if (err) {
    console.error(`setAppAccountSyncEnable err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('setAppAccountSyncEnable successful.');
  }
});

```

## setAppAccountSyncEnable

```TypeScript
setAppAccountSyncEnable(name: string, isEnable: boolean): Promise<void>
```

开启或禁止指定应用账号的数据同步功能。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setDataSyncEnabled](arkts-basicservices-appaccountmanager-i.md#setdatasyncenabled-2)替代
> 。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setDataSyncEnabled(name:

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| isEnable | boolean | 是 | 是否开启数据同步。true表示开启数据同步，false表示关闭数据同步。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAppAccountSyncEnable('ZhangSan', true).then(() => { 
  console.info('setAppAccountSyncEnable Success');
}).catch((err: BusinessError) => {
  console.error(`setAppAccountSyncEnable err: code is ${err.code}, message is ${err.message}`);
});

```

## setAssociatedData

```TypeScript
setAssociatedData(name: string, key: string, value: string, callback: AsyncCallback<void>): void
```

设置指定应用账号的关联数据。使用callback异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setCustomData](arkts-basicservices-appaccountmanager-i.md#setcustomdata-1)
> 替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setCustomData(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| key | string | 是 | 关联数据的键名。 |
| value | string | 是 | 关联数据的取值。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置与此应用账号关联的数据成功时，err为null，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAssociatedData('ZhangSan', 'k001', 'v001', (err: BusinessError) => {
  if (err) {
    console.error(`setAssociatedData err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('setAssociatedData successful.');
  }
});

```

## setAssociatedData

```TypeScript
setAssociatedData(name: string, key: string, value: string): Promise<void>
```

设置指定应用账号的关联数据。使用Promise异步回调。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用
> [setCustomData](arkts-basicservices-appaccountmanager-i.md#setcustomdata-2)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setCustomData(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| key | string | 是 | 关联数据的键名。 |
| value | string | 是 | 关联数据的取值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAssociatedData('ZhangSan', 'k001', 'v001').then(() => { 
  console.info('setAssociatedData Success');
}).catch((err: BusinessError) => {
  console.error(`setAssociatedData err: code is ${err.code}, message is ${err.message}`);
});

```

## setAuthToken

```TypeScript
setAuthToken(name: string, authType: string, token: string, callback: AsyncCallback<void>): void
```

为指定应用账号设置特定鉴权类型的授权令牌。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| token | string | 是 | 授权令牌。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置成功时，err为null；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, authType or token. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12400004](../../apis-basic-services-kit/errorcode-account.md#12400004-令牌数量已达上限) | The number of tokens reaches the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAuthToken('LiSi', 'getSocialData', 'xxxx', (err: BusinessError) => {
    if (err) {
      console.error(`setAuthToken failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setAuthToken successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthToken exception: code is ${err.code}, message is ${err.message}`);
}

```

## setAuthToken

```TypeScript
setAuthToken(name: string, authType: string, token: string): Promise<void>
```

为指定应用账号设置特定鉴权类型的授权令牌。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| token | string | 是 | 授权令牌。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, authType or token. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12400004](../../apis-basic-services-kit/errorcode-account.md#12400004-令牌数量已达上限) | The number of tokens reaches the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAuthToken('LiSi', 'getSocialData', 'xxxx').then(() => {
    console.info('setAuthToken successfully');
  }).catch((err: BusinessError) => {
    console.error(`setAuthToken failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthToken exception: code is ${err.code}, message is ${err.message}`);
}

```

## setAuthTokenVisibility

```TypeScript
setAuthTokenVisibility(
      name: string,
      authType: string,
      bundleName: string,
      isVisible: boolean,
      callback: AsyncCallback<void>
    ): void
```

设置指定账号的特定鉴权类型的授权令牌对指定应用的可见性。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| bundleName | string | 是 | 被设置可见性的应用包名。最大长度为512个字符。 |
| isVisible | boolean | 是 | 是否可见。true表示可见，false表示不可见。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置成功时，err为null；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, authType or bundleName. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300107](../../apis-basic-services-kit/errorcode-account.md#12300107-认证类型不存在) | AuthType not found. |
| [12400001](../../apis-basic-services-kit/errorcode-account.md#12400001-应用不存在) | Application not found.<br>**适用版本：** 9 - 13 |
| [12400005](../../apis-basic-services-kit/errorcode-account.md#12400005-授权列表已达上限) | The size of authorization list reaches the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true,
    (err: BusinessError) => {
      if (err) {
        console.error(`setAuthTokenVisibility failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('setAuthTokenVisibility successfully');
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthTokenVisibility exception: code is ${err.code}, message is ${err.message}`);
}

```

## setAuthTokenVisibility

```TypeScript
setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise<void>
```

设置指定账号的特定鉴权类型的授权令牌对指定应用的可见性。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| bundleName | string | 是 | 被设置可见性的应用包名。最大长度为512个字符。 |
| isVisible | boolean | 是 | 是否可见。true表示可见，false表示不可见。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, authType or bundleName. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300107](../../apis-basic-services-kit/errorcode-account.md#12300107-认证类型不存在) | AuthType not found. |
| [12400001](../../apis-basic-services-kit/errorcode-account.md#12400001-应用不存在) | Application not found.<br>**适用版本：** 9 - 13 |
| [12400005](../../apis-basic-services-kit/errorcode-account.md#12400005-授权列表已达上限) | The size of authorization list reaches the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true).then(() => {
    console.info('setAuthTokenVisibility successfully');
  }).catch((err: BusinessError) => {
    console.error(`setAuthTokenVisibility failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthTokenVisibility exception: code is ${err.code}, message is ${err.message}`);
}

```

## setAuthenticatorProperties

```TypeScript
setAuthenticatorProperties(owner: string, callback: AuthCallback): void
```

设置指定应用的认证器属性。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 认证器的所有者的包名。 |
| callback | AuthCallback | 是 | 回调函数，返回设置属性的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid owner. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAuthenticatorProperties('com.example.accountjsdemo', {
    onResult: (resultCode: number, result?: appAccount.AuthResult) => {
      console.info('setAuthenticatorProperties onResult, resultCode: ' + JSON.stringify(resultCode));
      console.info('setAuthenticatorProperties onResult, result: ' + JSON.stringify(result));
    },
    onRequestRedirected: (request: Want) => {
      console.info('setAuthenticatorProperties onRequestRedirected, request: ' + JSON.stringify(request));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthenticatorProperties err: code is ${err.code}, message is ${err.message}`);
}

```

## setAuthenticatorProperties

```TypeScript
setAuthenticatorProperties(owner: string, options: SetPropertiesOptions, callback: AuthCallback): void
```

设置认证器属性。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 认证器的所有者的包名。 |
| options | SetPropertiesOptions | 是 | 设置属性的选项。 |
| callback | AuthCallback | 是 | 认证器回调，返回设置属性的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid owner or options. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.SetPropertiesOptions = {
  properties: { prop1: 'value1' }
};
try {
  appAccountManager.setAuthenticatorProperties('com.example.accountjsdemo', options, {
    onResult: (resultCode: number, result?: appAccount.AuthResult) => {
      console.info('setAuthenticatorProperties onResult, resultCode: ' + JSON.stringify(resultCode));
      console.info('setAuthenticatorProperties onResult, result: ' + JSON.stringify(result));
    },
    onRequestRedirected: (request: Want) => {
      console.info('setAuthenticatorProperties onRequestRedirected, request: ' + JSON.stringify(request));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthenticatorProperties err: code is ${err.code}, message is ${err.message}`);
} 

```

## setCredential

```TypeScript
setCredential(name: string, credentialType: string, credential: string,
                             callback: AsyncCallback<void>): void
```

设置指定应用账号的凭据。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| credentialType | string | 是 | 凭据类型。自定义的类型，最大长度为1024个字符。 |
| credential | string | 是 | 凭据取值。自定义的数据，最大长度为1024个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当凭据设置成功时，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, credentialType or credential. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setCredential('ZhangSan', 'PIN_SIX', 'xxxxxx', (err: BusinessError) => {
    if (err) {
      console.error(`setCredential failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setCredential successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setCredential exception: code is ${err.code}, message is ${err.message}`);
}

```

## setCredential

```TypeScript
setCredential(name: string, credentialType: string, credential: string): Promise<void>
```

设置指定应用账号的凭据。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| credentialType | string | 是 | 凭据类型。自定义的类型，最大长度为1024个字符。 |
| credential | string | 是 | 凭据取值。自定义的数据，最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, credentialType or credential. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setCredential('ZhangSan', 'PIN_SIX', 'xxxxxx').then(() => {
    console.info('setCredential successfully');
  }).catch((err: BusinessError) => {
    console.error(`setCredential failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setCredential exception: code is ${err.code}, message is ${err.message}`);
}

```

## setCustomData

```TypeScript
setCustomData(name: string, key: string, value: string, callback: AsyncCallback<void>): void
```

设置指定应用账号的自定义数据。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| key | string | 是 | 自定义数据的键名。最大长度为1024个字符。 |
| value | string | 是 | 自定义数据的取值。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置自定义数据成功时，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, key or value. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12400003](../../apis-basic-services-kit/errorcode-account.md#12400003-自定义数据的数量已达上限) | The number of custom data reaches the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setCustomData('ZhangSan', 'age', '12', (err: BusinessError) => {
    if (err) {
      console.error(`setCustomData failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setCustomData successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setCustomData exception: code is ${err.code}, message is ${err.message}`);
}

```

## setCustomData

```TypeScript
setCustomData(name: string, key: string, value: string): Promise<void>
```

设置指定应用账号的自定义数据。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| key | string | 是 | 自定义数据的键名。最大长度为1024个字符。 |
| value | string | 是 | 自定义数据的取值。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, key or value. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12400003](../../apis-basic-services-kit/errorcode-account.md#12400003-自定义数据的数量已达上限) | The number of custom data reaches the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setCustomData('ZhangSan', 'age', '12').then(() => {
    console.info('setCustomData successfully');
  }).catch((err: BusinessError) => {
    console.error(`setCustomData failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setCustomData exception: code is ${err.code}, message is ${err.message}`);
}

```

## setDataSyncEnabled

```TypeScript
setDataSyncEnabled(name: string, isEnabled: boolean, callback: AsyncCallback<void>): void
```

开启或禁止指定应用账号的数据同步功能。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| isEnabled | boolean | 是 | 是否开启数据同步。true表示开启数据同步，false表示关闭数据同步。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当开启或禁止成功时，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    appAccountManager.setDataSyncEnabled('ZhangSan', true, (err: BusinessError) => { 
        console.error(`setDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
    });
} catch (e) {
    const err = e as BusinessError;
    console.error(`setDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
}

```

## setDataSyncEnabled

```TypeScript
setDataSyncEnabled(name: string, isEnabled: boolean): Promise<void>
```

开启或禁止指定应用账号的数据同步功能。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| isEnabled | boolean | 是 | 是否开启数据同步。true表示开启数据同步，false表示关闭数据同步。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    appAccountManager.setDataSyncEnabled('ZhangSan', true).then(() => { 
        console.info('setDataSyncEnabled Success');
    }).catch((err: BusinessError) => {
        console.error(`setDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
    });
} catch (e) {
    const err = e as BusinessError;
    console.error(`setDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
}

```

## setOAuthToken

```TypeScript
setOAuthToken(name: string, authType: string, token: string, callback: AsyncCallback<void>): void
```

为指定应用账号设置特定鉴权类型的授权令牌。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [setAuthToken](arkts-basicservices-appaccountmanager-i.md#setauthtoken-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setAuthToken(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| token | string | 是 | 授权令牌。最大长度为1024个字符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置成功时，err为null；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setOAuthToken('LiSi', 'getSocialData', 'xxxx', (err: BusinessError) => {
  if (err) {
    console.error(`setOAuthToken err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('setOAuthToken successful.');
  }
});

```

## setOAuthToken

```TypeScript
setOAuthToken(name: string, authType: string, token: string): Promise<void>
```

为指定应用账号设置特定鉴权类型的授权令牌。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [setAuthToken](arkts-basicservices-appaccountmanager-i.md#setauthtoken-2)替
> 代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setAuthToken(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| token | string | 是 | 授权令牌。最大长度为1024个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setOAuthToken('LiSi', 'getSocialData', 'xxxx').then(() => {
  console.info('setOAuthToken successfully');
}).catch((err: BusinessError) => {
  console.error(`setOAuthToken err: code is ${err.code}, message is ${err.message}`);
});

```

## setOAuthTokenVisibility

```TypeScript
setOAuthTokenVisibility(
      name: string,
      authType: string,
      bundleName: string,
      isVisible: boolean,
      callback: AsyncCallback<void>
    ): void
```

设置指定账号的特定鉴权类型的授权令牌对指定应用的可见性。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [setAuthTokenVisibility](arkts-basicservices-appaccountmanager-i.md#setauthtokenvisibility-1)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setAuthTokenVisibility(

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| bundleName | string | 是 | 被设置可见性的应用包名。最大长度为512个字符。 |
| isVisible | boolean | 是 | 是否可见。true表示可见，false表示不可见。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置成功时，err为null；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true,
  (err: BusinessError) => {
    if (err) {
      console.error(`setOAuthTokenVisibility err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setOAuthTokenVisibility successful.');
    }
  });

```

## setOAuthTokenVisibility

```TypeScript
setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise<void>
```

设置指定账号的特定鉴权类型的授权令牌对指定应用的可见性。使用Promise异步回调。

> **说明：**
>
> 从API version 8开始支持，从API version 9开始废弃。建议使用
> [setAuthTokenVisibility](arkts-basicservices-appaccountmanager-i.md#setauthtokenvisibility-2)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setAuthTokenVisibility(name:

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 鉴权类型。自定义数据，最大长度为1024个字符。 |
| bundleName | string | 是 | 被设置可见性的应用包名。最大长度为512个字符。 |
| isVisible | boolean | 是 | 是否可见。true表示可见，false表示不可见。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true).then(() => {
  console.info('setOAuthTokenVisibility successfully');
}).catch((err: BusinessError) => {
  console.error(`setOAuthTokenVisibility err: code is ${err.code}, message is ${err.message}`);
});

```

## verifyCredential

```TypeScript
verifyCredential(name: string, owner: string, callback: AuthCallback): void
```

验证指定账号的凭据。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| callback | AuthCallback | 是 | 回调函数，返回验证结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name or owner. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.verifyCredential('zhangsan', 'com.example.accountjsdemo', {
    onResult: (resultCode: number, result?: appAccount.AuthResult) => {
      console.info('verifyCredential onResult, resultCode: ' + JSON.stringify(resultCode));
      console.info('verifyCredential onResult, result: ' + JSON.stringify(result));
    },
    onRequestRedirected: (request: Want) => {
      console.info('verifyCredential onRequestRedirected, request: ' + JSON.stringify(request));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`verifyCredential err: code is ${err.code}, message is ${err.message}`);
}

```

## verifyCredential

```TypeScript
verifyCredential(name: string, owner: string, options: VerifyCredentialOptions, callback: AuthCallback): void
```

验证用户凭据。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| owner | string | 是 | 应用账号所有者的包名。最大长度为1024个字符。 |
| options | VerifyCredentialOptions | 是 | 验证凭据的选项。 |
| callback | AuthCallback | 是 | 回调函数，返回验证结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid name, owner or options. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300010](../../apis-basic-services-kit/errorcode-account.md#12300010-账号服务忙碌) | Account service busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | Authenticator service not found. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | Authenticator service exception. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.VerifyCredentialOptions = {
  credentialType: 'pin',
  credential: '123456'
};
try {
  appAccountManager.verifyCredential('zhangsan', 'com.example.accountjsdemo', options, {
    onResult: (resultCode: number, result?: appAccount.AuthResult) => {
      console.info('verifyCredential onResult, resultCode: ' + JSON.stringify(resultCode));
      console.info('verifyCredential onResult, result: ' + JSON.stringify(result));
    },
    onRequestRedirected: (request: Want) => {
      console.info('verifyCredential onRequestRedirected, request: ' + JSON.stringify(request));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`verifyCredential err: code is ${err.code}, message is ${err.message}`);
}

```

