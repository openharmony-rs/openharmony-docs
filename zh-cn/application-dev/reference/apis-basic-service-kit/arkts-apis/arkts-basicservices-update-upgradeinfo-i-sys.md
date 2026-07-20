# UpgradeInfo（系统接口）

升级信息。

**起始版本：** 9

<!--Device-update-export interface UpgradeInfo--><!--Device-update-export interface UpgradeInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## businessType

```TypeScript
businessType: BusinessType
```

升级业务类型。

**类型：** BusinessType

**起始版本：** 9

<!--Device-UpgradeInfo-businessType: BusinessType--><!--Device-UpgradeInfo-businessType: BusinessType-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## upgradeApp

```TypeScript
upgradeApp: string
```

调用方包名，用于标识调用此升级接口的应用身份。格式为com.xxx.xxx.xxx，由点号分隔的多段组成。长度范围[1，255]，单位：字符，每段长度范围[1，64]，单位：字符，仅支持字母、数字和点号。每段必须以字母开头，不能包含连续点号或以点号开头结尾。超出范围或格式错误时抛出异常。

**类型：** string

**起始版本：** 9

<!--Device-UpgradeInfo-upgradeApp: string--><!--Device-UpgradeInfo-upgradeApp: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

