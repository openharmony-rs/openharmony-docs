# setPowerPolicy（系统接口）

## setPowerPolicy

```TypeScript
function setPowerPolicy(admin: Want, powerScene: PowerScene, powerPolicy: PowerPolicy): void
```

���õ�Դ���ԡ�

**起始版本：** 11

**废弃版本：** 26.0.0

**替代接口：** [setValue](arkts-mdm-devicesettings-setvalue-f.md#setValue-1)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| powerScene | PowerScene | 是 | ��Դ���Գ�������ǰֻ֧�ֳ�ʱ������ |
| powerPolicy | PowerPolicy | 是 | ��Դ���ԡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let delayTime = 0;
  let powerScene: deviceSettings.PowerScene = deviceSettings.PowerScene.TIME_OUT;
  let powerPolicyAction: deviceSettings.PowerPolicyAction = deviceSettings.PowerPolicyAction.AUTO_SUSPEND;
  let powerPolicy: deviceSettings.PowerPolicy = {powerPolicyAction, delayTime};
  deviceSettings.setPowerPolicy(wantTemp, powerScene, powerPolicy);
  console.info(`Succeeded in setting power policy`);
} catch (err) {
  console.error(`Failed to set power policy. Code: ${err.code}, message: ${err.message}`);
}

```

