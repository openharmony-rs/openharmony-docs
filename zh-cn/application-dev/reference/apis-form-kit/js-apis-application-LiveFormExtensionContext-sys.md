# LiveFormExtensionContext (系统接口)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

LiveFormExtensionContext是[LiveFormExtensionAbility](./js-apis-app-form-LiveFormExtensionAbility.md)的上下文，继承自[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)。

> **说明：**
>
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公共接口参见[LiveFormExtensionContext](./js-apis-application-LiveFormExtensionContext.md)。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块
```ts
import { common } from '@kit.AbilityKit';
```

>  **说明：**
>
> - 在API version 22以前，需要通过`import LiveFormExtensionContext from 'application/LiveFormExtensionContext'; `导入LiveFormExtensionContext。该导入方式在DevEco Studio中标红，但不影响编译运行，可以直接使用LiveFormExtensionContext。
>
> - 在API version 22及以后，支持通过`import { common } from '@kit.AbilityKit'; `导入LiveFormExtensionContext，并通过common.LiveFormExtensionContext的方式使用。

## 使用说明
LiveFormExtensionContext主要用于查询所属LiveFormExtensionAbility的信息，提供访问特定LiveFormExtensionAbility资源的能力。
```ts
import { LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession } from '@kit.AbilityKit';

export default class MyLiveFormExtensionAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('context', this.context);
    session.loadContent('pages/MyLiveFormPage', storage);
    session.sendData({ ['isFormReady']: true });
    console.info("current language is: ", this.context.config.language);
  }
};
```

## LiveFormExtensionContext

LiveFormExtensionContext是LiveFormExtensionAbility的上下文环境。

### connectServiceExtensionAbility<sup>21+<sup>

connectServiceExtensionAbility(want: Want, connection: ConnectOptions): number

将当前LiveFormExtensionAbility客户端连接到一个[ServiceExtensionAbility](../../application-models/serviceextensionability-sys.md)服务端。

调用该接口前，必须实现[ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md)接口。

通过本接口连接成功后，LiveFormExtensionAbility可以通过ConnectOptions返回的[IRemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject)与ServiceExtensionAbility进行通信，以使用ServiceExtensionAbility对外提供的能力。

ServiceExtensionAbility是一类特殊的[ExtensionAbility](../../application-models/extensionability-overview.md)组件，这类组件由系统提供，通常用于提供指定场景后台服务能力，不支持开发者自定义。

