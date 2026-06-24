# setKioskFeatures

## setKioskFeatures

```TypeScript
function setKioskFeatures(admin: Want, features: Array<KioskFeature>): void
```

����Kioskģʽ��������ͨ�����ӿڿ��Կ�����Kioskģʽ���ܷ����֪ͨ���ġ��������ġ�

��API version 24��ʼ������֧�������Ƿ������ײ��ϻ�����������������󻬻��һ���ͣչʾ���DOCK����

�ڷ�Kioskģʽ�£����ӿڿ����������ã����ǲ�����Ч������Kioskģʽ��Ż���Ч��

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_SET_KIOSK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| features | Array&lt;KioskFeature&gt; | 是 | Kioskģʽ���������ϣ���API version 24��ʼ�����������ײ��ϻ��������������������ͣ���һ���ͣչʾ���DOCK������<br/><br/>�����������ʱ��ϵͳ�����֮ǰ�·������������ָ���Kioskģʽ��Ĭ��״̬����������֪ͨ���ġ��������ġ���������������Dock���������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-The) | The parameter verification failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.The application does not have the permission<br/>required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { applicationManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let kioskFeatures: Array<applicationManager.KioskFeature> = [];
kioskFeatures.push(applicationManager.KioskFeature.ALLOW_NOTIFICATION_CENTER);
kioskFeatures.push(applicationManager.KioskFeature.ALLOW_CONTROL_CENTER);
kioskFeatures.push(applicationManager.KioskFeature.ALLOW_GESTURE_CONTROL);
kioskFeatures.push(applicationManager.KioskFeature.ALLOW_SIDE_DOCK);
try {
  applicationManager.setKioskFeatures(wantTemp, kioskFeatures);
  console.info('Succeeded in setting kiosk feature.');
} catch (err) {
  console.error(`Failed to set kiosk feature. Code is ${err.code}, message is ${err.message}`);
}

```

