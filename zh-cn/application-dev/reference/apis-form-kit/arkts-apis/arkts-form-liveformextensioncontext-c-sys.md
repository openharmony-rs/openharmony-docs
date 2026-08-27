# LiveFormExtensionContext

LiveFormExtensionContext是[LiveFormExtensionAbility](arkts-form-app-form-liveformextensionability-liveformextensionability-c.md)的上下文，继承自 [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。它提供访问特定于LiveFormExtensionAbility资源的能力，支持在互动卡片中拉起应用页面，适用 于需要在互动卡片中响应用户点击并跳转到应用页面的场景，解决了互动卡片无法主动拉起应用页面的限制问题。

**继承/实现关系：** LiveFormExtensionContext extends ExtensionContext

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

## connectServiceExtensionAbility

```TypeScript
public connectServiceExtensionAbility(want: Want, connection: ConnectOptions): number
```

将当前LiveFormExtensionAbility客户端连接到一个 [ServiceExtensionAbility](../../../application-models/serviceextensionability-sys.md)服务端。调用该接口前，必须实现ConnectOptions接口。通过本接口连接成功后，LiveFormExtensionAbility可以通过ConnectOptions返回的[IRemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-iremoteobject-c.md)与 ServiceExtensionAbility进行通信，以使用ServiceExtensionAbility对外提供的能力。ServiceExtensionAbility是一类特殊的[ExtensionAbility](../../../application-models/extensionability-overview.md)组件，这类组件由系 统提供，通常用于提供指定场景后台服务能力，不支持开发者自定义。ServiceExtensionAbility提供后台服务扩展能力，支持后台运行并对外提供相应能力。三方应用可以连接该ExtensionAbility，并进行通信。通过本接口连接成功后，会启动ServiceExtensionAbility组件，具体请参考[组件启动规则](../../../application-models/component-startup-rules.md)。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 连接ServiceExtensionAbility的Want信息，包括Ability名称、Bundle名称等。 |
| connection | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-connectoptions-connectoptions-i.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息，连接成功会返回 [IRemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-iremoteobject-c.md)实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回连接id，客户端可以通过 [disconnectServiceExtensionAbility]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501011](../errorcode-form.md#16501011-卡片不支持调用当前接口) | The form can not support this operation |

**示例**

```TypeScript
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

```TypeScript
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

## disconnectServiceExtensionAbility

```TypeScript
public disconnectServiceExtensionAbility(connectionId: number): Promise<void>
```

断开与[ServiceExtensionAbility](../../../application-models/serviceextensionability-sys.md)的连接，断开连接之后开发者需要将连接成功时返回的 IRemoteObject对象置空。使用Promise异步回调。ServiceExtensionAbility是一类特殊的[ExtensionAbility](../../../application-models/extensionability-overview.md)组件，这类组件由系 统提供，通常用于提供指定场景后台服务能力，不支持开发者自定义。ServiceExtensionAbility提供后台服务扩展能力，支持后台运行并对外提供相应能力。三方应用可以连接该ExtensionAbility，并进行通信。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connectionId | number | 是 | 连接的ServiceExtensionAbility的连接id，即 [connectServiceExtensionAbility](#connectserviceextensionability)返回的connectionId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501011](../errorcode-form.md#16501011-卡片不支持调用当前接口) | The form can not support this operation |

**示例**

```TypeScript
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

```TypeScript
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
    //注意：应在connectServiceExtensionAbility连接成功时保存IRemoteObject对象
    //断开连接后，将保存的IRemoteObject对象置空
    try {
      await this.liveFormContext?.disconnectServiceExtensionAbility(connection);
      // 执行正常业务
      console.info('disconnectServiceExtensionAbility succeed');
      //将连接成功时保存的IRemoteObject对象置空，例如：this.savedRemoteObject = null;
    } catch (err) {
      // 处理错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }

  build() {
    Stack() {
      // 请开发者替换为实际的页面
    }
  }
}
```
