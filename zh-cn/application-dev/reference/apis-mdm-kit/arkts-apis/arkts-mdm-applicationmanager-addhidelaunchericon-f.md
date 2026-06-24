# addHideLauncherIcon

## addHideLauncherIcon

```TypeScript
function addHideLauncherIcon(admin: Want, bundleNames: Array<string>): void
```

������������Ӧ��ͼ��������

> **˵����**
>
> 1�����ӿڽ�֧�����ص�ǰ�û�������Ӧ��ͼ�꣬��֧������Ӧ�ÿ�Ƭ��
>
> 2����������ص�Ӧ����Ӧ�÷�������ͬ������Ӧ�÷�����
>
> 3�����ܰ���������Ӧ�ö����ӵ����������У���������Ӧ�ö�����ʾ�������ϡ�

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| bundleNames | Array&lt;string&gt; | 是 | Ӧ�ð������飬ָ����Ҫ���ص�Ӧ�ã����֧��500���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-Parameter) | Parameter verification failed. |
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
// 需根据实际情况进行替换
let bundleNames: Array<string> = ['com.example.test'];
try {
  applicationManager.addHideLauncherIcon(wantTemp, bundleNames);
  console.info('Succeeded in adding hide launcher icon.');
} catch (err) {
  console.error(`Failed to add hide launcher icon. Code is ${err.code}, message is ${err.message}`);
}

```

