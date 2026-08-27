# Want

Want是对象间信息传递的载体，可以用于应用组件间的信息传递。Want的使用场景之一是作为startAbility的参数，其包含了指定的启动目标，以及启动时需携带的相关数据，如bundleName和abilityName字段分别指明目 标Ability所在应用Bundle名称以及对应包内的Ability名称。当Ability A需要启动Ability B并传入一些数据时，可使用Want作为载体将这些数据传递给Ability B。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [Want/Want](arkts-ability-app-ability-want-want-c.md)

**系统能力：** SystemCapability.Ability.AbilityBase

## 导入模块

```TypeScript
```

## abilityName

```TypeScript
abilityName?: string
```

表示待启动的Ability名称。如果在Want中该字段同时指定了BundleName和AbilityName，则Want可以直接匹配到指定的Ability。AbilityName需要在一个应用的范围内保证唯一。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [abilityName](arkts-ability-app-ability-want-want-c.md#abilityname)

**系统能力：** SystemCapability.Ability.AbilityBase

## action

```TypeScript
action?: string
```

表示要执行的通用操作（如：查看、分享、应用详情）。在隐式Want中，您可以定义该字段，配合uri或parameters来表示对数据要执行的操作。具体参考： [action说明](arkts-ability-wantconstant-action-depr-e.md#action)。隐式Want定义及匹配规则参考： [显式Want与隐式Want匹配规则](../../../application-models/explicit-implicit-want-mappings.md)。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [action](arkts-ability-app-ability-want-want-c.md#action)

**系统能力：** SystemCapability.Ability.AbilityBase

## bundleName

```TypeScript
bundleName?: string
```

表示Bundle名称。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [bundleName](arkts-ability-app-ability-want-want-c.md#bundlename)

**系统能力：** SystemCapability.Ability.AbilityBase

## deviceId

```TypeScript
deviceId?: string
```

表示运行指定Ability的设备ID。如果未设置该字段，则表明指定本设备。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [deviceId](arkts-ability-app-ability-want-want-c.md#deviceid)

**系统能力：** SystemCapability.Ability.AbilityBase

## entities

```TypeScript
entities?: Array<string>
```

表示目标Ability额外的类别信息（如：浏览器、视频播放器）。在隐式Want中是对action字段的补充。在隐式Want中，您可以定义该字段，来过滤匹配Ability类型。具体参考： [entity说明](arkts-ability-wantconstant-entity-depr-e.md#entity)。

**类型：** Array&lt;string&gt;

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [entities](arkts-ability-app-ability-want-want-c.md#entities)

**系统能力：** SystemCapability.Ability.AbilityBase

## flags

```TypeScript
flags?: number
```

表示处理Want的方式。默认传数字，具体参考：[flags说明](arkts-ability-wantconstant-flags-depr-e.md#flags)。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [flags](arkts-ability-app-ability-want-want-c.md#flags)

**系统能力：** SystemCapability.Ability.AbilityBase

## parameters

```TypeScript
parameters?: { [key: string]: any }
```

表示WantParams描述，由开发者自行决定传入的键值对。默认会携带以下key值：ohos.aafwk.param.callerPid 表示拉起方的pid。ohos.aafwk.param.callerToken 表示拉起方的token。ohos.aafwk.param.callerUid 表示bundleInfo中的uid，应用包里应用程序的uid。  
- component.startup.newRules：表示是否启用新的管控规则。  
- moduleName：表示拉起方的模块名，该字段的值即使定义成其他字符串，在传递到另一端时会被修改为正确的值。  
- ohos.dlp.params.sandbox：表示dlp文件才会有。

**类型：** { [key: string]: any }

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [parameters](arkts-ability-app-ability-want-want-c.md#parameters)

**系统能力：** SystemCapability.Ability.AbilityBase

## type

```TypeScript
type?: string
```

表示MIME type类型描述，打开文件的类型，主要用于文管打开文件。比如：'text/xml' 、 'image/*'等，MIME定义参考：https://www.iana.org/assignments/media-types /media-types.xhtml?utm_source=ld246.com。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [type](arkts-ability-app-ability-want-want-c.md#type)

**系统能力：** SystemCapability.Ability.AbilityBase

## uri

```TypeScript
uri?: string
```

表示Uri描述。如果在Want中指定了Uri，则Want将匹配指定的Uri信息，包括scheme、schemeSpecificPart、authority和path信息。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [uri](arkts-ability-app-ability-want-want-c.md#uri)

**系统能力：** SystemCapability.Ability.AbilityBase

**示例**

基础用法（在UIAbility对象中调用，其中示例中的context为UIAbility的上下文对象）。

```TypeScript
import Want from '@ohos.application.Want';
import { BusinessError } from '@ohos.base';
import UIAbility from '@ohos.app.ability.UIAbility';
import AbilityConstant from '@ohos.app.ability.AbilityConstant';

let want: Want = {
'deviceId': '', // deviceId为空表示本设备
'bundleName': 'com.example.myapplication',
'abilityName': 'EntryAbility',
};
class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
      this.context.startAbility(want, (error: BusinessError) => {
        // 显式拉起Ability，通过bundleName、abilityName和moduleName可以唯一确定一个Ability
        if (error) {
          console.error(`StartAbility failed, error code: ${error.code}, error msg: ${error.message}.`);
        }
      });
    }
}
```

字符串（String）

```TypeScript
import Want from '@ohos.application.Want';

let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
  parameters: {
    keyForString: 'str',
  },
};
```

数字（Number）

```TypeScript
import Want from '@ohos.application.Want';

let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
  parameters: {
    keyForInt: 100,
    keyForDouble: 99.99,
  },
};
```

布尔（Boolean）

```TypeScript
import Want from '@ohos.application.Want';

let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
  parameters: {
    keyForBool: true,
  },
};
```

对象（Object）

```TypeScript
import Want from '@ohos.application.Want';

let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
  parameters: {
    keyForObject: {
      keyForObjectString: 'str',
      keyForObjectInt: -200,
      keyForObjectDouble: 35.5,
      keyForObjectBool: false,
    },
  },
};
```

数组（Array）

```TypeScript
import Want from '@ohos.application.Want';

let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
  parameters: {
    keyForArrayString: ['str1', 'str2', 'str3'],
    keyForArrayInt: [100, 200, 300, 400],
    keyForArrayDouble: [0.1, 0.2],
    keyForArrayObject: [{obj1: 'aaa'}, {obj2: 100}],
  },
};
```

文件描述符（FD）

```TypeScript
import fileIo from '@ohos.file.fs';
import Want from '@ohos.application.Want';
import { BusinessError } from '@ohos.base';
import AbilityConstant from '@ohos.app.ability.AbilityConstant';
import UIAbility from '@ohos.app.ability.UIAbility';

let fd: number = 0;
try {
  fd = fileIo.openSync('/data/storage/el2/base/haps/pic.png').fd;
} catch (e) {
  console.error(`OpenSync failed, error code: ${e.code}, error msg: ${e.message}.`);
}
let want: Want = {
  deviceId: '', // deviceId为空表示本设备
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
  parameters: {
    'keyFd': { 'type': 'FD', 'value': fd }
  }
};

class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    this.context.startAbility(want, (error: BusinessError) => {
      // 显式拉起Ability，通过bundleName、abilityName和moduleName可以唯一确定一个Ability
      if (error) {
        console.error(`StartAbility failed, error code: ${error.code}, error msg: ${error.message}.`);
      }
    });
  }
}
```
