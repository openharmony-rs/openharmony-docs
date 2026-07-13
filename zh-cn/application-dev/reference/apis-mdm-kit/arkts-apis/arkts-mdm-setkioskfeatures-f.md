# setKioskFeatures

## setKioskFeatures

```TypeScript
function setKioskFeatures(admin: Want, features: Array<KioskFeature>): void
```

设置Kiosk模式的特征。通过本接口可以控制在Kiosk模式下能否进入通知中心、控制中心。

从API version 24开始，新增支持设置是否允许底部上滑进入最近任务栏，左滑或右滑悬停展示侧边DOCK栏。

在非Kiosk模式下，本接口可以正常调用，但是不会生效，进入Kiosk模式后才会生效。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_SET_KIOSK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| features | Array&lt;KioskFeature&gt; | 是 | Kiosk模式的特征集合（从API version 24开始，新增允许底部上滑进入最近任务栏、左滑悬停或右滑悬停展示侧边DOCK栏）。 <br>当传入空数组时，系统会清空之前下发过的特征，恢复到Kiosk模式的默认状态。即：禁用通知中心、控制中心、最近任务栏、侧边Dock栏等能力。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | The parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permissionrequired to call the API. |

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

