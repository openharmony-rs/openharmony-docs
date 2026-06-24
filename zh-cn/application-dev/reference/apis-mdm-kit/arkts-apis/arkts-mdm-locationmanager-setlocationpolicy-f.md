# setLocationPolicy

## setLocationPolicy

```TypeScript
function setLocationPolicy(admin: Want, policy: LocationPolicy): void
```

����λ�÷���������ԡ�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_LOCATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| policy | LocationPolicy | 是 | λ�÷�����ԡ�<br/>- 0��Ĭ�ϲ��ԡ�<br/>- 1�����á�<br/>- 2��ǿ�����á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { locationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  locationManager.setLocationPolicy(wantTemp, locationManager.LocationPolicy.DISALLOW_LOCATION_SERVICE);
  console.info(`Succeeded in setting location patch tag.`);
} catch(err) {
  console.error(`Failed to set location policy. Code: ${err.code}, message: ${err.message}`);
}

```

