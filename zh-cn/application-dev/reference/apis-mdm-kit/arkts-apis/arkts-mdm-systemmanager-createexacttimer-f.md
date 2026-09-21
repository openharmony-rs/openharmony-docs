# createExactTimer

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## createExactTimer

```TypeScript
function createExactTimer(config: ExactTimerConfig): Promise<number>
```

创建精确定时器。该接口使用promise返回定时器ID。

> **说明：** 
> 
> 该接口需要和[systemManager.destroyTimer](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-systemtimer-destroytimer-f-sys.md)配合使用。否则，
> 内存泄漏。禁用或删除管理应用程序时，EDM服务会自动销毁管理员创建的所有计时器。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ExactTimerConfig](arkts-mdm-systemmanager-exacttimerconfig-c.md) | 是 | Timer initialization configuration, including whether the timer is a repeating timer, interval, callback, and name. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise用于返回定时器ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| 9201053 | The number of timers has reached the upper limit. |
