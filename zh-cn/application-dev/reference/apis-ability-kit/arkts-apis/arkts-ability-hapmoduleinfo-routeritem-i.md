# RouterItem

描述模块配置的路由表信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface RouterItem--><!--Device-unnamed-export interface RouterItem-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## buildFunction

```TypeScript
readonly buildFunction: string
```

标识被@Builder修饰的函数，该函数描述页面的UI。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RouterItem-readonly buildFunction: string--><!--Device-RouterItem-readonly buildFunction: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## customData

```TypeScript
readonly customData: string
```

标识[路由表配置文件](../../../quick-start/module-configuration-file.md#routermap标签)中的任意类型的自定义数据，即customData字段的JSON字符串，开发者需要 调用JSON.parse函数解析出具体内容。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RouterItem-readonly customData: string--><!--Device-RouterItem-readonly customData: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## data

```TypeScript
readonly data: Array<DataItem>
```

标识[路由表配置文件](../../../quick-start/module-configuration-file.md#routermap标签)中的字符串自定义数据，即data字段的信息，该字段已由系统解析，无需开发者自行解 析。

**类型：** Array&lt;[DataItem](arkts-ability-hapmoduleinfo-dataitem-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RouterItem-readonly data: Array<DataItem>--><!--Device-RouterItem-readonly data: Array<DataItem>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

标识跳转页面的名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RouterItem-readonly name: string--><!--Device-RouterItem-readonly name: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## pageSourceFile

```TypeScript
readonly pageSourceFile: string
```

标识页面在模块内的路径。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RouterItem-readonly pageSourceFile: string--><!--Device-RouterItem-readonly pageSourceFile: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

