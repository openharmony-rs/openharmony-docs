# CheckResult（系统接口）

版本检查结果。

**起始版本：** 9

<!--Device-update-export interface CheckResult--><!--Device-update-export interface CheckResult-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## isExistNewVersion

```TypeScript
isExistNewVersion: boolean
```

是否有新版本。true表示有新版本，false表示没有新版本。

**类型：** boolean

**起始版本：** 9

<!--Device-CheckResult-isExistNewVersion: boolean--><!--Device-CheckResult-isExistNewVersion: boolean-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## newVersionInfo

```TypeScript
newVersionInfo: NewVersionInfo
```

新版本数据。

**类型：** NewVersionInfo

**起始版本：** 9

<!--Device-CheckResult-newVersionInfo: NewVersionInfo--><!--Device-CheckResult-newVersionInfo: NewVersionInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

