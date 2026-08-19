# Authenticator

认证器基类。

**起始版本：** 23

<!--Device-appAccount-class Authenticator--><!--Device-appAccount-class Authenticator-End-->

**系统能力：** SystemCapability.Account.AppAccount

## 导入模块

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## addAccountImplicitly

```TypeScript
addAccountImplicitly(
      authType: string,
      callerBundleName: string,
      options: { [key: string]: any },
      callback: AuthenticatorCallback
    ): void
```

根据指定的鉴权类型和可选项，隐式地添加应用账号。使用callback异步回调。 > **说明：** > > 从API version 8开始支持, 从API version 9开始废弃。建议使用[createAccountImplicitly](#createaccountimplicitly)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [createAccountImplicitly](#createaccountimplicitly)(options: CreateAccountImplicitlyOptions, callback: AuthCallback)

<!--Device-Authenticator-addAccountImplicitly(      authType: string,      callerBundleName: string,      options: { [key: string]: any },      callback: AuthenticatorCallback    ): void--><!--Device-Authenticator-addAccountImplicitly(      authType: string,      callerBundleName: string,      options: { [key: string]: any },      callback: AuthenticatorCallback    ): void-End-->

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | string | 是 | 应用账号的鉴权类型。自定义数据，最大长度为1024个字符。 |
| callerBundleName | string | 是 | 鉴权请求方的包名。 |
| options | { [key: string]: any } | 是 | 鉴权所需要的可选项。 |
| callback | [AuthenticatorCallback](arkts-basicservices-appaccount-authenticatorcallback-i.md) | 是 | 认证器回调，用于返回鉴权结果。 |

## auth

```TypeScript
auth(name: string, authType: string, options: Record<string, Object>, callback: AuthCallback): void
```

对应用账号进行鉴权以获取授权令牌。使用callback异步回调。

**起始版本：** 9

<!--Device-Authenticator-auth(name: string, authType: string, options: Record<string, Object>, callback: AuthCallback): void--><!--Device-Authenticator-auth(name: string, authType: string, options: Record<string, Object>, callback: AuthCallback): void-End-->

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 应用账号的鉴权类型。自定义数据，最大长度为1024个字符。 |
| options | Record&lt;string, Object&gt; | 是 | 鉴权所需要的可选项。 |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | 是 | 认证器回调，用于返回鉴权结果。 |

## auth

```TypeScript
auth(name: string, authType: string, options: Record<string, RecordData>, callback: AuthCallback): void
```

对应用账号进行鉴权以获取授权令牌。使用callback异步回调。

**起始版本：** 23

<!--Device-Authenticator-auth(name: string, authType: string, options: Record<string, RecordData>, callback: AuthCallback): void--><!--Device-Authenticator-auth(name: string, authType: string, options: Record<string, RecordData>, callback: AuthCallback): void-End-->

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 应用账号的鉴权类型。自定义数据，最大长度为1024个字符。 |
| options | Record&lt;string, [RecordData](arkts-basicservices-recorddata-t.md)&gt; | 是 | 鉴权所需要的可选项。 |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | 是 | 认证器回调，用于返回鉴权结果。 |

## authenticate

```TypeScript
authenticate(
      name: string,
      authType: string,
      callerBundleName: string,
      options: { [key: string]: any },
      callback: AuthenticatorCallback
    ): void
```

对应用账号进行鉴权，获取OAuth令牌。使用callback异步回调。 > **说明：** > > 从API version 8开始支持, 从API version 9开始废弃。建议使用[auth](#auth)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [auth](#auth)(name: string, authType: string, options: Record&lt;string, Object&gt;, callback: AuthCallback)

<!--Device-Authenticator-authenticate(      name: string,      authType: string,      callerBundleName: string,      options: { [key: string]: any },      callback: AuthenticatorCallback    ): void--><!--Device-Authenticator-authenticate(      name: string,      authType: string,      callerBundleName: string,      options: { [key: string]: any },      callback: AuthenticatorCallback    ): void-End-->

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| authType | string | 是 | 应用账号的鉴权类型。自定义数据，最大长度为1024个字符。 |
| callerBundleName | string | 是 | 鉴权请求方的包名。 |
| options | { [key: string]: any } | 是 | 鉴权所需要的可选项。 |
| callback | [AuthenticatorCallback](arkts-basicservices-appaccount-authenticatorcallback-i.md) | 是 | 认证器回调，用于返回鉴权结果。 |

## checkAccountLabels

```TypeScript
checkAccountLabels(name: string, labels: Array<string>, callback: AuthCallback): void
```

检查账号标签。使用callback异步回调。

**起始版本：** 23

<!--Device-Authenticator-checkAccountLabels(name: string, labels: Array<string>, callback: AuthCallback): void--><!--Device-Authenticator-checkAccountLabels(name: string, labels: Array<string>, callback: AuthCallback): void-End-->

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| labels | Array&lt;string&gt; | 是 | 标签数组。 |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | 是 | 认证器回调，用于返回鉴权结果。 |

**示例**

接口需组合使用，请查看[getRemoteObject](#getremoteobject)中的示例。

## checkAccountRemovable

```TypeScript
checkAccountRemovable(name: string, callback: AuthCallback): void
```

判断账号是否可以删除。使用callback异步回调。

**起始版本：** 23

<!--Device-Authenticator-checkAccountRemovable(name: string, callback: AuthCallback): void--><!--Device-Authenticator-checkAccountRemovable(name: string, callback: AuthCallback): void-End-->

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | 是 | 认证器回调，用于返回鉴权结果。 |

**示例**

接口需组合使用，请查看[getRemoteObject](#getremoteobject)中的示例。

## createAccountImplicitly

```TypeScript
createAccountImplicitly(options: CreateAccountImplicitlyOptions, callback: AuthCallback): void
```

根据指定的账号所有者隐式地创建应用账号。使用callback异步回调。

**起始版本：** 23

<!--Device-Authenticator-createAccountImplicitly(options: CreateAccountImplicitlyOptions, callback: AuthCallback): void--><!--Device-Authenticator-createAccountImplicitly(options: CreateAccountImplicitlyOptions, callback: AuthCallback): void-End-->

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CreateAccountImplicitlyOptions](arkts-basicservices-appaccount-createaccountimplicitlyoptions-i.md) | 是 | 隐式创建账号的选项。 |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | 是 | 认证器回调对象，用于返回创建结果。 |

## getRemoteObject

```TypeScript
getRemoteObject(): rpc.RemoteObject
```

获取认证器的远程对象，不可以重载实现。

**起始版本：** 23

<!--Device-Authenticator-getRemoteObject(): rpc.RemoteObject--><!--Device-Authenticator-getRemoteObject(): rpc.RemoteObject-End-->

**系统能力：** SystemCapability.Account.AppAccount

**返回值：**

| 类型 | 说明 |
| --- | --- |
| rpc.RemoteObject | 认证器Authenticator的远程对象。用于跨进程通信。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class MyAuthenticator extends appAccount.Authenticator {
  verifyCredential(name: string,
    options: appAccount.VerifyCredentialOptions, callback: appAccount.AuthCallback) {
    let want: Want = {
      bundleName: 'com.example.accountjsdemo',
      abilityName: 'com.example.accountjsdemo.VerifyAbility',
      parameters: {
        name: name
      }
    };
    callback.onRequestRedirected(want);
  }

  setProperties(options: appAccount.SetPropertiesOptions, callback: appAccount.AuthCallback) {
    let want: Want = {
      bundleName: 'com.example.accountjsdemo',
      abilityName: 'com.example.accountjsdemo.SetPropertiesAbility',
      parameters: {
        options: options
      }
    };
    callback.onRequestRedirected(want);
  }

  checkAccountLabels(name: string, labels: string[], callback: appAccount.AuthCallback) {
    callback.onResult(0);
  }

  checkAccountRemovable(name: string, callback: appAccount.AuthCallback) {
    callback.onResult(0);
  }
}

export default {
  onConnect(want: Want): rpc.RemoteObject { // serviceAbility 生命周期函数, 需要放在serviceAbility中
    let authenticator = new MyAuthenticator();
    return authenticator.getRemoteObject();
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';
import { RecordData } from '@ohos.base';

import appAccount from '@ohos.account.appAccount';

@Entry
@Component
struct ListDemo5 {
  build(){
  }
}

class MyAuthenticator extends appAccount.Authenticator {
  verifyCredential(name: string,
    options: appAccount.VerifyCredentialOptions, callback: appAccount.AuthCallback) {
    let dataName: Record<String, RecordData> = {"name": name };
    let want: Want = {
      bundleName: 'com.example.accountjsdemo',
      abilityName: 'com.example.accountjsdemo.VerifyAbility',
      parameters: dataName
    };
    callback.onResult(0);
  }

  setProperties(options: appAccount.SetPropertiesOptions, callback: appAccount.AuthCallback) {
    let dataOptions: Record<String, RecordData> = {"options": options }
    let want: Want = {
      bundleName: 'com.example.accountjsdemo',
      abilityName: 'com.example.accountjsdemo.SetPropertiesAbility',
      parameters: dataOptions
    };
    callback.onResult(0);
  }

  checkAccountLabels(name: string, labels: string[], callback: appAccount.AuthCallback) {

    let accountLabels: Record<string, Array<string>> = {
      'zhangsan': ['male', '30-40', 'level4'],
      'lisi': ['female']
    };
    let authResult: appAccount.AuthResult = {
      account: {
        name: name,
        owner: 'com.acts.accountauthenticator.static'
      },
      tokenInfo: undefined
    }
    if (name === 'notExistAccount') {
      callback.onResult(12300003);
      return;
    }
    if (labels.length == 0) {
      callback.onResult(0, authResult)
      return
    }
    let allLabels: Array<string> | undefined;
    try {
      allLabels = accountLabels[name];
    } catch (err) {
      console.info('[Authenticator] no labels');
      allLabels == undefined
    }
    if (allLabels == undefined || allLabels.length == 0) {
      callback.onResult(0, undefined);
      return;
    }
    for (let i = 0; i < labels.length; ++i) {
      if (allLabels.indexOf(labels[i]) == -1) {
        callback.onResult(0, undefined);
        return;
      }
    }
    callback.onResult(0, authResult)
  }

  checkAccountRemovable(name: string, callback: appAccount.AuthCallback) {
    let accountRemovability: Record<string, boolean> = {
      'zhangsan': false,
      'lisi': true
    };
    console.info('[Authenticator] name: ' + name);
    let isRemovable: Boolean | undefined = false;
    try {
      isRemovable = accountRemovability[name];
    } catch (err) {
      console.info('[Authenticator] error: ' + JSON.stringify(err));
    }
    let authResult: appAccount.AuthResult = {
      account: {
        name: name,
        owner: 'com.acts.accountauthenticator.static'
      },
      tokenInfo: undefined
    }
    if (isRemovable) {
      callback.onResult(0, authResult);
      return;
    }
    callback.onResult(0, undefined);
  }
}

export default class ServiceExtAbilitty {
  onConnect(want: Want) {
    let authenticator = new MyAuthenticator();
    return authenticator.getRemoteObject();
  }
}
```

## setProperties

```TypeScript
setProperties(options: SetPropertiesOptions, callback: AuthCallback): void
```

设置认证器属性。使用callback异步回调。

**起始版本：** 23

<!--Device-Authenticator-setProperties(options: SetPropertiesOptions, callback: AuthCallback): void--><!--Device-Authenticator-setProperties(options: SetPropertiesOptions, callback: AuthCallback): void-End-->

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SetPropertiesOptions](arkts-basicservices-appaccount-setpropertiesoptions-i.md) | 是 | 设置属性的可选项。 |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | 是 | 认证器回调，用于返回鉴权结果。 |

**示例**

接口需组合使用，请查看[getRemoteObject](#getremoteobject)中的示例。

## verifyCredential

```TypeScript
verifyCredential(name: string, options: VerifyCredentialOptions, callback: AuthCallback): void
```

验证应用账号的凭据。使用callback异步回调。

**起始版本：** 23

<!--Device-Authenticator-verifyCredential(name: string, options: VerifyCredentialOptions, callback: AuthCallback): void--><!--Device-Authenticator-verifyCredential(name: string, options: VerifyCredentialOptions, callback: AuthCallback): void-End-->

**系统能力：** SystemCapability.Account.AppAccount

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 应用账号的名称。最大长度为512个字符。 |
| options | [VerifyCredentialOptions](arkts-basicservices-appaccount-verifycredentialoptions-i.md) | 是 | 验证凭据的可选项。 |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | 是 | 认证器回调，用于返回鉴权结果。 |

**示例**

接口需组合使用，请查看[getRemoteObject](#getremoteobject)中的示例。

