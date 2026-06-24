# isFingerprintAuthDisabled（系统接口）

## isFingerprintAuthDisabled

```TypeScript
function isFingerprintAuthDisabled(admin: Want): boolean
```

��ѯָ����֤�Ƿ񱻽��á�

**起始版本：** 11

**废弃版本：** 26.0.0

**替代接口：** getDisallowedPolicy(admin:

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ����ָ����֤�Ƿ񱻽��ã�true��ʾָ����֤�����ã�false��ʾָ����֤δ�����á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: boolean = restrictions.isFingerprintAuthDisabled(wantTemp);
  console.info(`Succeeded in getting the state of fingerprint auth. result : ${result}`);
} catch (err) {
  console.error(`Failed to get the state of fingerprint auth. Code: ${err.code}, message: ${err.message}`);
};

```

