# getAdmins（系统接口）

## getAdmins

```TypeScript
function getAdmins(): Promise<Array<Want>>
```

��ѯ��ǰ�û��µ������豸����Ӧ�á�ʹ��Promise�첽�ص���

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Want&gt;&gt; | ���������Ѽ�����豸����Ӧ�õ�Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

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

