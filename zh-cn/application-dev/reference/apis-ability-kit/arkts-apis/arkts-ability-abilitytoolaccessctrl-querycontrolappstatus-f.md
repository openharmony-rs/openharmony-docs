# queryControlAppStatus

## 导入模块

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## queryControlAppStatus

```TypeScript
export function queryControlAppStatus(appInfo: AppInfo[]): Promise<ControlAppStatusResult[]>
```

查询指定应用的控制权限状态。此函数检查输入列表中的每个应用程序是否被允许或拒绝被外部工具控制。结果列表与输入顺序相对应。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.CONTROL_DEVICE

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-abilityToolAccessCtrl-export function queryControlAppStatus(appInfo: AppInfo[]): Promise<ControlAppStatusResult[]>--><!--Device-abilityToolAccessCtrl-export function queryControlAppStatus(appInfo: AppInfo[]): Promise<ControlAppStatusResult[]>-End-->

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appInfo | [AppInfo](arkts-ability-abilitytoolaccessctrl-appinfo-i.md)[] | 是 | 应用信息列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ControlAppStatusResult](arkts-ability-abilitytoolaccessctrl-controlappstatusresult-i.md)[]&gt; | Promise用于返回${ControlAppStatusResult[]}。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-入参错误) | Invalid parameter. appInfo is empty, bundleName is invalid, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-系统服务工作异常) | Service is abnormal. possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-服务内部错误) | Common internal error. possible cause: dependent service unavailable, resource access failure, etc. |
