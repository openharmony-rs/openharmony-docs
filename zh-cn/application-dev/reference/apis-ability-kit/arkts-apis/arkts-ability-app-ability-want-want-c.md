# Want

Want是对象间信息传递的载体，可以用于应用组件间的信息传递。 其典型应用场景之一是，当UIAbilityA启动UIAbilityB、并需要传入一些数据时，可使用Want作为载体。例如在startAbility接口的入参want中，可以通过abilityName指定启动的目标Ability，也可以 通过parameters等字段携带其他数据。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityBase

## 导入模块

```TypeScript
import { Want } from '@kit.AbilityKit';
```

## abilityName

```TypeScript
abilityName?: string
```

应用的Ability组件名。在应用启动场景中表示被拉起方的Ability组件名。如果在Want中该字段同时指定了BundleName和AbilityName，则Want可以直接匹配到指定的Ability。AbilityName需要 在一个应用的范围内保证唯一。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## action

```TypeScript
action?: string
```

表示要执行的通用操作（如：查看、分享、应用详情）。在隐式Want中，开发者可以定义该字段，配合uri或parameters来表示对数据执行的操作。隐式Want定义及匹配规则请参见 [显式Want与隐式Want匹配规则](../../../application-models/explicit-implicit-want-mappings.md)。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## bundleName

```TypeScript
bundleName?: string
```

应用包名。在应用启动场景中表示被拉起方的应用包名。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## deviceId

```TypeScript
deviceId?: string
```

设备ID。在应用启动场景中表示被拉起方的设备ID，如果未设置该字段，则表示指定当前设备。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## entities

```TypeScript
entities?: Array<string>
```

表示目标Ability额外的类别信息（如：浏览器、视频播放器）。在隐式Want中是对action字段的补充。在隐式Want中，开发者可以定义该字段，来过滤匹配Ability类型。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## fds

```TypeScript
readonly fds?: Record<string, number>
```

表示文件描述符的集合。在应用启动场景中，拉起方通过 startAbility传递Want时， 需在parameters中以固定键值对形式传入文件描述符，被拉起方可通过该字段获取文件描述符，具体使用方式见“文件描述符（FD）”示例。从API version 15开始，该接口支持在原子化服务中使用。

**类型：** Record&lt;string, number&gt;

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## flags

```TypeScript
flags?: number
```

表示处理Want的方式。值为枚举类型[Flags](arkts-ability-wantconstant-flags-e.md)，默认传数字。例如取值为0x00000001（即wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION）表示临时授予接收方读取该URI指向的数据的权限。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## moduleName

```TypeScript
moduleName?: string
```

应用模块名。在应用启动场景中表示被拉起方的应用模块名。  
**说明：**若待启动的Ability所属的模块为[HAR](../../../quick-start/har-package.md)，则moduleName需为依赖该HAR的 [HAP](../../../quick-start/hap-package.md)/[HSP](../../../quick-start/in-app-hsp.md)的moduleName。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## parameters

```TypeScript
parameters?: Record<string, Object>
```

表示WantParams描述。一、以下Key均由系统赋值，开发者手动修改也不会生效，系统在数据传递时会自动修改为实际值。  
- ohos.aafwk.param.callerPid：表示拉起方的pid，值为字符串类型。  
- ohos.aafwk.param.callerBundleName：表示拉起方的BundleName，值为字符串类型。  
- ohos.aafwk.param.callerAbilityName：表示拉起方的AbilityName，值为字符串类型。  
- ohos.aafwk.param.callerNativeName：表示native调用时拉起方的进程名，值为字符串类型。  
- ohos.aafwk.param.callerAppId：表示拉起应用的AppId信息，值为字符串类型。  
- ohos.aafwk.param.callerAppIdentifier：表示拉起应用的AppIdentifier信息，值为字符串类型。  
- ohos.aafwk.param.callerToken：表示拉起方的token，值为字符串类型。  
- ohos.aafwk.param.callerUid：表示[BundleInfo](arkts-ability-bundleinfo-i.md)中的uid，应用包里应用程序的uid，值为数  
值类型。  
- ohos.param.callerAppCloneIndex：表示拉起方应用的分身索引，值为数值类型。  
- component.startup.newRules：表示是否启用新的管控规则，值为布尔类型。  
- moduleName：表示被拉起方的moduleName，值为字符串类型。  
- ohos.ability.params.abilityRecoveryRestart：表示当前Ability是否发生了故障恢复重启，值为布尔类型。  
- ohos.extra.param.key.showMode：表示拉起原子化服务的展示模式，值为枚举类型  
wantConstant.ShowMode。  
**说明：**在跨端场景中，以下三个字段不生效，不可用于身份或权限校验：ohos.aafwk.param.callerPid、ohos.aafwk.param.callerToken、ohos.aafwk.param.callerUid。二、提供了一些由系统定义、开发者按需赋值的Key。具体的key值与对应说明详见 wantConstant.Params。三、除了上述情况，应用间还可以相互约定传入的键值对。
**说明：**want的Params操作的常量的具体信息请参考[wantConstant](arkts-app-ability-wantconstant.md)。需注意，WantParams支持传输的最大数据量遵循Want约束限制。当数据量超过该限制时，请使用 WriteRawDataBuffer或[uri](../../apis-arkts/arkts-apis/arkts-uri.md)的方式进行数 据传输。parameters的Value值仅支持基本数据类型：String、Number、Boolean、Object、undefined和null，不支持传递Object内部的function。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## type

