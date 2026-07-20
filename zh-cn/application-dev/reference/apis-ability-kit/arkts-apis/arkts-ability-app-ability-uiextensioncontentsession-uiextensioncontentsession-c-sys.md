# UIExtensionContentSession

UIExtensionAbility组件的界面操作类，提供页面加载、设置宿主应用窗口隐私模式等功能。

**起始版本：** 10

<!--Device-unnamed-declare class UIExtensionContentSession--><!--Device-unnamed-declare class UIExtensionContentSession-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';
```

<a id="getuiextensionhostwindowproxy"></a>
## getUIExtensionHostWindowProxy

```TypeScript
getUIExtensionHostWindowProxy(): uiExtensionHost.UIExtensionHostWindowProxy
```

获取当前UIExtension对应的窗口对象，用于通知宽高、位置、避让信息等。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-getUIExtensionHostWindowProxy(): uiExtensionHost.UIExtensionHostWindowProxy--><!--Device-UIExtensionContentSession-getUIExtensionHostWindowProxy(): uiExtensionHost.UIExtensionHostWindowProxy-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| uiExtensionHost.UIExtensionHostWindowProxy | 宿主应用窗口信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { uiExtensionHost } from '@kit.ArkUI';

const TAG: string = '[UIExtAbility]';

export default class UIExtAbility extends UIExtensionAbility {
  onCreate() {
    console.info(TAG, `UIExtAbility onCreate`);
  }

  onForeground() {
    console.info(TAG, `UIExtAbility onForeground`);
  }

  onBackground() {
    console.info(TAG, `UIExtAbility onBackground`);
  }

  onDestroy() {
    console.info(TAG, `UIExtAbility onDestroy`);
  }

  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    let extensionHostWindow = session.getUIExtensionHostWindowProxy();
    let data: Record<string, UIExtensionContentSession | uiExtensionHost.UIExtensionHostWindowProxy> = {
      'session': session,
      'extensionHostWindow': extensionHostWindow
    };
    let storage: LocalStorage = new LocalStorage(data);

    try {
      session.loadContent('pages/Extension', storage);
    } catch (err) {
      console.error('loadContent err:' + JSON.stringify(err));
    }
  }

  onSessionDestroy(session: UIExtensionContentSession) {
    console.info(TAG, `UIExtAbility onSessionDestroy`);
  }
}

```

<a id="senddata"></a>
## sendData

```TypeScript
sendData(data: Record<string, Object>): void
```

