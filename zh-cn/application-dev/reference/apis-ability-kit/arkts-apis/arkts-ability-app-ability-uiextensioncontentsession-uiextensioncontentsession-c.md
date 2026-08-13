# UIExtensionContentSession

UIExtensionAbility组件的界面操作类，提供页面加载、设置宿主应用窗口隐私模式等功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class UIExtensionContentSession--><!--Device-unnamed-declare class UIExtensionContentSession-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## getUIExtensionWindowProxy

```TypeScript
getUIExtensionWindowProxy(): uiExtension.WindowProxy
```

获取UIExtension窗口代理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-getUIExtensionWindowProxy(): uiExtension.WindowProxy--><!--Device-UIExtensionContentSession-getUIExtensionWindowProxy(): uiExtension.WindowProxy-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| uiExtension.WindowProxy | UIExtensionAbility组件的宿主应用窗口代理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
// Index.ets
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { uiExtension } from '@kit.ArkUI';

@Entry()
@Component
struct Extension {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  @State message: string = 'EmbeddedUIExtensionAbility Index';
  private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');
  private extensionWindow: uiExtension.WindowProxy | undefined = this.session?.getUIExtensionWindowProxy();

  aboutToAppear(): void {
    this.extensionWindow?.on('windowSizeChange', (size) => {
      console.info(`size = ${JSON.stringify(size)}`);
    });
    this.extensionWindow?.on('avoidAreaChange', (info) => {
      console.info(`type = ${JSON.stringify(info.type)}, area = ${JSON.stringify(info.area)}`);
    });
  }

