# AutoFillExtensionContext (自动填充扩展上下文)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

AutoFillExtensionContext模块是AutoFillExtensionAbility的上下文环境，继承自[ExtensionContext](js-apis-inner-application-extensionContext.md)。

> **说明：**
>
> 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
> 本模块接口仅可在Stage模型下使用。  
> 本模块接口为系统接口。

## 使用说明

在使用AutoFillExtensionContext的功能前，需要通过AutoFillExtensionAbility子类实例获取。

```ts
import { AutoFillExtensionAbility } from '@kit.AbilityKit';

class MyAutoFillExtensionAbility extends AutoFillExtensionAbility {
  onCreate() {
    let AutoFillExtensionContext = this.context;
  }
}
```

## AutoFillExtensionContext

### reloadInModal<sup>13+</sup>

reloadInModal(customData: CustomData): Promise\<void>

重新拉起模态页面。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名     | 类型                                                      | 必填 | 说明                         |
| ---------- | --------------------------------------------------------- | ---- | ---------------------------- |
| customData | [CustomData](js-apis-inner-application-customData-sys.md) | 是 | 拉起模态页面时的自定义信息。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Permission verification failed. A non-system application calls a system API.        |
| 401      | If the input parameter is not valid parameter.               |
| 16000011 | The context does not exist.                                  |
| 16000050 | Internal error.                                              |

**示例：**

通过点击账号密码输入框触发自动填充服务时，在[AutoFillExtensionAbility](js-apis-app-ability-autoFillExtensionAbility-sys.md)的onFillRequest生命周期中拉起账号选择界面。

当点击账号选择界面选择任意账号时，调用reloadInModal接口再次触发自动填充服务，在AutoFillExtensionAbility的onFillRequest生命周期中拉起模态页面。

```ts
// AutoFillAbility.ts
import { AutoFillExtensionAbility, autoFillManager, UIExtensionContentSession } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class AutoFillAbility extends AutoFillExtensionAbility {
  // ...
  onFillRequest(session: UIExtensionContentSession,
    request: autoFillManager.FillRequest,
    callback: autoFillManager.FillRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onFillRequest');
    try {
      // 创建LocalStorage并存储自动填充所需的数据
      let storage_fill: LocalStorage = new LocalStorage(
        {
          'session': session,
          'message': "AutoFill Page",
          'fillCallback': callback,
          'viewData': request.viewData,
          'autoFillExtensionContext': this.context,
          'customData': request.customData
        } as Record<string, Object>);
      if (request.customData == undefined) {
        // 加载自动填充处理界面
        session.loadContent('pages/AccountPage', storage_fill);
      } else {
        // 拉起模态页面
        session.loadContent('pages/ReloadInModal', storage_fill);
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'autofill failed to load content');
    }
  }
}
```

当点击账号选择界面选择任意账号时，调用reloadInModal接口。

```ts
// AccountPage.ets
import { autoFillManager, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct AccountPage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  viewData: autoFillManager.ViewData | undefined = this.storage?.get<autoFillManager.ViewData>('viewData');
  context: common.AutoFillExtensionContext | undefined = this.storage?.get<common.AutoFillExtensionContext>('autoFillExtensionContext');


  build() {
    Row() {
      Column() {
        List({ space: 10, initialIndex: 0 }) {
          ListItem() {
            Text('HelloWorld789456')
              .width('100%')
              .height(40)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(5)
          }
          .onClick(() => {
            if (this.viewData != undefined) {
              if (this.context != undefined) {
                // 调用reloadInModal接口重新触发自动填充，传递自定义数据用于模态页面
                this.context.reloadInModal({ data: { viewData: 20, text: 'HelloWorld789456' } }).then(() => {
                  console.info('reloadInModal successfully.')
                }).catch((err: BusinessError) => {
                  console.error(`reloadInModal failed. Code: ${err.code}, message: ${err.message}`);
                })
              }
            }
          });
        }
        // ...
      }
      .width('100%')
      .shadow(ShadowStyle.OUTER_FLOATING_SM)
    }
    .height('100%')
    .shadow(ShadowStyle.OUTER_FLOATING_SM)
  }
}
```

