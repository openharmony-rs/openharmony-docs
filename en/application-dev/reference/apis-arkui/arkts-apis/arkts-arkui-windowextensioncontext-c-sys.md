# WindowExtensionContext (System API)

```TypeScript
declare class WindowExtensionContext extends ExtensionContext
```

The WindowExtensionContext module provides the context environment for the WindowExtensionAbility. It inherits from [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md).

The module provides the capabilities of the [WindowExtensionAbility](arkts-arkui-application-windowextensionability-windowextensionability-c-sys.md), including starting the ability.

> **NOTE:** 
> 
> - This module is deprecated since API version 21. You are advised to use [UIExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiextensioncontext-c.md) instead.
> 
> - The APIs provided by this module are system APIs.
> 
> - The APIs of this module can be used only in the stage model.

**Inheritance/Implementation:** WindowExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**Since:** 9

**Deprecated since:** 21

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## startAbility

```TypeScript
startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

Starts an ability. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-application-want-want-depr-c.md) | Yes | Want information about the target ability. |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | Yes | Parameters used for starting the ability. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { WindowExtensionAbility } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, StartOptions } from '@kit.AbilityKit';

class WindowExtAbility extends WindowExtensionAbility {
  
  onConnect() {
    let want: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'MainAbility'
    };
    let options: StartOptions = {
      windowMode: 102
    };

    try {
      this.context.startAbility(want, options, (error: BusinessError) => {
        let message = (error as BusinessError).message;
        let errCode = (error as BusinessError).code;
        if (errCode) {
          // Process service logic errors.
          console.error(`startAbility failed, error.code: ${errCode}, error.message: ${message}`);
          return;
        }
        // Carry out normal service processing.
        console.info('startAbility succeed');
      });
    } catch (paramError) {
      // Process input parameter errors.
      let message = (paramError as BusinessError).message;
      let errCode = (paramError as BusinessError).code;
      console.error(`error.code: ${errCode}, error.message: ${message}`);
    }
  }
}
```

<a id="startability-1"></a>

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

Starts an ability. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 21

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-application-want-want-depr-c.md) | Yes | Want information about the target ability, such as the ability name and bundle name. |
| options | [StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Parameters used for starting the ability. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { WindowExtensionAbility } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, StartOptions } from '@kit.AbilityKit';

class WindowExtAbility extends WindowExtensionAbility {

  onConnect() {
    let want: Want = {
      bundleName: 'com.example.myapp',
      abilityName: 'MainAbility'
    };
    let options: StartOptions = {
      windowMode: 102,
    };

    try {
      this.context.startAbility(want, options)
        .then(() => {
          // Carry out normal service processing.
          console.info('startAbility succeed');
        })
        .catch((error: BusinessError) => {
          // Process service logic errors.
          let message = (error as BusinessError).message;
          let errCode = (error as BusinessError).code;
          console.error(`startAbility failed, error.code: ${errCode}, error.message: ${message}`);
        });
    } catch (paramError) {
      // Process input parameter errors.
      let message = (paramError as BusinessError).message;
      let errCode = (paramError as BusinessError).code;
      console.error(`error.code: ${errCode}, error.message: ${message}`);
    }
  }
}
```