  aboutToDisappear(): void {
    this.extensionWindow?.off('windowSizeChange');
    this.extensionWindow?.off('avoidAreaChange');
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(20)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
// Index.ets
import { UIExtensionContentSession } from '@kit.AbilityKit';
import uiExtension from '@ohos.arkui.uiExtension';
import { Entry, Text, Column, Component, FontWeight, State } from '@kit.ArkUI';

@Entry()
@Component
struct Extension {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  @State message: string = 'EmbeddedUIExtensionAbility Index';
  private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');
  private extensionWindow: uiExtension.WindowProxy | undefined = this.session?.getUIExtensionWindowProxy();

  aboutToAppear(): void {
    this.extensionWindow?.onWindowSizeChange((size) => {
      console.info(`size = ${JSON.stringify(size)}`);
    });
    this.extensionWindow?.onAvoidAreaChange((info) => {
      console.info(`type = ${JSON.stringify(info.type)}, area = ${JSON.stringify(info.area)}`);
    });
  }

  aboutToDisappear(): void {
    this.extensionWindow?.offWindowSizeChange();
    this.extensionWindow?.offWindowSizeChange();
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(20)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
  }
}
```

## loadContent

```TypeScript
loadContent(path: string, storage?: LocalStorage): void
```

为[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#UIExtensionAbility)组件加载页面，支持通过 [LocalStorage](../../../ui/state-management/arkts-localstorage.md)传递状态属性给被加载的页面。该接口用于开发者在UIExtensionAbility组件的 [onSessionCreate](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onSessionCreate)生命周期中加载页面。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-loadContent(path: string, storage?: LocalStorage): void--><!--Device-UIExtensionContentSession-loadContent(path: string, storage?: LocalStorage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 要加载的页面所在的路径，该路径通过[module.json5配置文件](../../../quick-start/module-configuration-file.md)中的 [pages标签](../../../quick-start/module-configuration-file.md#pages标签)配置。 |
| storage | LocalStorage | 否 | 页面级UI状态存储单元，开发者可通过该参数为加载的页面传递状态属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { UIExtensionContentSession, ShareExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ShareExtAbility extends ShareExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    try {
      let storage: LocalStorage = new LocalStorage();
      storage.setOrCreate('session', session);
      session.loadContent('pages/Extension', storage);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`Failed to load content, code: ${code}, msg: ${message}`);
    }
  }

  // ...
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
// UIExtensionAbility不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { UIExtensionContentSession, ShareExtensionAbility, Want } from '@kit.AbilityKit';
import { LocalStorage } from '@kit.ArkUI';

export default class ShareExtAbility extends ShareExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('session', session);
    session.loadContent('pages/Extension', storage);
  }

  // ...
}
```

## loadContentByName

```TypeScript
loadContentByName(name: string, storage?: LocalStorage): void
```

为[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#UIExtensionAbility)组件加载 [命名路由](../../../ui/arkts-routing.md#命名路由)页面，支持通过 [LocalStorage](../../../ui/state-management/arkts-localstorage.md)传递状态属性给被加载的页面。该接口用于开发者在UIExtensionAbility组件的 [onSessionCreate](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#onSessionCreate)生命周期中加载命名路由页面。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-loadContentByName(name: string, storage?: LocalStorage): void--><!--Device-UIExtensionContentSession-loadContentByName(name: string, storage?: LocalStorage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 命名路由页面的名称。 |
| storage | LocalStorage | 否 | 页面级UI状态存储单元，开发者可通过该参数为加载的页面传递状态属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## 示例

UIExtensionAbility组件的实现：

```TypeScript
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { UIExtensionContentSession, ShareExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import './pages/UIExtensionPage'; // 导入命名路由页面，示例代码以“./pages/UIExtensionPage.ets”文件为例，在实际代码开发过程中修改为真实路径和文件名称。

export default class ShareExtAbility extends ShareExtensionAbility {
  // 其他生命周期和实现

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('session', session);

    let name: string = 'UIExtPage'; // 命名路由页面的名字。
    try {
      session.loadContentByName(name, storage);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`Failed to load content by name ${name}, code: ${code}, msg: ${message}`);
    }
  }

  // 其他生命周期和实现
}
```

UIExtensionAbility组件加载的命名路由页面的实现：

```TypeScript
// “./pages/UIExtensionPage.ets”文件的实现。
import { UIExtensionContentSession } from '@kit.AbilityKit';

@Entry({ routeName: 'UIExtPage' }) // 通过“routeName”定义命名路由页面的名字。
@Component
struct UIExtensionPage {
  @State message: string = 'Hello world';
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(20)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

UIExtensionAbility的实现：

```TypeScript
'use static'
// UIExtensionAbility不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { UIExtensionContentSession, ShareExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { LocalStorage } from '@kit.ArkUI';

export default class ShareExtAbility extends ShareExtensionAbility {
  // 其他生命周期和实现

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('session', session);

    let name: string = 'UIExtPage'; // 命名路由页面的名字。
    try {
      session.loadContentByName(name, storage);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`Failed to load content by name ${name}, code: ${code}, msg: ${message}`);
    }
  }

  // 其他生命周期和实现
}
```

UIExtensionAbility加载的命名路由页面的实现：

```TypeScript
// “./pages/UIExtensionPage.ets”文件的实现。
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { Entry, Text, Column, Row, Component, Button, FontWeight, State, LocalStorage } from '@kit.ArkUI';

@Entry({ routeName: 'UIExtPage' })
  // 通过“routeName”定义命名路由页面的名字。
@Component
struct UIExtensionPage {
  @State message: string = 'Hello world';
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(20)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## setWindowPrivacyMode

```TypeScript
setWindowPrivacyMode(isPrivacyMode: boolean): Promise<void>
```

设置宿主应用窗口的隐私模式开启或关闭。设置为隐私模式的窗口，窗口内容将无法被截屏或录屏。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRIVACY_WINDOW

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-setWindowPrivacyMode(isPrivacyMode: boolean): Promise<void>--><!--Device-UIExtensionContentSession-setWindowPrivacyMode(isPrivacyMode: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isPrivacyMode | boolean | 是 | 表示是否开启隐私模式。true表示开启；false表示关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |

## 示例

```TypeScript
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { UIExtensionContentSession, ShareExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ShareExtAbility extends ShareExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let isPrivacyMode: boolean = true;
    try {
      session.setWindowPrivacyMode(isPrivacyMode)
        .then(() => {
          console.info(`Succeeded in setting window to privacy mode.`);
        })
        .catch((error: Error) => {
          let err = error as BusinessError;
          console.error(`Failed to set window to privacy mode, code: ${err.code}, msg: ${err.message}`);
        });
    } catch (e) {
      let code = (e as BusinessError).code;
      let msg = (e as BusinessError).message;
      console.error(`Failed to set window to privacy mode, code: ${code}, msg: ${msg}`);
    }
  }

  // ...
}
```

## setWindowPrivacyMode

```TypeScript
setWindowPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback<void>): void
```

设置宿主应用窗口的隐私模式开启或关闭。设置为隐私模式的窗口，窗口内容将无法被截屏或录屏。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRIVACY_WINDOW

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-setWindowPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback<void>): void--><!--Device-UIExtensionContentSession-setWindowPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isPrivacyMode | boolean | 是 | 表示是否开启隐私模式。true表示开启；false表示关闭。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当设置成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |

## 示例

```TypeScript
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { UIExtensionContentSession, ShareExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ShareExtAbility extends ShareExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let isPrivacyMode: boolean = true;
    try {
      session.setWindowPrivacyMode(isPrivacyMode, (err: BusinessError | null) => {
        if (err) {
          console.error(`Failed to set window to privacy mode, code: ${err.code}, msg: ${err.message}`);
          return;
        }
        console.info(`Succeeded in setting window to privacy mode.`);
      });
    } catch (e) {
      let code = (e as BusinessError).code;
      let msg = (e as BusinessError).message;
      console.error(`Failed to set window to privacy mode, code: ${code}, msg: ${msg}`);
    }
  }

  // ...
}
```

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, Object>,
    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void
```

通过type隐式启动UIExtensionAbility。使用callback异步回调。仅支持处于前台的应用调用。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbilityByType(type: string, wantParam: Record<string, Object>,    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void--><!--Device-UIExtensionContentSession-startAbilityByType(type: string, wantParam: Record<string, Object>,    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | UIExtensionAbility组件类型，取值详见 [通过startAbilityByType接口拉起垂类面板](../../../application-models/start-intent-panel.md#匹配规则)。 |
| wantParam | Record&lt;string, Object&gt; | 是 | 表示启动UIExtensionAbility组件时传递的参数。 |
| abilityStartCallback | [AbilityStartCallback](../../apis-na/arkts-apis/arkts-na-abilitystartcallback-i.md) | 是 | 表示启动UIExtensionAbility组件的执行结果。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当接口调用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 11+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 11+ |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 11+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 11+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 11+ |

## 示例

```TypeScript
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { UIExtensionContentSession, ShareExtensionAbility, Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ShareExtAbility extends ShareExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let wantParams: Record<string, Object> = {
      'sceneType': 1
    };
    let abilityStartCallback: common.AbilityStartCallback = {
      onError: (code: number, name: string, message: string) => {
        console.error(`onError, code: ${code}, name: ${name}, msg: ${message}`);
      },
      onResult: (result: common.AbilityResult) => {
        console.info(`onResult, result: ${JSON.stringify(result)}`);
      }
    };

    session.startAbilityByType('navigation', wantParams, abilityStartCallback, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to startAbilityByType, code: ${err.code}, msg: ${err.message}`);
        return;
      }
      console.info(`Succeeded in startAbilityByType`);
    });
  }

  // ...
}
```

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, RecordData>,
    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void
```

通过type隐式启动UIExtensionAbility。使用callback异步回调。仅支持处于前台的应用调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbilityByType(type: string, wantParam: Record<string, RecordData>,    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void--><!--Device-UIExtensionContentSession-startAbilityByType(type: string, wantParam: Record<string, RecordData>,    abilityStartCallback: AbilityStartCallback, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 显示拉起的UIExtensionAbility类型，取值详见 [通过startAbilityByType接口拉起垂类面板](../../../application-models/start-intent-panel.md#匹配规则)。 |
| wantParam | Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt; | 是 | 表示扩展参数。 |
| abilityStartCallback | [AbilityStartCallback](../../apis-na/arkts-apis/arkts-na-abilitystartcallback-i.md) | 是 | 回调函数，返回启动失败后的详细错误信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当启动Ability成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
// UIExtensionAbility不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { UIExtensionContentSession, ShareExtensionAbility, Want, common } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

class MyAbilityStartCallback implements common.AbilityStartCallback {
  onError(code: int, name: string, message: string): void {
    console.info(`startAbilityByType Error:` + "code:" + code + "name:" + name + "message:" + message);
  }

  onResult?: (abilityResult: common.AbilityResult) => void = (parameter: common.AbilityResult) => {
    console.info(`startAbilityByType resultCode:` + parameter.resultCode + `bundleName:` + parameter.want?.bundleName);
  }
}

export default class ShareExtAbility extends ShareExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let wantParams: Record<string, RecordData> = {
      'sceneType': 1
    };

    let abilityStartCallback = new MyAbilityStartCallback();
    session.startAbilityByType('test', wantParams, abilityStartCallback, (err: BusinessError | null) => {
      if (err) {
        console.error(`Failed to startAbilityByType, code: ${err.code}, msg: ${err.message}`);
        return;
      }
      console.info(`Succeeded in startAbilityByType`);
    });
  }

  // ...
}
```

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, Object>,
    abilityStartCallback: AbilityStartCallback): Promise<void>
```

通过type隐式启动UIExtensionAbility组件。使用Promise异步回调。仅支持处于前台的应用调用。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbilityByType(type: string, wantParam: Record<string, Object>,    abilityStartCallback: AbilityStartCallback): Promise<void>--><!--Device-UIExtensionContentSession-startAbilityByType(type: string, wantParam: Record<string, Object>,    abilityStartCallback: AbilityStartCallback): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | UIExtensionAbility组件类型，取值详见 [通过startAbilityByType接口拉起垂类面板](../../../application-models/start-intent-panel.md#匹配规则)。 |
| wantParam | Record&lt;string, Object&gt; | 是 | 表示启动UIExtensionAbility组件时传递的参数。 |
| abilityStartCallback | [AbilityStartCallback](../../apis-na/arkts-apis/arkts-na-abilitystartcallback-i.md) | 是 | 表示启动UIExtensionAbility组件的执行结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component.<br>**适用版本：** 11+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist.<br>**适用版本：** 11+ |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type.<br>**适用版本：** 11+ |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-通用组件客户端caller已回收) | The caller has been released.<br>**适用版本：** 11+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface.<br>**适用版本：** 11+ |

## 示例

```TypeScript
// UIExtensionAbility组件不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { UIExtensionContentSession, ShareExtensionAbility, Want, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ShareExtAbility extends ShareExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let wantParams: Record<string, Object> = {
      'sceneType': 1
    };
    let abilityStartCallback: common.AbilityStartCallback = {
      onError: (code: number, name: string, message: string) => {
        console.error(`onError, code: ${code}, name: ${name}, msg: ${message}`);
      },
      onResult: (result: common.AbilityResult) => {
        console.info(`onResult, result: ${JSON.stringify(result)}`);
      }
    };

