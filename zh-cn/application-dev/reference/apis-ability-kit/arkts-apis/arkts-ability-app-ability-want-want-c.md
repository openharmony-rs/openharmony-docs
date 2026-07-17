# Want

Want是对象间信息传递的载体，可以用于应用组件间的信息传递。其典型应用场景之一是，当UIAbilityA启动UIAbilityB、并需要传入一些数据时，可使用Want作为载体。例如在startAbility接口的入参want中，可以通过abilityName指定启动的目标Ability，也可以通过parameters等字段携带其他数据。

**起始版本：** 9

<!--Device-unnamed-export default class Want--><!--Device-unnamed-export default class Want-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## 导入模块

```TypeScript
import { Want } from '@kit.AbilityKit';
```

## abilityName

```TypeScript
abilityName?: string
```

应用的Ability组件名。在应用启动场景中表示被拉起方的Ability组件名。如果在Want中该字段同时指定了BundleName和AbilityName，则Want可以直接匹配到指定的Ability。AbilityName需要在一个应用的范围内保证唯一。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Want-abilityName?: string--><!--Device-Want-abilityName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## action

```TypeScript
action?: string
```

表示要执行的通用操作（如：查看、分享、应用详情）。在隐式Want中，开发者可以定义该字段，配合uri或parameters来表示对数据执行的操作。隐式Want定义及匹配规则请参见[显式Want与隐式Want匹配规则](../../../../application-models/explicit-implicit-want-mappings.md)。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Want-action?: string--><!--Device-Want-action?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## bundleName

```TypeScript
bundleName?: string
```

应用包名。在应用启动场景中表示被拉起方的应用包名。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Want-bundleName?: string--><!--Device-Want-bundleName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## deviceId

```TypeScript
deviceId?: string
```

设备ID。在应用启动场景中表示被拉起方的设备ID，如果未设置该字段，则表示指定当前设备。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Want-deviceId?: string--><!--Device-Want-deviceId?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## entities

```TypeScript
entities?: Array<string>
```

表示目标Ability额外的类别信息（如：浏览器、视频播放器）。在隐式Want中是对action字段的补充。在隐式Want中，开发者可以定义该字段，来过滤匹配Ability类型。

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Want-entities?: Array<string>--><!--Device-Want-entities?: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## fds

```TypeScript
readonly fds?: Record<string, number>
```

表示文件描述符，在启动场景中拉起方写入的FD，会设置到该参数中。

从API version 15开始，该接口支持在原子化服务中使用。

**类型：** Record<string, number>

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-Want-readonly fds?: Record<string, int>--><!--Device-Want-readonly fds?: Record<string, int>-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## flags

```TypeScript
flags?: number
```

表示处理Want的方式。值为枚举类型[Flags](arkts-ability-wantconstant-flags-e.md)，默认传数字。

例如取值为0x00000001（即wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION）表示临时授予接收方读取该URI指向的数据的权限。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Want-flags?: int--><!--Device-Want-flags?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## moduleName

```TypeScript
moduleName?: string
```

应用模块名。在应用启动场景中表示被拉起方的应用模块名。

**说明：**

若待启动的Ability所属的模块为[HAR](../../../../quick-start/har-package.md)，则moduleName需为依赖该HAR的[HAP](../../../../quick-start/hap-package.md)/[HSP](../../../../quick-start/in-app-hsp.md)的moduleName。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Want-moduleName?: string--><!--Device-Want-moduleName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## parameters

```TypeScript
parameters?: Record<string, Object>
```

表示WantParams描述。

一、以下Key均由系统赋值，开发者手动修改也不会生效，系统在数据传递时会自动修改为实际值。

- ohos.aafwk.param.callerPid：表示拉起方的pid，值为字符串类型。  
- ohos.aafwk.param.callerBundleName：表示拉起方的BundleName，值为字符串类型。  
- ohos.aafwk.param.callerAbilityName：表示拉起方的AbilityName，值为字符串类型。  
- ohos.aafwk.param.callerNativeName：表示native调用时拉起方的进程名，值为字符串类型。  
- ohos.aafwk.param.callerAppId：表示拉起应用的AppId信息，值为字符串类型。  
- ohos.aafwk.param.callerAppIdentifier：表示拉起应用的AppIdentifier信息，值为字符串类型。  
- ohos.aafwk.param.callerToken：表示拉起方的token，值为字符串类型。  
- ohos.aafwk.param.callerUid：表示[BundleInfo](arkts-ability-bundleinfo-i.md)中的uid，应用包里应用程序的uid，值为数值类型。  
- ohos.param.callerAppCloneIndex：表示拉起方应用的分身索引，值为数值类型。  
- component.startup.newRules：表示是否启用新的管控规则，值为布尔类型。  
- moduleName：表示被拉起方的moduleName，值为字符串类型。  
- ohos.ability.params.abilityRecoveryRestart：表示当前Ability是否发生了故障恢复重启，值为布尔类型。  
- ohos.extra.param.key.showMode：表示拉起原子化服务的展示模式，值为枚举类型[wantConstant.ShowMode](./@ohos.app.ability.wantConstant:wantConstant.showMode)。

**说明**：

在跨端场景中，以下三个字段不生效，不可用于身份或权限校验：ohos.aafwk.param.callerPid、ohos.aafwk.param.callerToken、ohos.aafwk.param.callerUid。

二、提供了一些由系统定义、开发者按需赋值的Key。具体的key值与对应说明详见[wantConstant.Params](./@ohos.app.ability.wantConstant:wantConstant.params)。

三、除了上述情况，应用间还可以相互约定传入的键值对。

**说明**：

want的Params操作的常量的具体信息请参考[wantConstant](arkts-app-ability-wantconstant.md)。

需注意，WantParams支持传输的最大数据量遵循[Want约束限制](#约束限制)。当数据量超过该限制时，请使用[WriteRawDataBuffer](./@ohos.rpc:rpc.writeRawDataBuffer)或[uri](../../apis-arkts/arkts-apis/arkts-uri.md)的方式进行数据传输。

parameters的Value值仅支持基本数据类型：String、Number、Boolean、Object、undefined和null，不支持传递Object内部的function。

**类型：** Record<string, Object>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Want-parameters?: Record<string, Object>--><!--Device-Want-parameters?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## type

```TypeScript
type?: string
```

表示MIME type类型描述，打开文件的类型，主要用于文管打开文件。比如：'text/xml' 、 'image/*'等，MIME定义请参见[Media Types](https://www.iana.org/assignments/media-types/media-types.xhtml?utm_source=ld246.com)。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Want-type?: string--><!--Device-Want-type?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## uri

```TypeScript
uri?: string
```

统一资源标识符，一般在应用启动场景中配合type使用，指明待处理的数据类型。如果在Want中指定了uri，则Want将匹配指定的Uri信息，包括`scheme`、`schemeSpecificPart`、`authority`和`path`信息。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Want-uri?: string--><!--Device-Want-uri?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

