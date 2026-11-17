# unregisterHibernateCallback（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## unregisterHibernateCallback

```TypeScript
function unregisterHibernateCallback(): void
```

取消订阅设备进入或退出休眠的回调。所有已注册的休眠回调都会被移除。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.POWER_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-power-function unregisterHibernateCallback(): void--><!--Device-power-function unregisterHibernateCallback(): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |
