# startAdminProvision

## startAdminProvision

```TypeScript
function startAdminProvision(admin: Want, type: AdminType, context: common.Context, parameters: Record<string, string>): void
```

�豸����Ӧ������BYOD����Ա����ҳ����м��

**起始版本：** 15

**需要权限：** ohos.permission.START_PROVISIONING_MESSAGE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| type | AdminType | 是 | ������豸����Ӧ�����ͣ���֧��ADMIN_TYPE_BYOD���͡� |
| context | common.Context | 是 | ����Ӧ�õ���������Ϣ�� |
| parameters | Record&lt;string, string&gt; | 是 | �Զ��������Ϣ������Keyֵ���������"activateId"�����԰���"customizedInfo"��"<br/>localDeactivationPolicy"��<br/>- activateId����Ŀ����ID��<br/>- customizedInfo����ҵ�Զ�����Ϣ��<br/>- localDeactivationPolicy��<br/>��API version 22��ʼ֧�֣������ӳ�ȡ������ʱ�䣨��λ��Сʱ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let recordParameters: Record<string, string> = {
  // 需根据实际情况进行替换
  "activateId": "activateId testValue",
  "customizedInfo": "customizedInfo testValue"
};
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
try {
  console.info('context:' + JSON.stringify(context));
  adminManager.startAdminProvision(wantTemp, adminManager.AdminType.ADMIN_TYPE_BYOD, context, recordParameters);
  console.info('startAdminProvision::success');
} catch (error) {
  console.error('startAdminProvision::errorCode: ' + error.code + ' errorMessage: ' + error.message);
}

```

