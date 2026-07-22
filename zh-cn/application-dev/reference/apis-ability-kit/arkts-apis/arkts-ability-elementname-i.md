# ElementName

应用组件结构体，包含bundleName、moduleName和abilityName等。通常用于组件启动信息[AbilityRunningInfo.ability](arkts-ability-abilityrunninginfo-i.md)和组件启动回调函数[connectOptions.onConnect](arkts-ability-connectoptions-connectoptions-i.md#onconnect)中。

**起始版本：** 9

<!--Device-unnamed-export interface ElementName--><!--Device-unnamed-export interface ElementName-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## abilityName

```TypeScript
abilityName: string
```

Ability名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ElementName-abilityName: string--><!--Device-ElementName-abilityName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
bundleName: string
```

应用Bundle名称。

**类型：** string

**默认值：** Indicates bundle name

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ElementName-bundleName: string--><!--Device-ElementName-bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## deviceId

```TypeScript
deviceId?: string
```

设备ID。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ElementName-deviceId?: string--><!--Device-ElementName-deviceId?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
moduleName?: string
```

Ability所属的HAP的模块名称。

**类型：** string

**默认值：** Indicates module name

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ElementName-moduleName?: string--><!--Device-ElementName-moduleName?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## shortName

```TypeScript
shortName?: string
```

Ability短名称，以“.”为开头的字符串。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ElementName-shortName?: string--><!--Device-ElementName-shortName?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## uri

```TypeScript
uri?: string
```

资源标识符。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ElementName-uri?: string--><!--Device-ElementName-uri?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

