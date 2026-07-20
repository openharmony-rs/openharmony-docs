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

**类型：** Array&lt;ErrorMessage&gt;

**起始版本：** 9

<!--Device-TaskBody-errorMessages: Array<ErrorMessage>--><!--Device-TaskBody-errorMessages: Array<ErrorMessage>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## installMode

```TypeScript
installMode: number
```

安装模式，取值范围[0, 2]。取值原则：0为正常升级，适用于用户主动触发升级的场景；1为夜间升级，适用于设置夜间时段自动升级的场景；2为自动升级，适用于系统自动检测并执行升级的场景。应根据升级策略和用户体验需求选择。超出范围时抛出异常。

**类型：** number

**起始版本：** 9

<!--Device-TaskBody-installMode: int--><!--Device-TaskBody-installMode: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## progress

```TypeScript
progress: number
```

进度，单位为%，取值范围[0, 100]，超出范围时抛出异常。

**类型：** number

**起始版本：** 9

<!--Device-TaskBody-progress: int--><!--Device-TaskBody-progress: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: UpgradeStatus
```

升级状态。用于标识升级任务的当前执行阶段。包含下载状态（WAITING_DOWNLOAD到DOWNLOAD_FAIL）、安装状态（WAITING_INSTALL到UPDATING）、生效状态（WAITING_APPLY到APPLYING）和最终结果（UPGRADE_SUCCESS或UPGRADE_FAIL），用于任务状态监控、进度展示和异常处理等场景。

**类型：** UpgradeStatus

**起始版本：** 9

<!--Device-TaskBody-status: UpgradeStatus--><!--Device-TaskBody-status: UpgradeStatus-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## subStatus

```TypeScript
subStatus: number
```

子状态，取值范围参考[UpgradeStatus](arkts-basicservices-update-upgradestatus-e-sys.md)状态码。

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

**类型：** Array&lt;VersionComponent&gt;

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

