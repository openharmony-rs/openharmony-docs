# isOsAccountAdditionDisallowed

## isOsAccountAdditionDisallowed

```TypeScript
function isOsAccountAdditionDisallowed(admin: Want, accountId?: number): boolean
```

��ѯ�Ƿ��ֹ�û������˺š�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_SET_ACCOUNT_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| accountId | number | 否 | �û�ID��ָ�������û�����������˲���ʱ����ʾ��ѯ�����û��Ƿ��ֹ�����˺ţ�������˲���ʱ����ʾ��ѯָ���û��Ƿ��ֹ�����˺š�ȡֵ��Χ�����ڵ���0��<br/><br/>accountId����ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>�Ƚӿ�����ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ����true��ʾ��ֹ�����˺š�<br/>����false��ʾ���������˺š� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { accountManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let isDisallowed: boolean = accountManager.isOsAccountAdditionDisallowed(wantTemp, 100);
  console.info(`Succeeded in querying the os account addition or not: ${isDisallowed}`);
} catch (err) {
  console.error(`Failed to query the os account addition or not. Code: ${err.code}, message: ${err.message}`);
}

```

