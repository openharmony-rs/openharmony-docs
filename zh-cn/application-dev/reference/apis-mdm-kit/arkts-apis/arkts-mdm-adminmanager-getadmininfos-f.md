# getAdminInfos

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## getAdminInfos

```TypeScript
function getAdminInfos(): Array<AdminInfo>
```

查询管理员信息

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function getAdminInfos(): Array<AdminInfo>--><!--Device-adminManager-function getAdminInfos(): Array<AdminInfo>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[AdminInfo](arkts-mdm-adminmanager-admininfo-i.md)&gt; | Returns the administrators information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |

**示例**

```TypeScript
import { adminManager } from '@kit.MDMKit';

try {
  let result: boolean = adminManager.isSelfSuperAdmin();
  if (result) {
    let adminInfos: Array<adminManager.AdminInfo> = adminManager.getAdminInfos();
    console.info(`Succeeded in getting admin infos :${JSON.stringify(adminInfos)}`);
  } else {
    console.error('current application is not SDA');
  }
} catch (err) {
  console.error(`Failed to get admin infos. Code: ${err.code}, message: ${err.message}`);
}
```