```TypeScript
type?: string
```

表示MIME type类型描述，打开文件的类型，主要用于文管打开文件。比如：'text/xml' 、 'image/*'等，MIME定义请参见 [Media Types](https://www.iana.org/assignments/media-types/media-types.xhtml?utm_source=ld246.com)。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## uri

```TypeScript
uri?: string
```

统一资源标识符，一般在应用启动场景中配合type使用，指明待处理的数据类型。如果在Want中指定了uri，则Want将匹配指定的Uri信息，包括`scheme`、`schemeSpecificPart`、`authority`和` path`信息。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

**示例**

基础用法：在UIAbility对象中调用，示例中的context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { UIAbility, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    let want: Want = {
      deviceId: '', // deviceId为空表示本设备
      bundleName: 'com.example.myapplication',
      abilityName: 'FuncAbility',
      moduleName: 'entry' // moduleName非必选
    };

    this.context.startAbility(want, (err: BusinessError) => {
      if (err.code) {
        // 显式拉起Ability，通过bundleName、abilityName和moduleName可以唯一确定一个Ability
        console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
      }
    });
  }
}
```

字符串（String）

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

数字（Number）

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

布尔（Boolean）

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

对象（Object）

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

数组（Array）

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

文件描述符（FD）

```TypeScript
// 拉起方：在parameters中以{'type':'FD','value':fd}的固定键值对形式传入文件描述符
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
      deviceId: '', // deviceId为空表示本设备
      bundleName: 'com.example.myapplication',
      abilityName: 'FuncAbility',
      moduleName: 'entry', // moduleName非必选
      parameters: {
        // keyFd为自定义的key，被拉起方通过该key值查找对应value
        // {'type':'FD','value':fd}是固定键值对，其中fd为开发者传递的文件描述符
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
// 被拉起方：通过want.fds获取拉起方传入的文件描述符
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';

export default class FuncAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let fd: number = -1;
    // 从want.fds中获取拉起方传入的文件描述符，keyFd需与拉起方传入时使用的key保持一致
    const fds = want.fds;
    if (fds && fds.keyFd !== undefined) {
      fd = fds.keyFd;
    }
    // 校验文件描述符是否有效（非负整数表示有效），若无效则记录错误并立即退出，避免后续使用非法fd导致崩溃
    if (fd < 0) {
      console.error(`Failed to get fd from want.fds`);
      return;
    }
    // ...
    fileIo.closeSync(fd); // 使用完毕后关闭文件描述符，避免文件描述符泄漏
  }
}
```

parameters参数用法：parameters携带开发者自定义参数，由UIAbilityA传递给UIAbilityB，并在UIAbilityB中进行获取。

```TypeScript
// (1) UIAbilityA通过startAbility启动UIAbilityB
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
// (2) 以UIAbilityB实例首次启动为例，会进入到UIAbilityB的onCreate生命周期
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

class UIAbilityB extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info(`onCreate, want parameters: ${want.parameters?.developerParameters}`);
  }
}
```

parameters参数中[wantConstant](arkts-app-ability-wantconstant.md)的Key的使用方法。

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