ServiceExtensionAbility提供后台服务扩展能力，支持后台运行并对外提供相应能力。三方应用可以连接该ExtensionAbility，并进行通信。
通过本接口连接成功后，会启动ServiceExtensionAbility组件，具体请参考[组件启动规则](../../application-models/component-startup-rules.md)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是 | 连接ServiceExtensionAbility的Want信息，包括Ability名称、Bundle名称等。 |
| connection | [ConnectOptions](../apis-ability-kit/js-apis-inner-ability-connectOptions.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息，连接成功会返回[IRemoteObject](../apis-ipc-kit/js-apis-rpc.md#iremoteobject)实例。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 返回连接id，客户端可以通过[disconnectServiceExtensionAbility](#disconnectserviceextensionability21)传入该连接id来断开连接。 |

**错误码：**

以下错误码的详细介绍请参见[卡片错误码](errorcode-form.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed, application which is not a system application uses system API. |
| 16500100 | Failed to obtain the configuration information.              |
| 16501000 | An internal functional error occurred.                       |
| 16501011 | The form can not support this operation.                      |

**示例：**

```ts
// MyLiveFormExtensionAbility.ets
import { LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession } from '@kit.AbilityKit';

export default class MyLiveFormExtensionAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    // 1.将LiveFormExtensionContext传给互动卡片的页面组件
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('context', this.context);
    session.loadContent('pages/MyLiveFormPage', storage);
    session.sendData({['isFormReady']: true});
  }
};
```
```ts
// pages/MyLiveFormPage.ets
import { Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

@Entry
@Component
struct MyLiveFormPage {
  private storageForMyLiveFormPage: LocalStorage | undefined = undefined;
  private liveFormContext: common.LiveFormExtensionContext | undefined = undefined;

  aboutToAppear(): void {
    // 2.获取LiveFormExtensionContext
    this.storageForMyLiveFormPage = this.getUIContext().getSharedLocalStorage();
    this.liveFormContext = this.storageForMyLiveFormPage?.get<common.LiveFormExtensionContext>('context');
    if (!this.liveFormContext) {
        console.info('MyLiveFormPage liveFormContext is empty');
        return;
      }
    this.connectServiceExtensionAbility();
  }

  private connectServiceExtensionAbility(): void {
    // 请开发者替换为实际want
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let commRemote: rpc.IRemoteObject;
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('onConnect...');
      },
      onDisconnect(elementName) {
        console.info('onDisconnect...');
      },
      onFailed(code) {
        console.error(`onFailed, err code: ${code}.`);
      }
    };
    let connection: number | undefined;
    try {
      connection = this.liveFormContext?.connectServiceExtensionAbility(want, options);
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }

  build() {
    Stack() {
      // 请开发者替换为实际的页面
    }
  }
}
```

### disconnectServiceExtensionAbility<sup>21+<sup>

disconnectServiceExtensionAbility(connectionId: number): Promise\<void>

断开与[ServiceExtensionAbility](../../application-models/serviceextensionability-sys.md)的连接，断开连接之后开发者需要将连接成功时返回的IRemoteObject对象置空。使用Promise异步回调。

ServiceExtensionAbility是一类特殊的[ExtensionAbility](../../application-models/extensionability-overview.md)组件，这类组件由系统提供，通常用于提供指定场景后台服务能力，不支持开发者自定义。ServiceExtensionAbility提供后台服务扩展能力，支持后台运行并对外提供相应能力。三方应用可以连接该ExtensionAbility，并进行通信。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| connectionId | number | 是 | 连接的ServiceExtensionAbility的连接id，即[connectServiceExtensionAbility](#connectserviceextensionability21)返回的connectionId。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[卡片错误码](errorcode-form.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed, application which is not a system application uses system API.|
| 16501000 | An internal functional error occurred.                       |
| 16501011 | The form can not support this operation.                      |

**示例：**
```ts
// MyLiveFormExtensionAbility.ets
import { LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession } from '@kit.AbilityKit';

export default class MyLiveFormExtensionAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    // 1.将LiveFormExtensionContext传给互动卡片的页面组件
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('context', this.context);
    session.loadContent('pages/MyLiveFormPage', storage);
    session.sendData({['isFormReady']: true});
  }
};
```
```ts
// pages/MyLiveFormPage.ets
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

@Entry
@Component
struct MyLiveFormPage {
  private storageForMyLiveFormPage: LocalStorage | undefined = undefined;
  private liveFormContext: common.LiveFormExtensionContext | undefined = undefined;

  aboutToAppear(): void {
    // 2.获取LiveFormExtensionContext
    this.storageForMyLiveFormPage = this.getUIContext().getSharedLocalStorage();
    this.liveFormContext = this.storageForMyLiveFormPage?.get<common.LiveFormExtensionContext>('context');
    if (!this.liveFormContext) {
        console.info('MyLiveFormPage liveFormContext is empty');
        return;
      }
    this.disconnectServiceExtensionAbility();
  }

  private async disconnectServiceExtensionAbility(): Promise<void> {
    // connection为连接id，通常为connectServiceExtensionAbility接口的返回值，请开发者替换为实际取消连接的id值
    let connection = 1;
    let commRemote: rpc.IRemoteObject | null;

    try {
      await this.liveFormContext?.disconnectServiceExtensionAbility(connection);
      // 执行正常业务
      console.info('disconnectServiceExtensionAbility succeed');
    } catch (err) {
      // 处理错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    } finally {
      commRemote = null;
    }
  }

  build() {
    Stack() {
      // 请开发者替换为实际的页面
    }
  }
}
```