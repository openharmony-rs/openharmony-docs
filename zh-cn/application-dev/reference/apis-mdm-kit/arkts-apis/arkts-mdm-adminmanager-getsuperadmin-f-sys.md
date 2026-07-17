# getSuperAdmin（系统接口）

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## getSuperAdmin

```TypeScript
function getSuperAdmin(): Promise<Want>
```

查询首用户（u100）下的超级设备管理应用。使用Promise异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function getSuperAdmin(): Promise<Want>--><!--Device-adminManager-function getSuperAdmin(): Promise<Want>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Want> | 返回超级设备管理应用的Promise对象。当设备没有激活超级管理应用时，返回的Promise中Want的bundleName与abilityName为空串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

adminManager.getSuperAdmin().then((result) => {
  console.info(`Succeeded in getting super admin :${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get super admin. Code: ${err.code}, message: ${err.message}`);
})

```

