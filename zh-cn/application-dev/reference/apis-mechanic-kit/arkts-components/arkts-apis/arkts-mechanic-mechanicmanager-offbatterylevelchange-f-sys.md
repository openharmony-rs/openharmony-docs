# offBatteryLevelChange（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## offBatteryLevelChange

```TypeScript
function offBatteryLevelChange(mechId: number, callback?: Callback<BatteryLevelInfo>): void
```

取消订阅电池电量变化信息

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | number | 是 | ID of the mechanical device. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BatteryLevelInfo](arkts-mechanic-mechanicmanager-batterylevelinfo-i-sys.md)&gt; | 否 | Callback function that returns the current battery level.<br>If not specified, all callbacks registered for this mechId will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-功能不支持) | Feature not supported. |
