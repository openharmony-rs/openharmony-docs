# getAdmins（系统接口）

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

<a id="getadmins"></a>
## getAdmins

```TypeScript
function getAdmins(): Promise<Array<Want>>
```

查询当前用户下的所有设备管理应用。使用Promise异步回调。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function getAdmins(): Promise<Array<Want>>--><!--Device-adminManager-function getAdmins(): Promise<Array<Want>>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Want&gt;&gt; | 包含所有已激活的设备管理应用的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

adminManager.getAdmins().then((result) => {
  console.info(`Succeeded in getting admins :${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get admins. Code: ${err.code}, message: ${err.message}`);
})

```

