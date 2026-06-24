# replaceSuperAdmin（系统接口）

## replaceSuperAdmin

```TypeScript
function replaceSuperAdmin(oldAdmin: Want, newAdmin: Want, isKeepPolicy: boolean): void
```

��ָ��Ӧ���滻�ɳ����豸����Ӧ�á�

**起始版本：** 18

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldAdmin | Want | 是 | ԭ����ҵ�豸������չ�����Want�б������ԭ����ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| newAdmin | Want | 是 | ����ҵ�豸������չ�����Want�б�������µ���ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| isKeepPolicy | boolean | 是 | �Ƿ���ԭ����ҵ�豸������չ����Ĳ��ԣ�ȡֵΪtrue��ʾ������ȡֵΪfalse��ʾ�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200003](../../errorcode-universal.md#9200003-The) | The administrator ability component is invalid. |
| [9200011](../../errorcode-universal.md#9200011-Failed) | Failed to replace the administrator application of the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let oldAdmin: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let newAdmin: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication_new',
  abilityName: 'NewEnterpriseAdminAbility'
};
try {
  adminManager.replaceSuperAdmin(oldAdmin, newAdmin, false);
  console.info(`Succeeded in replacing super admin.`);
} catch(err) {
  console.error(`Failed to replace super admin. Code: ${err.code}, message: ${err.message}`);
}

```

