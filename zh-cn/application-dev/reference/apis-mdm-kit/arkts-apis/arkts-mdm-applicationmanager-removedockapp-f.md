# removeDockApp

## removeDockApp

```TypeScript
function removeDockApp(admin: Want, bundleName: string, abilityName: string): void
```

�ӿ�������Ƴ�Ӧ�á�

> **˵����**
>
> ����Ӧ�ò���ͨ�����ӿڴӿ�������Ƴ�����Ӧ�����ġ������������ġ������ļ���������������վ�������򱨴�9201018�����롣

> **˵��**
> ����Ӧ�ò���ͨ�����ӿڴӿ�������Ƴ�����Ӧ�����ġ������������ġ������ļ���������������վ�������򱨴�9201018�����롣

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | Ӧ�õİ����� |
| abilityName | string | 是 | Ӧ�õ�Ability���ơ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9201016](../../errorcode-universal.md#9201016-The) | The application has not been added to the Dock. |
| [9201018](../../errorcode-universal.md#9201018-The) | The application is inoperable. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let bundleName: string = 'com.example.exampleapplication';
  let abilityName: string = 'EntryAbility';
  applicationManager.removeDockApp(wantTemp, bundleName, abilityName);
  console.info('Succeeded in removing dock app.');
} catch(err) {
  console.error(`Failed to remove dock app. Code: ${err.code}, message: ${err.message}`);
}

```

