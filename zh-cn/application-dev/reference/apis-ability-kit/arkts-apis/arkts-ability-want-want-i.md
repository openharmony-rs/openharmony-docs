# Want

Want是对象间信息传递的载体, 可以用于应用组件间的信息传递。 Want的使用场景之一是作为[startAbility](arkts-ability-uiabilitycontext-c.md#startability-1)的参数, 其包含了指定的启动目标, 以及启动时需携带的相关数据, 如bundleName和abilityName字段分别指明目标Ability所在应用的Bundle名称以及对应包内的Ability名称。当Ability A需要启动Ability B并传入一些数据时, 可使用Want作为载体将这些数据传递给Ability B。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [Want:Want](arkts-ability-app-ability-want-want-c.md)

<!--Device-unnamed-export declare interface Want--><!--Device-unnamed-export declare interface Want-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## abilityName

```TypeScript
abilityName?: string
```

表示待启动的Ability名称。如果在Want中该字段同时指定了BundleName和AbilityName，则Want可以直接匹配到指定的Ability。AbilityName需要在一个应用的范围内保证唯一。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [abilityName](arkts-ability-app-ability-want-want-c.md#abilityname)

<!--Device-Want-abilityName?: string--><!--Device-Want-abilityName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## action

```TypeScript
action?: string
```

表示要执行的通用操作（如：查看、分享、应用详情）。在隐式Want中，您可以定义该字段，配合uri或parameters来表示对数据要执行的操作。具体参考：[action说明](arkts-ability-wantconstant-action-depr-e.md)。隐式Want定义及匹配规则参考：[显式Want与隐式Want匹配规则](docroot://application-models/explicit-implicit-want-mappings.md)。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [action](arkts-ability-app-ability-want-want-c.md#action)

<!--Device-Want-action?: string--><!--Device-Want-action?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## bundleName

```TypeScript
bundleName?: string
```

表示Bundle名称。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [bundleName](arkts-ability-app-ability-want-want-c.md#bundlename)

<!--Device-Want-bundleName?: string--><!--Device-Want-bundleName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## deviceId

```TypeScript
deviceId?: string
```

表示运行指定Ability的设备ID。如果未设置该字段，则表明指定本设备。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [deviceId](arkts-ability-app-ability-want-want-c.md#deviceid)

<!--Device-Want-deviceId?: string--><!--Device-Want-deviceId?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## entities

```TypeScript
entities?: Array<string>
```

表示目标Ability额外的类别信息（如：浏览器、视频播放器），在隐式Want中是对action字段的补充。在隐式Want中，您可以定义该字段，来过滤匹配Ability类型。

**类型：** Array&lt;string&gt;

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [entities](arkts-ability-app-ability-want-want-c.md#entities)

<!--Device-Want-entities?: Array<string>--><!--Device-Want-entities?: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## flags

```TypeScript
flags?: number
```

表示处理Want的方式。默认传数字，具体参考：[flags说明](arkts-ability-wantconstant-flags-depr-e.md)。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [flags](arkts-ability-app-ability-want-want-c.md#flags)

<!--Device-Want-flags?: number--><!--Device-Want-flags?: number-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## parameters

```TypeScript
parameters?: { [key: string]: any }
```

表示WantParams，由开发者自行决定传入的键值对。默认会携带以下key值：

ohos.aafwk.callerPid 表示拉起方的pid。

ohos.aafwk.param.callerToken 表示拉起方的token。

ohos.aafwk.param.callerUid 表示[bundleInfo](js-apis-bundle-BundleInfo.md#bundleinfodeprecated)中的uid，应用包里应用程序的uid。

- component.startup.newRules：表示是否启用新的管控规则。  
- moduleName：表示拉起方的模块名，该字段的值即使定义成其他字符串，在传递到另一端时会被修改为正确的值。  
- ohos.dlp.params.sandbox：表示dlp文件才会有。

**类型：** { [key: string]: any }

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [parameters](arkts-ability-app-ability-want-want-c.md#parameters)

<!--Device-Want-parameters?: { [key: string]: any }--><!--Device-Want-parameters?: { [key: string]: any }-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## type

```TypeScript
type?: string
```

表示MIME type类型，打开文件的类型，主要用于文管打开文件。比如：'text/xml' 、 'image/*'等，MIME定义参考：https://www.iana.org/assignments/media-types/media-types.xhtml?utm_source=ld246.com。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [type](arkts-ability-app-ability-want-want-c.md#type)

<!--Device-Want-type?: string--><!--Device-Want-type?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## uri

```TypeScript
uri?: string
```

表示Uri。如果在Want中指定了Uri，则Want将匹配指定的Uri信息，包括scheme, schemeSpecificPart, authority和path信息。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [uri](arkts-ability-app-ability-want-want-c.md#uri)

<!--Device-Want-uri?: string--><!--Device-Want-uri?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

