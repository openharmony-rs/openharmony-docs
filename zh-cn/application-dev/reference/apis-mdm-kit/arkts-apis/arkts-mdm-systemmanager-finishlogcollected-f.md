# finishLogCollected

## finishLogCollected

```TypeScript
function finishLogCollected(admin: Want): void
```

ɾ����MDMӦ���ڵ�ǰ�û����ռ������豸��־��

> **˵����**
>
> ��Ӧ�õ���[startCollectLog](arkts-mdm-systemmanager-startcollectlog-f.md#startCollectLog-1)��ʼ�ռ���־���յ�
> [EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterpriseadminextensionability-c.md#onLogCollected-1)
> �ص�ʱ�����������������ߴ�����־�������ô˽ӿ�ɾ���ռ�������־��
>
> ���������ӿڣ��豸��־��ռ��ϵͳ�洢�ռ䣬��Ӱ����һ�ε���[startCollectLog](arkts-mdm-systemmanager-startcollectlog-f.md#startCollectLog-1)������־�ռ�����

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_READ_LOG

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  systemManager.finishLogCollected(wantTemp);
  console.info('Succeeded in finishing log collected.');
} catch (err) {
  console.error(`Failed to finish log collected. Code is ${err.code}, message is ${err.message}`);
}

```

