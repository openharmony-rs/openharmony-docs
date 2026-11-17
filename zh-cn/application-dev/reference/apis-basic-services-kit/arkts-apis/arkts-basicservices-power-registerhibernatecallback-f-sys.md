# registerHibernateCallback（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## registerHibernateCallback

```TypeScript
function registerHibernateCallback(callback: HibernateCallback): void
```

订阅设备进入或退出休眠的回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.POWER_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-power-function registerHibernateCallback(callback: HibernateCallback): void--><!--Device-power-function registerHibernateCallback(callback: HibernateCallback): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [HibernateCallback](arkts-basicservices-power-hibernatecallback-i-sys.md) | 是 | 回调对象，包含onHibernate和onWakeup方法。onHibernate在进入休眠时调用，无参数；onWakeup在退出休眠时调用，hibernateResult表示休眠是否成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [4900400](../errorcode-power.md#4900400-接口入参无效) | Parameter error. Possible causes: The callback object is missing onHibernate or onWakeup function members. |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |
