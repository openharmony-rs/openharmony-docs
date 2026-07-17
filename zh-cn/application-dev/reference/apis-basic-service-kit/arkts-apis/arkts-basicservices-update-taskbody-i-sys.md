# TaskBody（系统接口）

任务数据。

**起始版本：** 9

<!--Device-update-export interface TaskBody--><!--Device-update-export interface TaskBody-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## errorMessages

```TypeScript
errorMessages: Array<ErrorMessage>
```

错误信息。

**类型：** Array<ErrorMessage>

**起始版本：** 9

<!--Device-TaskBody-errorMessages: Array<ErrorMessage>--><!--Device-TaskBody-errorMessages: Array<ErrorMessage>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## installMode

```TypeScript
installMode: number
```

安装模式。

**类型：** number

**起始版本：** 9

<!--Device-TaskBody-installMode: int--><!--Device-TaskBody-installMode: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## progress

```TypeScript
progress: number
```

进度。

**类型：** number

**起始版本：** 9

<!--Device-TaskBody-progress: int--><!--Device-TaskBody-progress: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: UpgradeStatus
```

升级状态。

**类型：** UpgradeStatus

**起始版本：** 9

<!--Device-TaskBody-status: UpgradeStatus--><!--Device-TaskBody-status: UpgradeStatus-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## subStatus

```TypeScript
subStatus: number
```

子状态。

**类型：** number

**起始版本：** 9

<!--Device-TaskBody-subStatus: int--><!--Device-TaskBody-subStatus: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## versionComponents

```TypeScript
versionComponents: Array<VersionComponent>
```

版本组件。

**类型：** Array<VersionComponent>

**起始版本：** 9

<!--Device-TaskBody-versionComponents: Array<VersionComponent>--><!--Device-TaskBody-versionComponents: Array<VersionComponent>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## versionDigestInfo

```TypeScript
versionDigestInfo: VersionDigestInfo
```

版本摘要。

**类型：** VersionDigestInfo

**起始版本：** 9

<!--Device-TaskBody-versionDigestInfo: VersionDigestInfo--><!--Device-TaskBody-versionDigestInfo: VersionDigestInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

