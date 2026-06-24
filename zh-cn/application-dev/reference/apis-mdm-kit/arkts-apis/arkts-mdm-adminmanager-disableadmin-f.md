# disableAdmin

## disableAdmin

```TypeScript
function disableAdmin(admin: Want, userId?: number): Promise<void>
```

�������ָ���û����豸����Ӧ�á�ʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN, ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN or ohos.permission.START_PROVISIONING_MESSAGE, ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN or ohos.permission.START_PROVISIONING_MESSAGE or ohos.permission.ENTERPRISE_DEACTIVATE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName���������BYOD�豸����Ӧ��ʱ����֧�ִ��뵱ǰӦ�õ���ҵ�豸����<br/>��չ����� |
| userId | number | 否 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>- ���ýӿ�ʱ��������userId����ʾָ���û���<br/>- ���ýӿ�ʱ����δ����userId����ʾ��ǰ�û��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵���������豸����Ӧ��ʧ��ʱ�����׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200005](../../errorcode-universal.md#9200005-Failed) | Failed to deactivate the administrator application of the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

adminManager.disableAdmin(wantTemp, 100).catch((err: BusinessError) => {
  console.error(`Failed to disable admin. Code: ${err.code}, message: ${err.message}`);
});

```

