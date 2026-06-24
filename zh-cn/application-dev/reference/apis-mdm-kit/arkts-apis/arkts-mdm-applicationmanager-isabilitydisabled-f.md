# isAbilityDisabled

## isAbilityDisabled

```TypeScript
function isAbilityDisabled(admin: Want, bundleName: string, accountId: number, abilityName: string): boolean
```

��ȡָ��Ӧ�ã�ϵͳӦ�ú�����Ӧ�þ�֧�֣���Ability����Ƿ񱻽��á�

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | Ӧ�ð�����ָ���Ƿ���õ�Ӧ�ð����� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��������<br/>- �û�ID��ȡֵ��Χ�����ڵ���0��������<br/>accountId����ͨ��@ohos.account.osAccount�е�<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-2)�Ƚӿ�����ȡ�� |
| abilityName | string | 是 | ��ʾҪ����/������õ�Ability������ƣ���ǰ��֧��UIAbility���� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | �������Ƿ���á�true��ʾ��Ability��������ã�false��ʾ��Ability���δ�����á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let bundleName: string = "com.example.exampleapplication";
  let accountId: number = 100;
  let abilityName: string = "EntryAbility";
  let isDisabled: boolean = applicationManager.isAbilityDisabled(wantTemp, bundleName, accountId, abilityName);
  console.info(`Succeeded in querying whether the ability is disabled, isDisabled: ${isDisabled}`);
} catch(err) {
  console.error(`Failed to query whether the ability is disabled. Code: ${err.code}, message: ${err.message}`);
}

```

