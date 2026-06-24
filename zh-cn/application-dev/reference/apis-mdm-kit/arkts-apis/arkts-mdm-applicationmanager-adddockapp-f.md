# addDockApp

## addDockApp

```TypeScript
function addDockApp(admin: Want, bundleName: string, abilityName: string, index?: number): void
```

����λ����������Ӧ�õ�PC/2in1�豸�ĵײ�����������Ӻ��û�����ͨ������������Ӧ��ͼ��ֱ������Ӧ�ã�Ӧ��ͼ��ΪӦ������������ʾ��Ĭ��ͼ�ꡣ

> **˵����**
>
> 1.��λ��0��1���Ѵ��ڡ�Ӧ�����ġ����������ġ����������λ������Ӧ�û᷵�ش�����9201019������λ��Ϊ����Ӧ�ã�����������ӡ�
>
> 2.����Ӧ�ò���ͨ�����ӿ����ӵ����������Ӧ�����ġ������������ġ������ļ���������������վ����
>
> 3.��֧�����Ӿ���Ӧ�ó�����ڣ�����ͼ�꣩��Ӧ�ã���ͼ���Ӧ�ò�֧�����ӡ�
>
> 4.��֧�����õ�ǰ�û��µĿ������ÿ���û��Ŀ������������100��Ӧ�á�
>
> 5.������Ӧ�õ�λ�ò�����Ӧ��ʱ����Ӧ�ý�ֱ��ռ�ø�λ�ã�ԭӦ�ü�����Ӧ���������˳��һλ��
>
> 6.������index�����������indexֵ���ڿ������ǰӦ������������Ӧ��Ĭ��׷�ӵ������ĩβ��
>
> 7.ͨ�����ӿ�����Ӧ�õ���������û������ֶ��Ƴ������Ӧ�õ�λ�á�

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleName | string | 是 | Ӧ�õİ����� |
| abilityName | string | 是 | Ӧ�õ�Ability���ƣ���֧��Ӧ�ó������Ability�� |
| index | number | 否 | Ӧ���ڿ�����е�λ��������<br/><br/>ȡֵӦΪ[0,99]�ڵ�������Ĭ��ֵΪ99�� Ĭ��ֵ�� 99�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
| [9200015](../../errorcode-universal.md#9200015-The) | The ability does not exist. |
| [9201013](../../errorcode-universal.md#9201013-The) | The number of applications in the Dock has reached the maximum. |
| [9201014](../../errorcode-universal.md#9201014-The) | The application is already in the Dock. |
| [9201015](../../errorcode-universal.md#9201015-The) | The application is not installed. |
| [9201018](../../errorcode-universal.md#9201018-The) | The application is inoperable. |
| [9201019](../../errorcode-universal.md#9201019-The) | The location is inoperable. |
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
  applicationManager.addDockApp(wantTemp, bundleName, abilityName, 3);
  console.info('Succeeded in adding dock app.');
} catch(err) {
  console.error(`Failed to add dock app. Code: ${err.code}, message: ${err.message}`);
}

```

