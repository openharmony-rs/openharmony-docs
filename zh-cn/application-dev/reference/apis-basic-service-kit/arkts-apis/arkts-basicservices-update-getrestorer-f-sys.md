# getRestorer（系统接口）

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## getRestorer

```TypeScript
function getRestorer(): Restorer
```

获取恢复出厂设置对象，用于执行恢复出厂设置相关操作。调用此方法后，系统返回Restorer工具类对象，提供三种恢复出厂方式：

- factoryReset（普通恢复出厂，用于清除用户数据分区。详见[术语](../../../basic-services/update/update-kit-term.md)）。  
- forceFactoryReset（强制恢复出厂，用于清除用户数据分区并同步清除文件密钥。详见[术语](../../../basic-services/update/update-kit-term.md)）。  
- deepFactoryReset（深度恢复出厂，用于通过scope参数指定清除范围：DATA仅清除用户数据分区，DATA_AND_OS同时清除用户数据和操作系统分区。详见[术语](../../../basic-services/update/update-kit-term.md)）。

获取对象后可调用相应方法执行恢复出厂操作，设备将重启恢复到出厂初始状态。

**原理说明**：

该方法通过系统服务接口获取恢复出厂设置对象，封装了数据分区清除、密钥清除、系统分区清理等核心功能。

**约束和限制**：

- 恢复出厂操作不可逆，将永久删除用户数据，需提前提醒用户备份重要数据。  
- 调用factoryReset，deepFactoryReset和getDeepFactoryResetInfo接口时，需要权限ohos.permission.FACTORY_RESET。  
- 调用forceFactoryReset接口时，需要权限ohos.permission.FORCE_FACTORY_RESET。  
- 操作过程中设备会自动重启，应用需做好状态保存。  
- 深度恢复出厂(deepFactoryReset)耗时较长（根据设备存储容量，可能需要1-4小时），必须确保设备电量充足(建议电量>50%)。  
- 建议在用户通过对话框或界面点击确认按钮后，再执行恢复出厂操作。

**起始版本：** 9

<!--Device-update-function getRestorer(): Restorer--><!--Device-update-function getRestorer(): Restorer-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Restorer](arkts-basicservices-update-restorer-i-sys.md) | 用于执行恢复出厂设置相关操作的工具类对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();

```

