# startCollectLog

## startCollectLog

```TypeScript
function startCollectLog(admin: Want): Promise<void>
```

��ʼ�ռ��豸�������ɲ��洢��Ӳ�̵�[faultlog](@ohos.faultLogger:FaultLogger.FaultType)��־����֧���ռ�δ�洢��Ӳ�̵�faultlog��־��Ӧ��ҵ����־��ϵͳ������־��

- ���ýӿں�ϵͳ������һ����־�ռ���������������ӿ��������ء�������ܻ���Ϊϵͳ���ܵ�ԭ�����ռ�ʧ�ܡ�
- �������MDMӦ�õ��ã���ͬMDMӦ���ڲ�ͬ�û����ռ�����־�ֿ����棬����Ӱ�졣ͬһʱ��ֻ����һ��MDMӦ��������־�ռ�����������ִ�����ǰ���ñ��ӿڻ᷵�ش�����9201009������ִ����ɺ���������MDMӦ�õ��á�
- ����ִ����ɺ�ͨ��
[EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterpriseadminextensionability-c.md#onLogCollected-1)
�ص�����֪ͨ��MDMӦ�ã�ϵͳ�����ռ�����־�ļ����ص�MDMӦ��ɳ��·����MDMӦ�ÿ����ڻص������ж�ȡ���ռ�����־��
- �����־�ռ�����ִ�г���5���ӣ�
[EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterpriseadminextensionability-c.md#onLogCollected-1)
�ص������᷵����־�ռ�����ʧ�ܡ�
- Ӧ��ȡ����־�󣬽������[systemManager.finishLogCollected](arkts-mdm-systemmanager-finishlogcollected-f.md#finishLogCollected-1)ɾ�����ռ�������־��

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_READ_LOG

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵��ռ���־���񴴽�ʧ��ʱ�����׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9201009](../../errorcode-universal.md#9201009-Collecting) | Collecting logs, please try again later. |
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

systemManager.startCollectLog(wantTemp).then(() => {
  console.info('Succeeded in starting collect log');
}).catch((err: BusinessError) => {
  console.error(`Failed to start collect log. Code: ${err.code}, message: ${err.message}`);
});

```

