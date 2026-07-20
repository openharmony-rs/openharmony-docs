# VersionComponent（系统接口）

版本组件。

**起始版本：** 9

<!--Device-update-export interface VersionComponent--><!--Device-update-export interface VersionComponent-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## componentId

```TypeScript
componentId: string
```

组件标识，用于唯一标识升级包中的组件。从版本检查结果的versionComponents数组中获取，用于后续描述信息查询或组件信息展示等场景。

**类型：** string

**起始版本：** 9

<!--Device-VersionComponent-componentId: string--><!--Device-VersionComponent-componentId: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## componentType

```TypeScript
componentType: ComponentType
```

组件类型。

**类型：** ComponentType

**起始版本：** 9

<!--Device-VersionComponent-componentType: ComponentType--><!--Device-VersionComponent-componentType: ComponentType-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## descriptionInfo

```TypeScript
descriptionInfo: DescriptionInfo
```

描述文件信息.

**类型：** DescriptionInfo

**起始版本：** 9

<!--Device-VersionComponent-descriptionInfo: DescriptionInfo--><!--Device-VersionComponent-descriptionInfo: DescriptionInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## displayVersion

```TypeScript
displayVersion: string
```

显示版本号。

**类型：** string

**起始版本：** 9

<!--Device-VersionComponent-displayVersion: string--><!--Device-VersionComponent-displayVersion: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## effectiveMode

```TypeScript
effectiveMode: EffectiveMode
```

生效模式，取值原则：COLD为冷升级，需重启设备生效；LIVE为热升级，无需重启即可生效；LIVE_AND_COLD为融合升级，结合两者特性。

**类型：** EffectiveMode

**起始版本：** 9

<!--Device-VersionComponent-effectiveMode: EffectiveMode--><!--Device-VersionComponent-effectiveMode: EffectiveMode-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## innerVersion

```TypeScript
innerVersion: string
```

版本号。

**类型：** string

**起始版本：** 9

<!--Device-VersionComponent-innerVersion: string--><!--Device-VersionComponent-innerVersion: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## otaMode

```TypeScript
otaMode?: OtaMode
```

升级模式。当需要指定特定的升级模式时传入此参数，适用于存储空间受限、快速升级或A/B分区设备等特殊场景。取值原则：REGULAR_OTA为正常升级，适用于大多数常规升级场景；STREAM_OTA为流式升级，适用于存储空间受限或需要快速升级的场景；AB_REGULAR_OTA为AB正常升级，适用于A/B分区设备；AB_STREAM_OTA为AB流式升级，适用于A/B分区设备。不传入时默认为REGULAR_OTA，使用正常升级模式。

**类型：** OtaMode

**起始版本：** 20

<!--Device-VersionComponent-otaMode?: OtaMode--><!--Device-VersionComponent-otaMode?: OtaMode-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: number
```

升级包大小，单位为B，取值范围[0, +∞]。超出范围时抛出异常。

**类型：** number

**起始版本：** 9

<!--Device-VersionComponent-size: int--><!--Device-VersionComponent-size: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## upgradeAction

```TypeScript
upgradeAction: UpgradeAction
```

升级方式，取值原则：UPGRADE为差分包，适用于增量升级场景；RECOVERY为修复包，适用于系统故障修复场景。

**类型：** UpgradeAction

**起始版本：** 9

<!--Device-VersionComponent-upgradeAction: UpgradeAction--><!--Device-VersionComponent-upgradeAction: UpgradeAction-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

