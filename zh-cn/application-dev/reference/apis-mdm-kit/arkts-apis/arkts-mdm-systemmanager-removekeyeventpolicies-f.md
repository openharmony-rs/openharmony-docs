# removeKeyEventPolicies

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## removeKeyEventPolicies

```TypeScript
function removeKeyEventPolicies(admin: Want, keyCodes: Array<KeyCode>): void
```

删除按键事件处理策略。

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-systemManager-function removeKeyEventPolicies(admin: Want, keyCodes: Array<KeyCode>): void--><!--Device-systemManager-function removeKeyEventPolicies(admin: Want, keyCodes: Array<KeyCode>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| keyCodes | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<KeyCode> | 是 | 按键编码。支持一次删除多条按键策略，删除不支持按键时返回9200012错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let keyCodes: Array<systemManager.KeyCode> = [
  systemManager.KeyCode.POWER, systemManager.KeyCode.VOLUME_UP,
];

try {
  systemManager.removeKeyEventPolicies(wantTemp, keyCodes);
  console.info('Succeeded in removing key event policies.');
} catch (err) {
  console.error(`Failed to remove key event policies. Code is ${err.code}, message is ${err.message}`);
}

```