    session.startAbilityByType('test', wantParams, abilityStartCallback)
      .then(() => {
        console.info(`Succeeded in startAbilityByType`);
      })
      .catch((err: BusinessError) => {
        console.error(`Failed to startAbilityByType, code: ${err.code}, msg: ${err.message}`);
      });
  }

  // ...
}
```

## startAbilityByType

```TypeScript
startAbilityByType(type: string, wantParam: Record<string, RecordData>,
    abilityStartCallback: AbilityStartCallback): Promise<void>
```

通过type隐式启动UIExtensionAbility。使用callback异步回调。仅支持处于前台的应用调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-startAbilityByType(type: string, wantParam: Record<string, RecordData>,    abilityStartCallback: AbilityStartCallback): Promise<void>--><!--Device-UIExtensionContentSession-startAbilityByType(type: string, wantParam: Record<string, RecordData>,    abilityStartCallback: AbilityStartCallback): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 显示拉起的UIExtensionAbility类型，取值详见 [通过startAbilityByType接口拉起垂类面板](../../../application-models/start-intent-panel.md#匹配规则)。 |
| wantParam | Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt; | 是 | 表示扩展参数。 |
| abilityStartCallback | [AbilityStartCallback](../../apis-na/arkts-apis/arkts-na-abilitystartcallback-i.md) | 是 | 回调函数，返回启动失败后的详细错误信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
// UIExtensionAbility不支持三方应用直接继承，故以派生类ShareExtensionAbility举例说明。
import { UIExtensionContentSession, ShareExtensionAbility, Want, common } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

class MyAbilityStartCallback implements common.AbilityStartCallback {
  onError(code: int, name: string, message: string): void {
    console.info(`startAbilityByType Error:` + "code:" + code + "name:" + name + "message:" + message);
  }

  onResult?: (abilityResult: common.AbilityResult) => void = (parameter: common.AbilityResult) => {
    console.info(`startAbilityByType resultCode:` + parameter.resultCode + `bundleName:` + parameter.want?.bundleName);
  }
}

export default class ShareExtAbility extends ShareExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let wantParams: Record<string, RecordData> = {
      'sceneType': 1
    };

    let abilityStartCallback = new MyAbilityStartCallback();
    session.startAbilityByType('test', wantParams, abilityStartCallback).then(() => {
      console.info(`Succeeded in startAbilityByType`);
    }).catch((error) => {
      let err = error as BusinessError;
      console.error(`Failed to startAbilityByType, code: ${err.code}, msg: ${err.message}`);
    });
  }

  // ...
}
```

