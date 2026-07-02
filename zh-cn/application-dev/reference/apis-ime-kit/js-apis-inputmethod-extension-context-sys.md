# @ohos.InputMethodExtensionContext (InputMethodExtensionContext)(系统接口)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

InputMethodExtensionContext模块是InputMethodExtensionAbility的上下文环境，继承于ExtensionContext，提供InputMethodExtensionAbility具有的能力和接口（系统接口）。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 本模块接口仅可在Stage模型下使用。
> 本模块接口为系统接口。

## 导入模块

```ts
import { InputMethodExtensionContext } from '@kit.IMEKit';
```

## 使用说明

在使用InputMethodExtensionContext的功能前，需要通过InputMethodExtensionAbility子类实例获取。

```ts
import { InputMethodExtensionAbility, InputMethodExtensionContext } from '@kit.IMEKit';
import { Want } from '@kit.AbilityKit';

class InputMethodExtAbility extends InputMethodExtensionAbility {
  onCreate(want: Want): void {
    console.info('onCreate, want:' + want.abilityName);
  }
}
```

## InputMethodExtensionContext

InputMethodExtensionContext是InputMethodExtensionAbility的上下文环境，继承自ExtensionContext，用于操作输入法扩展相关的生命周期和状态。

### terminateSelf<sup>(deprecated)</sup>

terminateSelf(callback: AsyncCallback&lt;void&gt;): void

