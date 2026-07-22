# disableDeviceAdmin

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## disableDeviceAdmin

```TypeScript
function disableDeviceAdmin(admin: Want): Promise<void>
```

[超级设备管理应用](../../../mdm/mdm-kit-term.md#sda)通过该接口可以解除激活其他[普通设备管理应用](../../../mdm/mdm-kit-term.md#da)，使用Promise异步回调。该接口仅支持超级设备管理应用调用。

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_DEVICE_ADMIN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function disableDeviceAdmin(admin: Want): Promise<void>--><!--Device-adminManager-function disableDeviceAdmin(admin: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。当解除激活设备管理应用失败时，会抛出错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200005](../errorcode-enterpriseDeviceManager.md#9200005-解除激活设备管理器失败) | Failed to deactivate the administrator application of the device. |
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

adminManager.disableDeviceAdmin(wantTemp).catch((err: BusinessError) => {
  console.error(`Failed to disable device admin. Code: ${err.code}, message: ${err.message}`);
});

```