发送数据给UIExtensionComponent控件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-sendData(data: Record<string, Object>): void--><!--Device-UIExtensionContentSession-sendData(data: Record<string, Object>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 发送给UIExtensionComponent控件的数据参数。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';

@Entry()
@Component
struct Index {
  private storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('SendData')
        .onClick(() => {
          let data: Record<string, Object> = {
            'number': 123456,
            'message': 'test'
          };

          try {
            this.session?.sendData(data);
          } catch (err) {
            console.error('sendData err:' + JSON.stringify(err));
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}

```

<a id="setreceivedatacallback"></a>
## setReceiveDataCallback

```TypeScript
setReceiveDataCallback(callback: (data: Record<string, Object>) => void): void
```

设置从UIExtensionComponent控件接收数据的回调方法。使用callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-setReceiveDataCallback(callback: (data: Record<string, Object>) => void): void--><!--Device-UIExtensionContentSession-setReceiveDataCallback(callback: (data: Record<string, Object>) => void): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (data: Record&lt;string, Object&gt;) =&gt; void | 是 | 回调函数，返回接收的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';

@Entry()
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('SendData')
        .onClick(() => {
          this.session?.setReceiveDataCallback((data: Record<string, Object>) => {
            console.info(`Succeeded in setReceiveDataCallback, data: ${JSON.stringify(data)}`);
          });
        })
    }
    .height('100%')
    .width('100%')
  }
}

```

<a id="setreceivedataforresultcallback"></a>
## setReceiveDataForResultCallback

```TypeScript
setReceiveDataForResultCallback(callback: (data: Record<string, Object>) => Record<string, Object>): void
```

设置从UIExtensionComponent控件接收数据带返回值的回调方法。使用callback异步回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-setReceiveDataForResultCallback(callback: (data: Record<string, Object>) => Record<string, Object>): void--><!--Device-UIExtensionContentSession-setReceiveDataForResultCallback(callback: (data: Record<string, Object>) => Record<string, Object>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (data: Record&lt;string, Object&gt;) =&gt; Record&lt;string, Object&gt; | 是 | 回调函数，返回带返回值的接收的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';

@Entry()
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('SetReceiveDataForResultCallback')
        .onClick(() => {
          this.session?.setReceiveDataForResultCallback((data: Record<string, Object>) => {
            console.info(`Succeeded in setReceiveDataCallback, data: ${JSON.stringify(data)}`);
            return data;
          });
        })
    }
    .height('100%')
    .width('100%')
  }
}

```

<a id="setwindowbackgroundcolor"></a>
## setWindowBackgroundColor

```TypeScript
setWindowBackgroundColor(color: string): void
```

设置UIExtensionAbility加载界面的背景色。该接口需要在[loadContent()](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md#loadcontent-1)调用生效后使用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-setWindowBackgroundColor(color: string): void--><!--Device-UIExtensionContentSession-setWindowBackgroundColor(color: string): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | string | 是 | 需要设置的背景色，为十六进制RGB或ARGB颜色，不区分大小写，例如`#00FF00`或`#FF00FF00`。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { UIExtensionContentSession, UIExtensionAbility, Want } from '@kit.AbilityKit';

export default class UIExtAbility extends UIExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('session', session);

    try {
      session.loadContent('pages/Extension', storage);
    } catch (err) {
      console.error('loadContent err:' + JSON.stringify(err));
    }

    try {
      session.setWindowBackgroundColor('#00FF00');
    } catch (err) {
      console.error('setWindowBackgroundColor err:' + JSON.stringify(err));
    }
  }

  // ...
}

```

<a id="startability"></a>
## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

启动Ability。使用callback异步回调。

> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（Stage模型）](docroot://application-models/component-startup-rules.md)。  
> > 对应UIExtensionComponent控件所在的应用需要处于前台获焦状态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbility(want: Want, callback: AsyncCallback<void>): void--><!--Device-UIExtensionContentSession-startAbility(want: Want, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动Ability的want信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIExtensionContentSession, UIExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    session.startAbility(want, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to startAbility, code: ${err.code}, msg: ${err.message}`);
        return;
      }
      console.info(`Succeeded in startAbility`);
    })
  }

  // ...
}

```

<a id="startability-1"></a>
## startAbility

```TypeScript
startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

启动Ability。使用callback异步回调。

> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（Stage模型）](docroot://application-models/component-startup-rules.md)。  
> > 对应UIExtensionComponent控件所在的应用需要处于前台获焦状态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void--><!--Device-UIExtensionContentSession-startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动Ability的want信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 是 | 启动Ability所携带的参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIExtensionContentSession, UIExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let startOptions: StartOptions = {
      displayId: 0
    };

    session.startAbility(want, startOptions, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to startAbility, code: ${err.code}, msg: ${err.message}`);
        return;
      }
      console.info(`Succeeded in startAbility`);
    })
  }

  // ...
}

```

<a id="startability-2"></a>
## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

启动Ability。使用Promise异步回调。

> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（Stage模型）](docroot://application-models/component-startup-rules.md)。  
> > 对应UIExtensionComponent控件所在的应用需要处于前台获焦状态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbility(want: Want, options?: StartOptions): Promise<void>--><!--Device-UIExtensionContentSession-startAbility(want: Want, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动Ability的want信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIExtensionContentSession, UIExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let startOptions: StartOptions = {
      displayId: 0
    };

    session.startAbility(want, startOptions)
      .then(() => {
        console.info(`Succeeded in startAbility`);
      })
      .catch((err: BusinessError) => {
        console.error(`Failed to startAbility, code: ${err.code}, msg: ${err.message}`);
      });
  }

  // ...
}

```

<a id="startabilityascaller"></a>
## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, callback: AsyncCallback<void>): void
```

初始Ability将自己的caller信息（如BundleName、AbilityName等）置于want参数中，传递给中间层的ExtensionAbility。当ExtensionAbility通过该接口拉起另外一个Ability，被拉起的Ability可以从onCreate生命周期获取到初始Ability的caller信息。使用callback异步回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbilityAsCaller(want: Want, callback: AsyncCallback<void>): void--><!--Device-UIExtensionContentSession-startAbilityAsCaller(want: Want, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动Ability的want信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIExtensionContentSession, UIExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';

    session.startAbilityAsCaller(localWant, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to startAbilityAsCaller, code: ${err.code}, msg: ${err.message}`);
        return;
      }
      console.info(`Succeeded in startAbilityAsCaller`);
    })
  }

  // ...
}

```

<a id="startabilityascaller-1"></a>
## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

初始Ability将自己的caller信息（如BundleName、AbilityName等）置于want参数中，传递给中间层的ExtensionAbility。当ExtensionAbility通过该接口拉起另外一个Ability，被拉起的Ability可以从onCreate生命周期获取到初始Ability的caller信息。使用callback异步回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbilityAsCaller(want: Want, options: StartOptions, callback: AsyncCallback<void>): void--><!--Device-UIExtensionContentSession-startAbilityAsCaller(want: Want, options: StartOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动Ability的want信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 是 | 启动Ability所携带的参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当启动Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIExtensionContentSession, UIExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';

    let startOptions: StartOptions = {
      displayId: 0
    };

    session.startAbilityAsCaller(localWant, startOptions, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to startAbilityAsCaller, code: ${err.code}, msg: ${err.message}`);
        return;
      }
      console.info(`Succeeded in startAbilityAsCaller`);
    })
  }

  // ...
}

```

<a id="startabilityascaller-2"></a>
## startAbilityAsCaller

```TypeScript
startAbilityAsCaller(want: Want, options?: StartOptions): Promise<void>
```

初始Ability将自己的caller信息（如BundleName、AbilityName等）置于want参数中，传递给中间层的ExtensionAbility。当ExtensionAbility通过该接口拉起另外一个Ability，被拉起的Ability可以从onCreate生命周期获取到初始Ability的caller信息。使用Promise异步回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbilityAsCaller(want: Want, options?: StartOptions): Promise<void>--><!--Device-UIExtensionContentSession-startAbilityAsCaller(want: Want, options?: StartOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动Ability的want信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIExtensionContentSession, UIExtensionAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let localWant: Want = want;
    localWant.bundleName = 'com.example.demo';
    localWant.moduleName = 'entry';
    localWant.abilityName = 'TestAbility';

    let startOptions: StartOptions = {
      displayId: 0
    };

    session.startAbilityAsCaller(localWant, startOptions)
      .then(() => {
        console.info(`Succeeded in startAbilityAsCaller`);
      })
      .catch((err: BusinessError) => {
        console.error(`Failed to startAbilityAsCaller, code: ${err.code}, msg: ${err.message}`);
      });
  }

  // ...
}

```

<a id="startabilityforresult"></a>
## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, callback: AsyncCallback<AbilityResult>): void
```

启动一个Ability，在Ability终止后返回结果给调用方。使用callback异步回调。Ability的终止方式包括以下几种情况：

- 正常情况下可通过调用[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)接口使之终止并且返回结果给调用方。  
- 异常情况下比如杀死Ability会返回异常信息给调用方，异常信息中resultCode为-1。  
- 如果被启动的Ability模式是单实例模式，不同应用多次调用该接口启动这个Ability，当这个Ability调用[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)接口使之终止时，只将正常结果返回给最后一个调用方，其他调用方返回异常信息，异常信息中resultCode为-1。

> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（Stage模型）](docroot://application-models/component-startup-rules.md)。  
> > 对应UIExtensionComponent控件所在的应用需要处于前台获焦状态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbilityForResult(want: Want, callback: AsyncCallback<AbilityResult>): void--><!--Device-UIExtensionContentSession-startAbilityForResult(want: Want, callback: AsyncCallback<AbilityResult>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动Ability的want信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AbilityResult&gt; | 是 | 回调函数。当Ability启动并终止成功，err为undefined，data为获取到的结果码和数据；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIExtensionContentSession, UIExtensionAbility, Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    session.startAbilityForResult(want, (err: BusinessError, data: common.AbilityResult) => {
      if (err) {
        console.error(`Failed to startAbilityForResult, code: ${err.code}, msg: ${err.message}`);
        return;
      }
      console.info(`Succeeded in startAbilityForResult, data: ${JSON.stringify(data)}`);
    })
  }

  // ...
}

```

<a id="startabilityforresult-1"></a>
## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options: StartOptions, callback: AsyncCallback<AbilityResult>): void
```

启动一个Ability，在Ability终止后返回结果给调用方。使用callback异步回调。Ability的终止方式包括以下几种情况：

- 正常情况下可通过调用[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)接口使之终止并且返回结果给调用方。  
- 异常情况下比如杀死Ability会返回异常信息给调用方，异常信息中resultCode为-1。  
- 如果被启动的Ability模式是单实例模式，不同应用多次调用该接口启动这个Ability，当这个Ability调用[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)接口使之终止时，只将正常结果返回给最后一个调用方，其他调用方返回异常信息，异常信息中resultCode为-1。

> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（Stage模型）](docroot://application-models/component-startup-rules.md)。  
> > 对应UIExtensionComponent控件所在的应用需要处于前台获焦状态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbilityForResult(want: Want, options: StartOptions, callback: AsyncCallback<AbilityResult>): void--><!--Device-UIExtensionContentSession-startAbilityForResult(want: Want, options: StartOptions, callback: AsyncCallback<AbilityResult>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动Ability的want信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 是 | 启动Ability所携带的参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AbilityResult&gt; | 是 | 回调函数。当Ability启动并终止成功，err为undefined，data为获取到的结果码和数据；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIExtensionContentSession, UIExtensionAbility, Want, StartOptions, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let startOptions: StartOptions = {
      displayId: 0
    };

    session.startAbilityForResult(want, startOptions, (err: BusinessError, data: common.AbilityResult) => {
      if (err) {
        console.error(`Failed to startAbilityForResult, code: ${err.code}, msg: ${err.message}`);
        return;
      }
      console.info(`Succeeded in startAbilityForResult, data: ${JSON.stringify(data)}`);
    })
  }

  // ...
}

```

<a id="startabilityforresult-2"></a>
## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>
```

启动一个Ability，在Ability终止后返回结果给调用方。使用Promise异步回调。Ability的终止方式包括以下几种情况：

- 正常情况下可通过调用[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)接口使之终止并且返回结果给调用方。  
- 异常情况下比如杀死Ability会返回异常信息给调用方，异常信息中resultCode为-1。  
- 如果被启动的Ability模式是单实例模式，不同应用多次调用该接口启动这个Ability，当这个Ability调用[terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult-1)接口使之终止时，只将正常结果返回给最后一个调用方，其他调用方返回异常信息，异常信息中resultCode为-1。

> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（Stage模型）](docroot://application-models/component-startup-rules.md)。  
> > 对应UIExtensionComponent控件所在的应用需要处于前台获焦状态。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>--><!--Device-UIExtensionContentSession-startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 启动Ability的want信息。 |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c-sys.md) | 否 | 启动Ability所携带的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityResult&gt; | Promise对象，返回结果码和数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-wukong模式不允许启动停止ability) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-不允许带迁移flag) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-非顶层应用) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released. |

**示例：**

```TypeScript
import { UIExtensionContentSession, UIExtensionAbility, Want, StartOptions, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let startOptions: StartOptions = {
      displayId: 0
    };

    session.startAbilityForResult(want, startOptions)
      .then((data: common.AbilityResult) => {
        console.info(`Succeeded in startAbilityForResult, data: ${JSON.stringify(data)}`);
      })
      .catch((err: BusinessError) => {
        console.error(`Failed to startAbilityForResult, code: ${err.code}, msg: ${err.message}`);
      });
  }

  // ...
}

```