停止当前输入法扩展自身。仅支持在主线程调用。使用callback异步回调。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃，建议使用[destroy](./js-apis-inputmethod-extension-context.md#destroy9)替代。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当停止输入法扩展自身成功，err为undefined，否则为错误对象。 |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    this.context.terminateSelf((error: BusinessError) => {
      if (error.code) {
        console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
        return;
      }
      console.info('terminateSelf succeed');
    });
  }
}
```

### terminateSelf<sup>(deprecated)</sup>

terminateSelf(): Promise&lt;void&gt;

停止当前输入法扩展自身。仅支持在主线程调用。使用Promise异步回调。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃，建议使用[destroy](./js-apis-inputmethod-extension-context.md#destroy9)替代。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    this.context.terminateSelf().then(() => {
      console.info('terminateSelf succeed');
    }).catch((error: BusinessError) => {
      console.error(`terminateSelf failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```

### startAbilityWithAccount<sup>(deprecated)</sup>

startAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback&lt;void&gt;): void

启动指定账号的Ability。使用callback异步回调。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃。

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是 | 启动Ability的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当启动Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | The application does not have permission to call the interface.<br>适用版本：9+ |
| 202 | not system application.<br>适用版本：9+ |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>适用版本：9+ |
| 16000001 | The specified ability does not exist.<br>适用版本：9+ |
| 16000002 | Incorrect ability type.<br>适用版本：9+ |
| 16000004 | Cannot start an invisible component.<br>适用版本：9+ |
| 16000005 | The specified process does not have the permission.<br>适用版本：9+ |
| 16000006 | Cross-user operations are not allowed.<br>适用版本：9+ |
| 16000008 | The crowdtesting application expires.<br>适用版本：9+ |
| 16000009 | An ability cannot be started or stopped in Wukong mode.<br>适用版本：9+ |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.<br>适用版本：9+ |
| 16000011 | The context does not exist.<br>适用版本：9+ |
| 16000012 | The application is controlled.<br>适用版本：9+ |
| 16000013 | The application is controlled by EDM.<br>适用版本：9+ |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.<br>适用版本：9+ |
| 16000053 | The ability is not on the top of the UI.<br>适用版本：9+ |
| 16000055 | Installation-free timed out.<br>适用版本：9+ |
| 16200001 | The caller has been released.<br>适用版本：9+ |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let accountId = 100;
    this.context.startAbilityWithAccount(want, accountId, (error: BusinessError) => {
      if (error.code) {
        console.error(`startAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
        return;
      }
      console.info('startAbilityWithAccount succeed');
    });
  }
}
```

### startAbilityWithAccount<sup>(deprecated)</sup>

startAbilityWithAccount(want: Want, accountId: number): Promise&lt;void&gt;

启动指定账号的Ability。使用Promise异步回调。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃。

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是 | 启动Ability的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | The application does not have permission to call the interface.<br>适用版本：9+ |
| 202 | not system application.<br>适用版本：9+ |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>适用版本：9+ |
| 16000001 | The specified ability does not exist.<br>适用版本：9+ |
| 16000002 | Incorrect ability type.<br>适用版本：9+ |
| 16000004 | Cannot start an invisible component.<br>适用版本：9+ |
| 16000005 | The specified process does not have the permission.<br>适用版本：9+ |
| 16000006 | Cross-user operations are not allowed.<br>适用版本：9+ |
| 16000008 | The crowdtesting application expires.<br>适用版本：9+ |
| 16000009 | An ability cannot be started or stopped in Wukong mode.<br>适用版本：9+ |
| 16000010 | The call with the continuation and prepare continuation flag is forbidden.<br>适用版本：9+ |
| 16000011 | The context does not exist.<br>适用版本：9+ |
| 16000012 | The application is controlled.<br>适用版本：9+ |
| 16000013 | The application is controlled by EDM.<br>适用版本：9+ |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.<br>适用版本：9+ |
| 16000053 | The ability is not on the top of the UI.<br>适用版本：9+ |
| 16000055 | Installation-free timed out.<br>适用版本：9+ |
| 16200001 | The caller has been released.<br>适用版本：9+ |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let accountId = 100;
    this.context.startAbilityWithAccount(want, accountId).then(() => {
      console.info('startAbilityWithAccount succeed');
    }).catch((error: BusinessError) => {
      console.error(`startAbilityWithAccount failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```

### connectAbility<sup>(deprecated)</sup>

connectAbility(want: Want, options: ConnectOptions): number

将当前输入法扩展连接到一个ServiceExtensionAbility。仅支持在主线程调用。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃，建议使用[connectServiceExtensionAbility](#connectserviceextensionabilitydeprecated)替代。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是 | Want类型参数，传入需要启动的Ability的信息，如Ability名称、Bundle名称等。 |
| options | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、断开或连接失败后的信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 返回一个number，后续根据这个number去断开连接。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>适用版本：9+ |
| 16000001 | The specified ability does not exist.<br>适用版本：9+ |
| 16000005 | The specified process does not have the permission.<br>适用版本：9+ |
| 16000011 | The context does not exist.<br>适用版本：9+ |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.<br>适用版本：9+ |
| 16000002 | Incorrect ability type.<br>适用版本：10+ |
| 16000004 | Cannot start an invisible component.<br>适用版本：10+ |
| 16000006 | Cross-user operations are not allowed.<br>适用版本：10+ |
| 16000008 | The crowdtesting application expires.<br>适用版本：10+ |
| 16000053 | The ability is not on the top of the UI.<br>适用版本：10+ |
| 16000055 | Installation-free timed out.<br>适用版本：10+ |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('----------- onConnect -----------');
      },
      onDisconnect(elementName) {
        console.info('----------- onDisconnect -----------');
      },
      onFailed(code) {
        console.error('----------- onFailed -----------');
      }
    };
    let connection: number;

    try {
      connection = this.context.connectAbility(want, options);
    } catch (paramError) {
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

### connectAbilityWithAccount<sup>(deprecated)</sup>

connectAbilityWithAccount(want: Want, accountId: number): number

将当前输入法扩展连接到一个指定账号的ServiceExtensionAbility。仅支持在主线程调用。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃。

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是 | 启动Ability的Want信息。 |
| accountId | number | 是 | 系统账号的账号ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 返回Ability连接的结果code。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | The application does not have permission to call the interface.<br>适用版本：9+ |
| 202 | not system application.<br>适用版本：9+ |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>适用版本：9+ |
| 16000001 | The specified ability does not exist.<br>适用版本：9+ |
| 16000005 | The specified process does not have the permission.<br>适用版本：9+ |
| 16000011 | The context does not exist.<br>适用版本：9+ |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.<br>适用版本：9+ |
| 16000002 | Incorrect ability type.<br>适用版本：10+ |
| 16000004 | Cannot start an invisible component.<br>适用版本：10+ |
| 16000006 | Cross-user operations are not allowed.<br>适用版本：10+ |
| 16000008 | The crowdtesting application expires.<br>适用版本：10+ |
| 16000053 | The ability is not on the top of the UI.<br>适用版本：10+ |
| 16000055 | Installation-free timed out.<br>适用版本：10+ |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let accountId = 100;
    let connection: number;

    try {
      connection = this.context.connectAbilityWithAccount(want, accountId);
    } catch (paramError) {
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

### connectServiceExtensionAbility<sup>(deprecated)</sup>

connectServiceExtensionAbility(want: Want, options: ConnectOptions): number

将当前输入法扩展连接到一个ServiceExtensionAbility。仅支持在主线程调用。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是 | Want类型参数，传入需要启动的Ability的信息，如Ability名称、Bundle名称等。 |
| options | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、断开或连接失败后的信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 返回一个number，后续根据这个number去断开连接。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>适用版本：9+ |
| 16000001 | The specified ability does not exist.<br>适用版本：9+ |
| 16000005 | The specified process does not have the permission.<br>适用版本：9+ |
| 16000011 | The context does not exist.<br>适用版本：9+ |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.<br>适用版本：9+ |
| 16000002 | Incorrect ability type.<br>适用版本：10+ |
| 16000004 | Cannot start an invisible component.<br>适用版本：10+ |
| 16000006 | Cross-user operations are not allowed.<br>适用版本：10+ |
| 16000008 | The crowdtesting application expires.<br>适用版本：10+ |
| 16000053 | The ability is not on the top of the UI.<br>适用版本：10+ |
| 16000055 | Installation-free timed out.<br>适用版本：10+ |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MyAbility'
    };
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('----------- onConnect -----------');
      },
      onDisconnect(elementName) {
        console.info('----------- onDisconnect -----------');
      },
      onFailed(code) {
        console.error('----------- onFailed -----------');
      }
    };
    let connection: number;

    try {
      connection = this.context.connectServiceExtensionAbility(want, options);
    } catch (paramError) {
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

### disconnectAbility<sup>(deprecated)</sup>

disconnectAbility(connection: number, callback: AsyncCallback&lt;void&gt;): void

将一个Ability与绑定的服务类型的Ability解绑，断开连接之后需要将连接成功时返回的remote对象置空。仅支持在主线程调用。使用callback异步回调。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃，建议使用[disconnectServiceExtensionAbility](#disconnectserviceextensionabilitydeprecated)替代。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| connection | number | 是 | 在connectServiceExtensionAbility中返回的number。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当Ability与绑定服务类型的Ability解绑成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>适用版本：9+ |
| 16000011 | The context does not exist.<br>适用版本：9+ |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.<br>适用版本：9+ |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject | null;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let connection = 1;
    try {
      this.context.disconnectAbility(connection, (error: BusinessError) => {
        commRemote = null;
        if (error.code) {
          console.error(`disconnectAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        console.info('disconnectAbility succeed');
      });
    } catch (paramError) {
      commRemote = null;
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

### disconnectAbility<sup>(deprecated)</sup>

disconnectAbility(connection: number): Promise&lt;void&gt;

将一个Ability与绑定的服务类型的Ability解绑，断开连接之后需要将连接成功时返回的remote对象置空。仅支持在主线程调用。使用Promise异步回调。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃，建议使用[disconnectServiceExtensionAbility](#disconnectserviceextensionabilitydeprecated-1)替代。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| connection | number | 是 | 在connectServiceExtensionAbility中返回的number。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>适用版本：9+ |
| 16000011 | The context does not exist.<br>适用版本：9+ |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.<br>适用版本：9+ |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject | null;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let connection = 1;
    this.context.disconnectAbility(connection).then(() => {
      commRemote = null;
      console.info('disconnectAbility succeed');
    }).catch((error: BusinessError) => {
      commRemote = null;
      console.error(`disconnectAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```

### disconnectServiceExtensionAbility<sup>(deprecated)</sup>

disconnectServiceExtensionAbility(connection: number, callback: AsyncCallback&lt;void&gt;): void

将一个Ability与绑定的服务类型的Ability解绑，断开连接之后需要将连接成功时返回的remote对象置空。仅支持在主线程调用。使用callback异步回调。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| connection | number | 是 | 在connectServiceExtensionAbility中返回的number。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当Ability与绑定服务类型的Ability解绑成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>适用版本：9+ |
| 16000011 | The context does not exist.<br>适用版本：9+ |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.<br>适用版本：9+ |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject | null;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let connection = 1;
    try {
      this.context.disconnectServiceExtensionAbility(connection, (error: BusinessError) => {
        commRemote = null;
        if (error.code) {
          console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
          return;
        }
        console.info('disconnectServiceExtensionAbility succeed');
      });
    } catch (paramError) {
      commRemote = null;
      console.error(`error.code: ${(paramError as BusinessError).code}, error.message: ${(paramError as BusinessError).message}`);
    }
  }
}
```

### disconnectServiceExtensionAbility<sup>(deprecated)</sup>

disconnectServiceExtensionAbility(connection: number): Promise&lt;void&gt;

将一个Ability与绑定的服务类型的Ability解绑，断开连接之后需要将连接成功时返回的remote对象置空。仅支持在主线程调用。使用Promise异步回调。

> **说明：**
>
> 从API version 9 开始支持，从API version 10 开始废弃。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| connection | number | 是 | 在connectServiceExtensionAbility中返回的number。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](../apis-ability-kit/errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.<br>适用版本：9+ |
| 16000011 | The context does not exist.<br>适用版本：9+ |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module.<br>适用版本：9+ |

**示例：**

```ts
import { InputMethodExtensionAbility } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let commRemote: rpc.IRemoteObject | null;

class MyInputMethodExtensionAbility extends InputMethodExtensionAbility {
  onCreate() {
    let connection = 1;
    this.context.disconnectServiceExtensionAbility(connection).then(() => {
      commRemote = null;
      console.info('disconnectServiceExtensionAbility succeed');
    }).catch((error: BusinessError) => {
      commRemote = null;
      console.error(`disconnectServiceExtensionAbility failed, error.code: ${error.code}, error.message: ${error.message}`);
    });
  }
}
```