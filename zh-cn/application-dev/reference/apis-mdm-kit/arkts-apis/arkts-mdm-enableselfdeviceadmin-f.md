# enableSelfDeviceAdmin

## enableSelfDeviceAdmin

```TypeScript
function enableSelfDeviceAdmin(admin: Want, credential: string): Promise<void>
```

在企业设备中，MDM应用没有预置激活的场景下，MDM应用可以通过该接口实现自激活。该接口仅支持激活MDM应用自身，不支持激活其他MDM应用；支持的激活类型包括超级设备管理应用和普通设备管理应用。

<!--RP1--><!--RP1End-->

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_ACTIVATE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| credential | string | 是 | 激活凭证。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the enableSelfDeviceAdmin. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200003](../errorcode-enterpriseDeviceManager.md#9200003-指定的设备管理器元能力组件无效) | The administrator ability component is invalid. |
| [9200004](../errorcode-enterpriseDeviceManager.md#9200004-激活设备管理器失败) | Failed to activate the administrator application of the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200017](../errorcode-enterpriseDeviceManager.md#9200017-企业设备管理员自激活凭证无效) | The self-activation credential of the enterprise device administratoris invalid. |
| [9200018](../errorcode-enterpriseDeviceManager.md#9200018-该设备非企业设备) | This device is not an enterprise device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { adminManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 需根据实际情况进行替换
let credential: string = '{"enterpriseId": "123456", "appIdentifier": "123456", "type": "SDA", "sign": "", "certs": []}';

try {
  adminManager.enableSelfDeviceAdmin(wantTemp, credential);
  console.info(`succeed in enable self device admin.`);
} catch (err) {
  console.error(`Failed to enable self device admin. Code: ${err.code}, message: ${err.message}`);
}

```

