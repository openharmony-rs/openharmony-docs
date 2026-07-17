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

组件标识。

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

版本描述文件信息。

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

生效模式。

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

升级模式。

**类型：** OtaMode

**起始版本：** 20

<!--Device-VersionComponent-otaMode?: OtaMode--><!--Device-VersionComponent-otaMode?: OtaMode-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: number
```

升级包大小，单位为B。

**类型：** number

**起始版本：** 9

<!--Device-VersionComponent-size: int--><!--Device-VersionComponent-size: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## upgradeAction

```TypeScript
upgradeAction: UpgradeAction
```

升级方式。

**类型：** UpgradeAction

**起始版本：** 9

<!--Device-VersionComponent-upgradeAction: UpgradeAction--><!--Device-VersionComponent-upgradeAction: UpgradeAction-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

