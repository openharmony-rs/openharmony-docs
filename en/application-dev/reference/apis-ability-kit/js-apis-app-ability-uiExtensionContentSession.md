# @ohos.app.ability.UIExtensionContentSession (UIExtensionAbility UI Operation Class)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c; @xuzhihao666-->
<!--Designer: @xhz-sz-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

UIExtensionContentSession is the UI operation class for the [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md). It provides control over page loading and allows configuration of the window privacy mode of the host application (application that starts the UIExtensionAbility). When the host application starts a specific UIExtensionAbility, the system creates a UIExtensionContentSession object and passes it back via the [onSessionCreate](js-apis-app-ability-uiExtensionAbility.md#onsessioncreate) callback. Each UIExtensionAbility corresponds to one UIExtensionContentSession object, and these objects operate independently without interfering with each other.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { UIExtensionContentSession } from '@kit.AbilityKit';
```

## UIExtensionContentSession

UIExtensionContentSession is the UI operation class for the UIExtensionAbility. It provides control over page loading and allows configuration of the window privacy mode of the host application.

### loadContent

loadContent(path: string, storage?: LocalStorage): void

Loads a page for the [UIExtensionAbility](./js-apis-app-ability-uiExtensionAbility.md), with state properties passed to the page through [LocalStorage](../../ui/state-management/arkts-localstorage.md). This API is used to load a page in the [onSessionCreate](./js-apis-app-ability-uiExtensionAbility.md#onsessioncreate) lifecycle of the UIExtensionAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| path | string | Yes| Path of the page to load. The path is configured using the [pages](../../quick-start/module-configuration-file.md#pages) tag in the [module.json5](../../quick-start/module-configuration-file.md) file.|
| storage | [LocalStorage](../../ui/state-management/arkts-localstorage.md) | No| A page-level UI state storage unit, which is used to pass state properties to the page.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 16000050 | Internal error. |

**Example**

```ts
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
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

### loadContentByName<sup>18+</sup>

loadContentByName(name: string, storage?: LocalStorage): void

Loads a [named route](../../ui/arkts-routing.md#named-route) page for a [UIExtensionAbility](./js-apis-app-ability-uiExtensionAbility.md), with state properties passed to the page through [LocalStorage](../../ui/state-management/arkts-localstorage.md). This API is used to load a named route page in the [onSessionCreate](./js-apis-app-ability-uiExtensionAbility.md#onsessioncreate) lifecycle of the UIExtensionAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------ |
| name | string | Yes| Name of the named route page.|
| storage | [LocalStorage](../../ui/state-management/arkts-localstorage.md) | No| A page-level UI state storage unit, which is used to pass state properties to the page.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------ | ------ |
| 16000050 | Internal error. |

**Example**

Implementation of the UIExtensionAbility:
```ts
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
import { UIExtensionContentSession, ShareExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import './pages/UIExtensionPage'; // Import the named route page. The ./pages/UIExtensionPage.ets file is used as an example in the sample code. Change the path and file name to the actual ones during your development.

export default class ShareExtAbility extends ShareExtensionAbility {
  // Other lifecycles and implementations

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('session', session);

    let name: string = 'UIExtPage'; // Name of the named route page.
    try {
      session.loadContentByName(name, storage);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`Failed to load content by name ${name}, code: ${code}, msg: ${message}`);
    }
  }

  // Other lifecycles and implementations
}
```

Implementation of the named route page loaded by the UIExtensionAbility:
```ts
// Implementation of the ./pages/UIExtensionPage.ets file.
import { UIExtensionContentSession } from '@kit.AbilityKit';

@Entry ({routeName: 'UIExtPage'}) // Use routeName to define the name of the named route page.
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

### terminateSelf

terminateSelf(callback: AsyncCallback&lt;void&gt;): void

Destroys this UIExtensionAbility and closes the corresponding window of the host application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
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

### terminateSelf

terminateSelf(): Promise&lt;void&gt;

Destroys this UIExtensionAbility and closes the corresponding window of the host application. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

```ts
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

### terminateSelfWithResult

terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback&lt;void&gt;): void

Destroys this UIExtensionAbility, closes the corresponding window of the host application, and returns the result to the host application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| parameter | [AbilityResult](js-apis-inner-ability-abilityResult.md) | Yes| Information returned to the host application.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
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

### terminateSelfWithResult

terminateSelfWithResult(parameter: AbilityResult): Promise&lt;void&gt;

Destroys this UIExtensionAbility, closes the corresponding window of the host application, and returns the result to the host application. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| parameter | [AbilityResult](js-apis-inner-ability-abilityResult.md) | Yes| Information returned to the host application.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
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

### setWindowPrivacyMode

setWindowPrivacyMode(isPrivacyMode: boolean): Promise&lt;void&gt;

Enables or disables the window privacy mode of the host application. A window in privacy mode cannot be captured or recorded. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Required permissions**: ohos.permission.PRIVACY_WINDOW

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| isPrivacyMode | boolean | Yes| Whether to enable the privacy mode. **true** to enable, **false** otherwise.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
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
        .catch((err: BusinessError) => {
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

### setWindowPrivacyMode

setWindowPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback&lt;void&gt;): void

Enables or disables the window privacy mode of the host application. A window in privacy mode cannot be captured or recorded. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Required permissions**: ohos.permission.PRIVACY_WINDOW

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| isPrivacyMode | boolean | Yes| Whether to enable the privacy mode. **true** to enable, **false** otherwise.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the setting is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
import { UIExtensionContentSession, ShareExtensionAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class ShareExtAbility extends ShareExtensionAbility {
  // ...

  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let isPrivacyMode: boolean = true;
    try {
      session.setWindowPrivacyMode(isPrivacyMode, (err: BusinessError) => {
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

### startAbilityByType<sup>11+</sup>

startAbilityByType(type: string, wantParam: Record<string, Object>, abilityStartCallback: AbilityStartCallback, callback: AsyncCallback\<void>): void

Implicitly starts a given type of UIExtensionAbility. This API uses an asynchronous callback to return the result. It can be called only by applications running in the foreground.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the UIExtensionAbility. For details, see [Starting an Application of the Specified Type](../../application-models/start-intent-panel.md#matching-rules).|
| wantParam | Record<string, Object> | Yes| Parameters passed for starting the UIExtensionAbility.|
| abilityStartCallback | [AbilityStartCallback](js-apis-inner-application-abilityStartCallback.md) | Yes| Execution result of starting the UIExtensionAbility.|
| callback | AsyncCallback\<void> | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 16000050 | Internal error. |

**Example**

```ts
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
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

### startAbilityByType<sup>11+</sup>

startAbilityByType(type: string, wantParam: Record<string, Object>, abilityStartCallback: AbilityStartCallback): Promise\<void>

Implicitly starts a given type of UIExtensionAbility. This API uses a promise to return the result. It can be called only by applications running in the foreground.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the UIExtensionAbility. For details, see [Starting an Application of the Specified Type](../../application-models/start-intent-panel.md#matching-rules).|
| wantParam | Record<string, Object> | Yes| Parameters passed for starting the UIExtensionAbility.|
| abilityStartCallback | [AbilityStartCallback](js-apis-inner-application-abilityStartCallback.md) | Yes| Execution result of starting the UIExtensionAbility.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 16000050 | Internal error. |

**Example**

```ts
// The UIExtensionAbility class does not allow direct inheritance by third-party applications. The child class ShareExtensionAbility is used here as an example.
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

### getUIExtensionWindowProxy<sup>12+</sup>

getUIExtensionWindowProxy(): uiExtension.WindowProxy

Obtains the window proxy of this UIExtensionAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type| Description|
| -------- | -------- |
| [uiExtension.WindowProxy](../apis-arkui/js-apis-arkui-uiExtension.md#windowproxy) | Window proxy of the host application.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| -------- | -------- |
| 16000050 | Internal error. |

**Example**

```ts
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
