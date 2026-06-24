# addAllowedPermissionBundle

## addAllowedPermissionBundle

```TypeScript
function addAllowedPermissionBundle(admin: Want, permission: string, applicationInstance: common.ApplicationInstance): void
```

��������ʹ���ѽ���ָ��Ȩ�޵�Ӧ�õ�Ȩ��ʹ������������Ȩ��ʹ�����������е�Ӧ�ÿ��Բ���[setDisallowedPermission](arkts-mdm-securitymanager-setdisallowedpermission-f.md#setDisallowedPermission-1)�Ĳ������ơ�

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| permission | string | 是 | Ȩ�����ơ� |
| applicationInstance | common.ApplicationInstance | 是 | �����ӵ�Ȩ��ʹ������������Ӧ��ʵ����Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9201015](../../errorcode-universal.md#9201015-The) | The application is not installed. |
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
let disallow: boolean = true;
let accountId: number = 100;
// 该应用已经申请了ohos.permission.CAMERA权限
let appInstance: common.ApplicationInstance = {
  appIdentifier: '123456789',
  appIndex: 0,
  accountId: 100
};
try {
  // 禁用ohos.permission.CAMERA权限
  securityManager.setDisallowedPermission(wantTemp, permission, disallow, accountId);
  // 设置指定应用可以继续使用ohos.permission.CAMERA权限
  securityManager.addAllowedPermissionBundle(wantTemp, permission, appInstance);
  console.info(`Succeeded in adding allowed permission bundle.`);
} catch(err) {
  console.error(`Failed to add allowed permission bundle. Code: ${err.code}, message: ${err.message}`);
}

```

