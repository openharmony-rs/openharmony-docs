# @ohos.app.ability.Want (Want)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=84474fd67db0a73a342cb372b4641b984bfe4ab7 translatedAt=2026-09-03T10:39:30.621Z pushedAt=2026-09-05T10:47:30.459Z -->

Want is a carrier for information transfer between objects (application components).

A typical scenario is when a UIAbility (for example, UIAbility A) needs to launch another UIAbility (for example, UIAbility B) and pass some data along. In this case, a Want can be used as the medium. For example, in the **want** parameter of the **startAbility** API, you can specify the target ability using the **abilityName** field or include additional data via the **parameters** field.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Constraints

Due to IPC limitations, the **Want** field passed when launching an ability must meet the following requirements.

- Starting from API version 23, the maximum data supported in the **Want** field is 200 KB.
- In API version 22 and earlier, the maximum data supported in the **Want** field is 100 KB.

## Modules to Import

```ts
import { Want } from '@kit.AbilityKit';
```

## Want

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityBase

| Name       | Type                | Read-Only| Optional| Description                                                        |
| ----------- | -------------------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| deviceId    | string               | No| Yes| Device ID. It indicates the device ID of the target application in the application launch scenario. If not specified, it defaults to the current device.              |
| bundleName   | string               | No| Yes | Bundle name of the application. It represents the bundle name of the target application in the application launch scenario.|
| moduleName | string | No| Yes| Module name of the application. It represents the module name of the target application in the application launch scenario.<br>**NOTE**<br> If the ability belongs to a [HAR](../../quick-start/har-package.md) module, **moduleName** must be set to the name of the [HAP](../../quick-start/hap-package.md) or [HSP](../../quick-start/in-app-hsp.md) module that depends on this HAR.|
| abilityName  | string               | No | Yes  | Name of the Ability component of the application. In the application startup scenario, indicates the name of the Ability component of the launched party. If both bundleName and abilityName are specified in the Want, the Want can directly match the specified Ability. The abilityName must be unique within an application. |
| action | string               | No| Yes | Action to take, such as viewing and sharing application details. In implicit Want, you can define this field and use it together with **uri** or **parameters** to specify the operation to be performed on the data. For details about the definition and matching rules of implicit Want, see [Matching Rules of Explicit Want and Implicit Want](../../application-models/explicit-implicit-want-mappings.md).     |
| entities | Array\<string> | No| Yes| Additional category information (such as browser and video player) of the ability. It is a supplement to the **action** field for implicit Want. and is used to filter ability types.|
| uri | string | No| Yes| URI, which is used with **type** to specify the data type to be processed in the application launch scenario. If **uri** is specified in a Want, the Want will match the specified URI information, including **scheme**, **schemeSpecificPart**, **authority**, and **path**.|
| type | string | No | Yes | Indicates the MIME type description, that is, the type of the file to open. It is mainly used by the file manager to open files, for example, 'text/xml' and 'image/*'. For details about MIME, see [Media Types](https://www.iana.org/assignments/media-types/media-types.xhtml?utm_source=ld246.com). |
| parameters   | Record\<string, Object> | No | Yes  | Indicates the WantParams description.<br />1. The following keys are assigned by the system. Manual modification by developers does not take effect, and the system automatically changes them to the actual values during data transfer.<br />- ohos.aafwk.param.callerPid: indicates the PID of the launching party. Value is of string type.<br />- ohos.aafwk.param.callerBundleName: indicates the bundle name of the launching party. Value is of string type.<br />- ohos.aafwk.param.callerAbilityName: indicates the ability name of the launching party. Value is of string type.<br />- ohos.aafwk.param.callerNativeName: indicates the process name of the launching party in a native call. Value is of string type.<br />- ohos.aafwk.param.callerAppId: indicates the AppId information of the launched application. Value is of string type.<br />- ohos.aafwk.param.callerAppIdentifier: indicates the AppIdentifier information of the launched application. Value is of string type.<br />- ohos.aafwk.param.callerToken: indicates the token of the launching party. Value is of string type.<br />- ohos.aafwk.param.callerUid: indicates the UID in [BundleInfo](js-apis-bundleManager-bundleInfo.md#bundleinfo-1), that is, the UID of the application in the application package. Value is of number type.<br />- ohos.param.callerAppCloneIndex: indicates the clone index of the launching application. Value is of number type.<br />- component.startup.newRules: indicates whether to enable the new control rules. Value is of boolean type.<br />- moduleName: indicates the module name of the launched party. Value is of string type.<br />- ohos.ability.params.abilityRecoveryRestart: indicates whether the current Ability is restarted due to fault recovery. Value is of boolean type.<br />- ohos.extra.param.key.showMode: indicates the display mode for launching an Atomic Service. Value is of enum type [wantConstant.ShowMode](js-apis-app-ability-wantConstant.md#showmode12).<br/><br/>**Note:**<br/>In cross-device scenarios, the following three fields do not take effect and cannot be used for identity or permission verification: ohos.aafwk.param.callerPid, ohos.aafwk.param.callerToken, and ohos.aafwk.param.callerUid.<br /><br />2. Some keys defined by the system are provided for developers to assign values as needed. For details about the specific keys and their descriptions, see [wantConstant.Params](js-apis-app-ability-wantConstant.md#params)<!--Del--> and [wantConstant.Params (system applications only)](js-apis-app-ability-wantConstant-sys.md#params)<!--DelEnd-->.<br /><br />3. In addition to the preceding cases, applications can agree on key-value pairs to be passed between them.<br /><br />**Note:**<br/>For details about the constants for Params operations of Want, see [wantConstant](js-apis-app-ability-wantConstant.md).<br/>Note that the maximum amount of data that WantParams supports for transfer follows the [Want Constraints](#constraints). When the data amount exceeds the limit, use [WriteRawDataBuffer](../apis-ipc-kit/js-apis-rpc.md#writerawdatabuffer11) or [uri](../apis-arkts/js-apis-uri.md) to transfer data.<br/>The Value of parameters supports only the basic data types: String, Number, Boolean, Object, undefined, and null. Functions inside Object are not supported. |
| flags | number | No| Yes| How the Want object will be handled. The value is of the enumeration type [Flags](js-apis-app-ability-wantConstant.md#flags). A numeric value should be passed by default.<br>For example, if the value is 0x00000001 (**wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION**), the receiver is temporarily granted the permission to read the data pointed to by the URI.|
| fds<sup>15+</sup> | Record\<string, number> | Yes | Yes | Indicates the set of file descriptors. In the application startup scenario, when the launching party passes a Want through [startAbility](js-apis-inner-application-uiAbilityContext.md#startability), the file descriptors must be passed in parameters as fixed key-value pairs. The launched party can obtain the file descriptors through this field. For details about how to use it, see the "File Descriptor (FD)" example.<br>**Atomic Service API**: Since API version 15, this API is supported in Atomic Services. |

**Example**

- Basic usage: called in a UIAbility object, as shown in the example below. For details about how to obtain the context, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```ts
  import { UIAbility, Want } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';

  export default class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage): void {
      let want: Want = {
        deviceId: '', // An empty deviceId indicates the local device.
        bundleName: 'com.example.myapplication',
        abilityName: 'FuncAbility',
        moduleName: 'entry' // moduleName is optional.
      };

      this.context.startAbility(want, (err: BusinessError) => {
        if (err.code) {
          // Start an ability explicitly. The bundleName, abilityName, and moduleName parameters work together to uniquely identify an ability.
          console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
        }
      });
    }
  }
  ```

- Currently, the following data types are supported: string, number, Boolean, object, array, and file descriptor (FD).

    * String
        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                keyForString: 'str',
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```
    * Number
        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                keyForInt: 100,
                keyForDouble: 99.99,
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```
    * Boolean
        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                keyForBool: true,
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```
    * Object
        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                keyForObject: {
                  keyForObjectString: 'str',
                  keyForObjectInt: -200,
                  keyForObjectDouble: 35.5,
                  keyForObjectBool: false,
                },
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```
    * Array

        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                keyForArrayString: ['str1', 'str2', 'str3'],
                keyForArrayInt: [100, 200, 300, 400],
                keyForArrayDouble: [0.1, 0.2],
                keyForArrayObject: [{ obj1: 'aaa' }, { obj2: 100 }],
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```

    * FD

        ```ts
        // Launcher: Pass the file descriptor in parameters in the fixed key-value pair format {'type':'FD','value':fd}.
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';
        import { fileIo } from '@kit.CoreFileKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let fd: number = 0;

            try {
              fd = fileIo.openSync('/data/storage/el2/base/haps/pic.png').fd;
            } catch (err) {
              let code = (err as BusinessError).code;
              let message = (err as BusinessError).message;
              console.error(`Failed to openSync. Code: ${code}, message: ${message}`);
            }
            let want: Want = {
              deviceId: '', // An empty deviceId indicates the local device.
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              moduleName: 'entry', // moduleName is optional.
              parameters: {
                // keyFd is a custom key. The launched party uses this key to find the corresponding value.
                // {'type':'FD','value':fd} is a fixed key-value pair, where fd is the file descriptor passed by the developer.
                'keyFd': { 'type': 'FD', 'value': fd }
              }
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```

        ```ts
        // Launched party: Obtain the file descriptor passed by the launcher through want.fds.
        import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';
        import { fileIo } from '@kit.CoreFileKit';

        export default class FuncAbility extends UIAbility {
          onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
            let fd: number = -1;
            // Obtain the file descriptor passed by the launcher from want.fds. The keyFd must be consistent with the key used by the launcher when passing it.
            const fds = want.fds;
            if (fds && fds.keyFd !== undefined) {
              fd = fds.keyFd;
            }
            // Check whether the file descriptor is valid (a non-negative integer indicates validity). If it is invalid, log an error and exit immediately to avoid a crash caused by using an invalid fd later.
            if (fd < 0) {
              console.error(`Failed to get fd from want.fds`);
              return;
            }
            // ...
            fileIo.closeSync(fd); // Close the file descriptor after use to avoid file descriptor leakage.
          }
        }
        ```

    * **parameters** usage: **parameters** carries custom parameters. It is transferred by UIAbilityA to UIAbilityB and obtained from UIAbilityB.

        ```ts
        // (1) UIAbilityA starts UIAbilityB through startAbility.
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'UIAbilityB',
              parameters: {
                developerParameters: 'parameters',
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```

        ```ts
        // (2) If the UIAbilityB instance is started for the first time, it enters the onCreate lifecycle.
        import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

        class UIAbilityB extends UIAbility {
          onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
            console.info(`onCreate, want parameters: ${want.parameters?.developerParameters}`);
          }
        }
        ```
    * Usage of the keys of [wantConstant](js-apis-app-ability-wantConstant.md) in **parameters**.

        ```ts
        import { UIAbility, Want, wantConstant } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                [wantConstant.Params.CONTENT_TITLE_KEY]: 'contentTitle',
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```
    * Obtain the information about the party that starts the UIAbility from **parameters**.

      For details, see [Obtaining Information About the UIAbility Launcher](../../application-models/uiability-usage.md#obtaining-information-about-the-uiability-launcher).
