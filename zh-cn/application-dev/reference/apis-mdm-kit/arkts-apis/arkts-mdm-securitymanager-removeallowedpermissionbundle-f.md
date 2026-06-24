# removeAllowedPermissionBundle

## removeAllowedPermissionBundle

```TypeScript
function removeAllowedPermissionBundle(admin: Want, permission: string, applicationInstance: common.ApplicationInstance): void
```

��Ȩ��ʹ�������������Ƴ�ָ��Ӧ�ã��Ƴ����Ӧ�����ܼ���ʹ�ö�Ӧ��Ȩ�ޡ�

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| permission | string | 是 | Ȩ�����ơ� |
| applicationInstance | common.ApplicationInstance | 是 | ���Ȩ��ʹ�����������Ƴ���Ӧ��ʵ����Ϣ��<br/>the application need to be removed from the list of applications allowed to grant the permission. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9201044](../../errorcode-universal.md#9201044-This) | This permission is not disallowed.<br/>Applications cannot be added to or removed from the trustlist. |

**示例：**

```TypeScript
import { securityManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let permission: string = 'ohos.permission.CAMERA';
let appInstance: common.ApplicationInstance = {
  appIdentifier: '736498586',
  appIndex: 0,
  accountId: 100
};
try {
  securityManager.removeAllowedPermissionBundle(wantTemp, permission, appInstance);
  console.info(`Succeeded in removing allowed permission bundle.`);
} catch(err) {
  console.error(`Failed to remove allowed permission bundle. Code: ${err.code}, message: ${err.message}`);
}

```

