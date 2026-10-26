# getLocalHotaDomain

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## getLocalHotaDomain

```TypeScript
function getLocalHotaDomain(): string
```

获取设备的本地HOTA域。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-systemManager-function getLocalHotaDomain(): string--><!--Device-systemManager-function getLocalHotaDomain(): string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回本地HOTA域。当前设备，返回空字符串作为默认值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [9200018](../errorcode-enterpriseDeviceManager.md#9200018-该设备非企业设备) | This device is not an enterprise device. |

**示例**

```TypeScript
import { systemManager } from '@kit.MDMKit';

try {
  let domain: string = systemManager.getLocalHotaDomain();
  console.info(`Succeeded in getting local HOTA domain: ${domain}`);
} catch (err) {
  console.error(`Failed to get local HOTA domain. Code is ${err.code}, message is ${err.message}`);
}
```
