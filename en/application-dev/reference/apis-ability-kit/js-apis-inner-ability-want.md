# Want

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T11:31:49.898Z pushedAt=2026-09-05T10:47:30.636Z -->

Want is a carrier for information transfer between objects and can be used to transfer information between application components. One of the use cases of Want is to serve as a parameter of [startAbility](js-apis-inner-application-uiAbilityContext.md#startability). It contains the specified launch target and the related data to carry during startup. For example, the bundleName and abilityName fields respectively indicate the bundle name of the application where the target Ability resides and the Ability name in the corresponding package. When Ability A needs to start Ability B and pass some data, Want can be used as a carrier to pass the data to Ability B.

> **NOTE**
> 
> The APIs of this module are supported since API version 6 and deprecated since API version 9. You are advised to use [@ohos.app.ability.Want](js-apis-app-ability-want.md) instead. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import Want from '@ohos.app.ability.Want';
```

## Attributes

**System capability**: SystemCapability.Ability.AbilityBase

| Name       | Type                | Read-Only| Optional| Description                                                        |
| ----------- | -------------------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| deviceId    | string               | No| Yes | ID of the device running the ability. If this field is unspecified, the local device is used.                               |
| bundleName   | string               | No| Yes | Bundle name.|
| abilityName  | string               | No | Yes  | Indicates the name of the ability to start. If both bundleName and abilityName are specified in the Want, the Want can directly match the specified ability. The abilityName must be unique within an application. |
| uri          | string               | No | Yes  | Indicates the URI. If a URI is specified in the Want, the Want matches the specified URI information, including scheme, schemeSpecificPart, authority, and path. |
| type         | string               | No| Yes | MIME type, that is, the type of the file to open, for example, **'text/xml'** and **'image/*'**. For details about the MIME type definition, see https://www.iana.org/assignments/media-types/media-types.xhtml?utm_source=ld246.com.  |
| flags        | number               | No| Yes | How the Want object will be handled. By default, numbers are passed in. For details, see [flags](js-apis-ability-wantConstant.md#flags).|
| action      | string               | No | Yes  | Indicates the common operation to perform, for example, view, share, and application details. In an implicit Want, you can define this field and use it with uri or parameters to indicate the operation to perform on the data. For details, see [Action](js-apis-ability-wantConstant.md#action). For details about the definition and matching rules of implicit Want, see [Matching Rules of Explicit Want and Implicit Want](../../application-models/explicit-implicit-want-mappings.md).                           |
| parameters   | { [key: string]: any } | No | Yes  | Indicates WantParams, which consists of key-value pairs defined by the developer. The following keys are carried by default:<br>ohos.aafwk.callerPid indicates the PID of the caller.<br>ohos.aafwk.param.callerToken indicates the token of the caller.<br>ohos.aafwk.param.callerUid indicates the UID in [bundleInfo](js-apis-bundle-BundleInfo.md#bundleinfodeprecated), that is, the UID of the application in the application package.<br>- component.startup.newRules: indicates whether to enable the new control rules.<br>- moduleName: indicates the module name of the caller. Even if this field is set to another string, it will be changed to the correct value when passed to the other end.<br>- ohos.dlp.params.sandbox: indicates that it is available only for DLP files.                                       |
| entities    | Array\<string>       | No| Yes | Additional category information (such as browser and video player) of the target ability. It is a supplement to **action** in implicit Want and is used to filter ability types.                                   |

**Example**

- Basic usage (called in a UIAbility object, where context in the example is the context object of the UIAbility)

  ```ts
  import AbilityConstant from '@ohos.app.ability.AbilityConstant';
  import UIAbility from '@ohos.app.ability.UIAbility';
  import Want from '@ohos.app.ability.Want';
  import { BusinessError } from '@ohos.base';

  let want: Want = {
    deviceId: '', // An empty deviceId indicates the local device.
    bundleName: 'com.example.myapplication',
    abilityName: 'EntryAbility',
    moduleName: 'entry' // moduleName is optional.
  };
  class MyAbility extends UIAbility{
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam){
      this.context.startAbility(want, (error: BusinessError) => {
        // Start an ability explicitly. The bundleName, abilityName, and moduleName parameters work together to uniquely identify an ability.
        console.error(`error.code = ${error.code}`);
      });
    }
  }
  ```

- Passes FD (file descriptor) data (called in a UIAbility object, where context in the example is the context object of the UIAbility)

  ```ts
  import fileIo from '@ohos.file.fs';
  import Want from '@ohos.app.ability.Want';
  import { BusinessError } from '@ohos.base';
  import AbilityConstant from '@ohos.app.ability.AbilityConstant';
  import UIAbility from '@ohos.app.ability.UIAbility';
  
  let fd: number = 0;
  try {
    fd = fileIo.openSync('/data/storage/el2/base/haps/pic.png').fd;
  } catch (e) {
    console.error(`OpenSync fail: ${JSON.stringify(e)}`);
  }

  let want: Want = {
    deviceId: '', // An empty deviceId indicates the local device.
    bundleName: 'com.example.myapplication',
    abilityName: 'EntryAbility',
    moduleName: 'entry', // moduleName is optional.
    parameters: {
      'keyFd': { 'type': 'FD', 'value': fd }
    }
  };

  class MyAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
      this.context.startAbility(want, (error: BusinessError) => {
        // Start an ability explicitly. The bundleName, abilityName, and moduleName parameters work together to uniquely identify an ability.
        console.error(`StartAbility failed, error.code: ${error.code}, err msg: ${error.message}.`);
      });
    }
  }
  ```
