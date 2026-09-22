# Want

```TypeScript
export default class Want
```

Want is a carrier for information transfer between objects (application components). A typical scenario is when a UIAbility (for example, UIAbility A) needs to launch another UIAbility (for example, UIAbility B) and pass some data along. In this case, a Want can be used as the medium. For example, in the **want** parameter of the **startAbility** API, you can specify the target ability using the **abilityName** field or include additional data via the **parameters** field.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityBase

## Modules to Import

```TypeScript
import { Want } from '@kit.AbilityKit';
```

## abilityName

```TypeScript
abilityName?: string
```

Ability name of the application. It represents the ability name of the target application in the application launch scenario. If both **bundleName** and **abilityName** are specified in a Want object, the Want object can match a specific ability. The value of **abilityName** must be unique in an application.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## action

```TypeScript
action?: string
```

Action to take, such as viewing and sharing application details. In implicit Want, you can define this field and use it together with **uri** or **parameters** to specify the operation to be performed on the data. For details about the definition and matching rules of implicit Want, see [Matching Rules of Explicit Want and Implicit Want](../../../application-models/explicit-implicit-want-mappings.md).

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## bundleName

```TypeScript
bundleName?: string
```

Bundle name of the application. It represents the bundle name of the target application in the application launch scenario.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## deviceId

```TypeScript
deviceId?: string
```

Device ID. It indicates the device ID of the target application in the application launch scenario. If not specified, it defaults to the current device.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## entities

```TypeScript
entities?: Array<string>
```

Additional category information (such as browser and video player) of the ability. It is a supplement to the **action** field for implicit Want. and is used to filter ability types.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## fds

```TypeScript
readonly fds?: Record<string, number>
```

File descriptor (FD). The FD written by the launcher in the application launch scenario is set to this parameter.

This API can be used in atomic services since API version 15.

**Type:** Record&lt;string, number&gt;

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Ability.AbilityBase

## flags

```TypeScript
flags?: number
```

How the Want object will be handled. The value is of the enumeration type [Flags](arkts-ability-wantconstant-flags-e.md). A numeric value should be passed by default.

For example, if the value is 0x00000001 (**wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION**), the receiver is temporarily granted the permission to read the data pointed to by the URI.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## moduleName

```TypeScript
moduleName?: string
```

Module name of the application. It represents the module name of the target application in the application launch scenario.

**NOTE:** 

If the ability belongs to a [HAR](../../../quick-start/har-package.md) module, **moduleName** must be set to the name of the [HAP](../../../quick-start/hap-package.md) or [HSP](../../../quick-start/in-app-hsp.md) module that depends on this HAR.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## parameters

```TypeScript
parameters?: Record<string, Object>
```

List of parameters in the Want object.

1. The values of the following keys are assigned by the system. Manual settings do not take effect, since the
system automatically changes the values to the actual values during data transfer.

- **ohos.aafwk.param.callerPid**: PID of the caller. The value is a string.  
- **ohos.aafwk.param.callerBundleName**: bundle name of the caller. The value is a string.  
- **ohos.aafwk.param.callerAbilityName**: ability name of the caller. The value is a string.  
- **ohos.aafwk.param.callerNativeName**: process name of the caller when the native method is called. The value is  
a string.  
- **ohos.aafwk.param.callerAppId**: appId of the caller. The value is a string.  
- **ohos.aafwk.param.callerAppIdentifier**: appIdentifier of the caller. The value is a string.  
- **ohos.aafwk.param.callerToken**: token of the caller. The value is a string.  
- **ohos.aafwk.param.callerUid**: UID in [BundleInfo](arkts-ability-bundleinfo-i.md), that is,  
the application's UID in the bundle information. The value is a number.  
- **ohos.param.callerAppCloneIndex**: clone index of the caller. The value is of the numeric type.  
- **component.startup.newRules**: enabled status of the new control rule. The value is of the Boolean type.  
- **moduleName**: module name of the caller. The value is a string.  
- **ohos.ability.params.abilityRecoveryRestart**: support for ability restart upon fault recovery. The value is of  
the Boolean type.  
- **ohos.extra.param.key.showMode**: mode to show the atomic service startup. The value is an enumerated value of wantConstant.ShowMode.

**NOTE:** 

In cross-device scenarios, the following fields do not take effect and cannot be used for identity or permission verification: **ohos.aafwk.param.callerPid**, **ohos.aafwk.param.callerToken**, and **ohos.aafwk.param.callerUid**.

2. Certain keys are defined by the system, and their values need to be manually assigned. For details about the
keys and their values, see wantConstant.Params.
3. In addition to the foregoing cases, applications may further agree on the key-value pairs to transfer.

**NOTE:** 

For details about the constants of **Params** in **want**, see [wantConstant](arkts-ability-app-ability-wantconstant.md).

Note that a maximum of 100 KB data that can be transferred by using **WantParams**. If the data volume exceeds 100 KB, transfer data in WriteRawDataBuffer or [uri](../../apis-arkts/arkts-apis/arkts-arkts-uri.md) mode.

The values of **parameters** must be of the following basic data types: String, Number, Boolean, Object, undefined, and null. Functions in an object cannot be transferred.

**Type:** Record&lt;string, Object&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## type

```TypeScript
type?: string
```

MIME type, that is, the type of the file to open, for example, **'text/xml'** and **'image/*'**. For details about the MIME type definition, see [Media Types](https://www.iana.org/assignments/media-types/media-types.xhtml?utm_source=ld246.com).

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## uri

```TypeScript
uri?: string
```

URI, which is used with **type** to specify the data type to be processed in the application launch scenario. If **uri** is specified in a Want, the Want will match the specified URI information, including **scheme**, **schemeSpecificPart**, **authority**, and **path**.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

**Examples**

Basic usage: called in a UIAbility object, as shown in the example below. For details about how to obtain the context, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
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

Currently, the following data types are supported: string, number, Boolean, object, array, and file descriptor (FD).

String

```TypeScript
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

Number

```TypeScript
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

Boolean

```TypeScript
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

Object

```TypeScript
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

Array

```TypeScript
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

FD

```TypeScript
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

```TypeScript
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

parameters usage: parameters carries custom parameters. It is transferred by UIAbilityA to UIAbilityB and obtained from UIAbilityB.

```TypeScript
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

```TypeScript
// (2) If the UIAbilityB instance is started for the first time, it enters the onCreate lifecycle.
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

class UIAbilityB extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info(`onCreate, want parameters: ${want.parameters?.developerParameters}`);
  }
}
```

Usage of the keys of [wantConstant](arkts-ability-app-ability-wantconstant.md) in parameters.

```TypeScript
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
