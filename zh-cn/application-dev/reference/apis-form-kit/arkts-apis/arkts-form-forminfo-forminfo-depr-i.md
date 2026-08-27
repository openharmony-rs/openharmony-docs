# FormInfo

卡片信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [FormInfo](arkts-form-forminfo-forminfo-i.md)

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
```

## abilityName

```TypeScript
abilityName: string
```

表示卡片所属的Ability名称。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [abilityName](arkts-form-forminfo-forminfo-i.md#abilityname)

**系统能力：** SystemCapability.Ability.Form

## bundleName

```TypeScript
bundleName: string
```

表示卡片所属包的Bundle名称。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [bundleName](arkts-form-forminfo-forminfo-i.md#bundlename)

**系统能力：** SystemCapability.Ability.Form

## colorMode

```TypeScript
colorMode: ColorMode
```

表示卡片颜色模式。

**类型：** ColorMode

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [colorMode](arkts-form-forminfo-forminfo-i.md#colormode)

**系统能力：** SystemCapability.Ability.Form

## customizeData

```TypeScript
customizeData: { [key: string]: [value: string] }
```

表示卡片自定义数据。

**类型：** { [key: string]: [value: string] }

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [customizeData](arkts-form-forminfo-forminfo-i.md#customizedata)

**系统能力：** SystemCapability.Ability.Form

## defaultDimension

```TypeScript
defaultDimension: number
```

表示卡片默认规格。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [defaultDimension](arkts-form-forminfo-forminfo-i.md#defaultdimension)

**系统能力：** SystemCapability.Ability.Form

## description

```TypeScript
description: string
```

表示卡片描述。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [description](arkts-form-forminfo-forminfo-i.md#description)

**系统能力：** SystemCapability.Ability.Form

## formConfigAbility

```TypeScript
formConfigAbility: string
```

表示卡片配置ability。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [formConfigAbility](arkts-form-forminfo-forminfo-i.md#formconfigability)

**系统能力：** SystemCapability.Ability.Form

## formVisibleNotify

```TypeScript
formVisibleNotify: boolean
```

表示卡片是否使能可见通知。  
- true：通知卡片提供方可见状态变化。  
- false：不通知卡片提供方可见状态变化。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [formVisibleNotify](arkts-form-forminfo-forminfo-i.md#formvisiblenotify)

**系统能力：** SystemCapability.Ability.Form

## isDefault

```TypeScript
isDefault: boolean
```

表示是否是默认卡片。  
- true：默认卡片。  
- false：非默认卡片。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isDefault](arkts-form-forminfo-forminfo-i.md#isdefault)

**系统能力：** SystemCapability.Ability.Form

## jsComponentName

```TypeScript
jsComponentName: string
```

表示JS卡片的组件名。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [jsComponentName](arkts-form-forminfo-forminfo-i.md#jscomponentname)

**系统能力：** SystemCapability.Ability.Form

## moduleName

```TypeScript
moduleName: string
```

表示卡片所属模块的模块名。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [moduleName](arkts-form-forminfo-forminfo-i.md#modulename)

**系统能力：** SystemCapability.Ability.Form

## name

```TypeScript
name: string
```

表示卡片名称。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [name](arkts-form-forminfo-forminfo-i.md#name)

**系统能力：** SystemCapability.Ability.Form

## relatedBundleName

```TypeScript
relatedBundleName: string
```

表示卡片所属的相关联Bundle名称。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Ability.Form

## scheduledUpdateTime

```TypeScript
scheduledUpdateTime: string
```

表示卡片定时更新时间。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [scheduledUpdateTime](arkts-form-forminfo-forminfo-i.md#scheduledupdatetime)

**系统能力：** SystemCapability.Ability.Form

## supportDimensions

```TypeScript
supportDimensions: Array<number>
```

表示卡片支持的规格。

**类型：** Array&lt;number&gt;

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [supportDimensions](arkts-form-forminfo-forminfo-i.md#supportdimensions)

**系统能力：** SystemCapability.Ability.Form

## type

```TypeScript
type: FormType
```

表示卡片类型，当前支持JS卡片。

**类型：** FormType

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [type](arkts-form-forminfo-forminfo-i.md#type)

**系统能力：** SystemCapability.Ability.Form

## updateDuration

```TypeScript
updateDuration: number
```

表示卡片更新周期。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [updateDuration](arkts-form-forminfo-forminfo-i.md#updateduration)

**系统能力：** SystemCapability.Ability.Form

## updateEnabled

```TypeScript
updateEnabled: boolean
```

表示卡片是否使能更新。  
- true：表示支持周期性刷新。  
- false：表示不支持周期性刷新。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [updateEnabled](arkts-form-forminfo-forminfo-i.md#updateenabled)

**系统能力：** SystemCapability.Ability.Form
