# isFingerprintAuthDisabled（系统接口）

## 导入模块

```TypeScript
import { restrictions } from '@kit.MDMKit';
```

## isFingerprintAuthDisabled

```TypeScript
function isFingerprintAuthDisabled(admin: Want): boolean
```

查询指纹认证是否被禁用。

**起始版本：** 11

**废弃版本：** 26.0.0

**替代接口：** [getDisallowedPolicy(admin:](arkts-mdm-restrictions-getdisallowedpolicy-f.md#getdisallowedpolicy)

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-restrictions-function isFingerprintAuthDisabled(admin: Want): boolean--><!--Device-restrictions-function isFingerprintAuthDisabled(admin: Want): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指纹认证是否被禁用，true表示指纹认证被禁用，false表示指纹认证未被禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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