### connectServiceExtensionAbility

connectServiceExtensionAbility(want: Want, options: ConnectOptions): number

将当前AutoFillExtensionAbility连接到指定的ServiceExtensionAbility。连接成功后，可通过options的onConnect回调获取remote对象，并与其进行IPC通信；具体可调用的服务由目标ServiceExtensionAbility的remote接口定义，返回的连接ID用于断开连接。

ServiceExtensionAbility是一类由系统提供的特殊[ExtensionAbility](../../application-models/extensionability-overview.md)组件（不支持三方应用自定义），主要用于提供特定场景的后台服务。其他组件可与之建立连接，由其在后台根据调用者的请求信息处理相关事务。

> **说明：**
>
> - 组件启动规则详见：[设备内组件启动规则](../../application-models/component-startup-rules-inner-device.md)、[跨设备组件启动规则](../../application-models/component-startup-rules-cross-device.md)。
> - 该接口不支持连接分身应用的ServiceExtensionAbility。
> - 连接建立后，若AutoFillExtensionAbility被销毁，系统会自动断开该AutoFillExtensionAbility建立的所有连接。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | 是 | 连接ServiceExtensionAbility的Want信息，包括Ability名称、Bundle名称等。 |
| options | [ConnectOptions](js-apis-inner-ability-connectOptions.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 返回连接ID，客户端可以通过[disconnectServiceExtensionAbility](#disconnectserviceextensionability)传入该连接ID来断开连接。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist. |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by EDM. |
| 16000050 | Internal error. |
| 16000053 | The ability is not on the top of the UI. |
| 16000055 | Installation-free timed out. |
| 16000070 | The extension cannot start the service. |

**示例：**

```ts
import { AutoFillExtensionAbility, Want, common } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AutoFillAbility extends AutoFillExtensionAbility {
  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'ServiceExtensionAbility'
    };
    let commRemote: rpc.IRemoteObject | null;
    let options: common.ConnectOptions = {
      onConnect(elementName, remote) {
        commRemote = remote;
        console.info('onConnect...');
      },
      onDisconnect(elementName) {
        commRemote = null;
        console.info('onDisconnect...');
      },
      onFailed(code) {
        console.error(`onFailed, err code: ${code}.`);
      }
    };
    let connection: number;
    try {
      connection = this.context.connectServiceExtensionAbility(want, options);
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`connectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```

### disconnectServiceExtensionAbility

disconnectServiceExtensionAbility(connection: number): Promise\<void>

断开与指定ServiceExtensionAbility的连接。使用Promise异步回调。

断开连接后，开发者需将连接成功时获取的remote对象置空，以释放相关资源。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| connection | number | 是 | 连接的ServiceExtensionAbility的标识ID，即[connectServiceExtensionAbility](#connectserviceextensionability)返回的连接ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 16000011 | The context does not exist. |
| 16000050 | Internal error. |

**示例：**

```ts
import { AutoFillExtensionAbility } from '@kit.AbilityKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class AutoFillAbility extends AutoFillExtensionAbility {
  onForeground() {
    // connection需要通过connectServiceExtensionAbility接口返回获取，详见connectServiceExtensionAbility示例
    let connection = 1; // 示例值，实际开发中应使用连接时返回的连接ID
    let commRemote: rpc.IRemoteObject | null;

    try {
      this.context.disconnectServiceExtensionAbility(connection).then(() => {
        commRemote = null;
        // 执行正常业务
        console.info('disconnectServiceExtensionAbility succeed');
      }).catch((err: BusinessError) => {
        // 处理业务逻辑错误
        console.error(`disconnectServiceExtensionAbility failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      commRemote = null;
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`disconnectServiceExtensionAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```