## terminateSelf

```TypeScript
terminateSelf(callback: AsyncCallback<void>): void
```

销毁UIExtensionAbility组件自身，同时关闭对应的宿主应用窗口界面。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-terminateSelf(callback: AsyncCallback<void>): void--><!--Device-UIExtensionContentSession-terminateSelf(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当接口调用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry()
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('TerminateSelf')
        .onClick(() => {
          this.session?.terminateSelf((err: BusinessError) => {
            if (err) {
              console.error(`Failed to terminate self, code: ${err.code}, msg: ${err.message}`);
              return;
            }
            console.info(`Succeeded in terminating self.`);
          });

          this.storage?.clear();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Entry, Component, Button, RelativeContainer, LocalStorage } from '@kit.ArkUI';

@Entry()
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('TerminateSelf')
        .onClick(() => {
          this.session?.terminateSelf((err: BusinessError | null) => {
            if (err) {
              console.error(`Failed to terminate self, code: ${err.code}, msg: ${err.message}`);
              return;
            }
            console.info(`Succeeded in terminating self.`);
          });

          this.storage?.clear();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

销毁UIExtensionAbility组件自身，同时关闭对应的宿主应用窗口界面。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-terminateSelf(): Promise<void>--><!--Device-UIExtensionContentSession-terminateSelf(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry()
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('TerminateSelf')
        .onClick(() => {
          this.session?.terminateSelf()
            .then(() => {
              console.info(`Succeeded in terminating self.`);
            })
            .catch((err: BusinessError) => {
              console.error(`Failed to terminate self, code: ${err.code}, msg: ${err.message}`);
            });

          this.storage?.clear();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Entry, Component, Button, RelativeContainer, LocalStorage } from '@kit.ArkUI';

@Entry()
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('TerminateSelf')
        .onClick(() => {
          this.session?.terminateSelf()
            .then(() => {
              console.info(`Succeeded in terminating self.`);
            })
            .catch((error) => {
              let err = error as BusinessError;
              console.error(`Failed to terminate self, code: ${err.code}, msg: ${err.message}`);
            });

          this.storage?.clear();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback<void>): void
```

销毁UIExtensionAbility组件自身，关闭对应的宿主应用窗口界面，并将结果返回给宿主应用。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback<void>): void--><!--Device-UIExtensionContentSession-terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | 是 | 返回给宿主应用的信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当接口调用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { UIExtensionContentSession, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry()
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('TerminateSelfWithResult')
        .onClick(() => {
          let abilityResult: common.AbilityResult = {
            resultCode: 0,
            want: {
              bundleName: 'com.ohos.uiextensioncontentsession',
              parameters: {
                'result': 123456
              }
            }
          };

          this.session?.terminateSelfWithResult(abilityResult, (err: BusinessError) => {
            if (err) {
              console.error(`Failed to terminate self with result, code: ${err.code}, msg: ${err.message}`);
              return;
            }
            console.info(`Succeeded in terminating self with result.`);
          });

          this.storage?.clear();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIExtensionContentSession, common } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';
import { Entry, Component, Button, RelativeContainer, LocalStorage } from '@kit.ArkUI';

@Entry()
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('TerminateSelfWithResult')
        .onClick(() => {
          let abilityResult: common.AbilityResult = {
            resultCode: 0,
            want: {
              bundleName: 'com.ohos.uiextensioncontentsession',
              parameters: {
                'result': 123456
              } as Record<string, RecordData>
            }
          };

          this.session?.terminateSelfWithResult(abilityResult, (err: BusinessError | null) => {
            if (err) {
              console.error(`Failed to terminate self with result, code: ${err.code}, msg: ${err.message}`);
              return;
            }
            console.info(`Succeeded in terminating self with result.`);
          });

          this.storage?.clear();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult): Promise<void>
```

销毁UIExtensionAbility组件自身，关闭对应的宿主应用窗口界面，并将结果返回给宿主应用。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionContentSession-terminateSelfWithResult(parameter: AbilityResult): Promise<void>--><!--Device-UIExtensionContentSession-terminateSelfWithResult(parameter: AbilityResult): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | 是 | 返回给宿主应用的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { UIExtensionContentSession, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry()
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('TerminateSelfWithResult')
        .onClick(() => {
          let abilityResult: common.AbilityResult = {
            resultCode: 0,
            want: {
              bundleName: 'com.ohos.uiextensioncontentsession',
              parameters: {
                'result': 123456
              }
            }
          };

          this.session?.terminateSelfWithResult(abilityResult)
            .then(() => {
              console.info(`Succeeded in terminating self with result.`);
            })
            .catch((err: BusinessError) => {
              console.error(`Failed to terminate self with result, code: ${err.code}, msg: ${err.message}`);
            });

          this.storage?.clear();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { UIExtensionContentSession, common } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';
import { Entry, Column, Component, Button, RelativeContainer, LocalStorage } from '@kit.ArkUI';

@Entry()
@Component
struct Index {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined =
    this.storage?.get<UIExtensionContentSession>('session');

  build() {
    RelativeContainer() {
      Button('TerminateSelfWithResult')
        .onClick(() => {
          let abilityResult: common.AbilityResult = {
            resultCode: 0,
            want: {
              bundleName: 'com.ohos.uiextensioncontentsession',
              parameters: {
                'result': 123456
              } as Record<string, RecordData>
            }
          };

          this.session?.terminateSelfWithResult(abilityResult)
            .then(() => {
              console.info(`Succeeded in terminating self with result.`);
            })
            .catch((error) => {
              let err = error as BusinessError;
              console.error(`Failed to terminate self with result, code: ${err.code}, msg: ${err.message}`);
            });

          this.storage?.clear();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

