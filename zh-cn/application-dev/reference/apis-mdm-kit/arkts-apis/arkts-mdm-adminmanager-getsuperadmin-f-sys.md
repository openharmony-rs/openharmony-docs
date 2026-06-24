# getSuperAdmin（系统接口）

## getSuperAdmin

```TypeScript
function getSuperAdmin(): Promise<Want>
```

��ѯ���û���u100���µĳ����豸����Ӧ�á�ʹ��Promise�첽�ص���

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Want&gt; | ���س����豸����Ӧ�õ�Promise���󡣵��豸û�м��������Ӧ��ʱ�����ص�Promise��Want��bundleName��abilityNameΪ�մ��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

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

