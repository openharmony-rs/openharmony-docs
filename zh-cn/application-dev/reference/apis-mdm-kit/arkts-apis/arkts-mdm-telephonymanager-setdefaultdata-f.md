# setDefaultData

## 导入模块

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

<a id="setdefaultdata"></a>
## setDefaultData

```TypeScript
function setDefaultData(admin: Want, slotId: number): void
```

设置指定卡槽的SIM卡为默认数据流量卡，设备将使用指定卡槽的SIM卡流量上网。该接口需要插入SIM卡并关闭飞行模式才能成功调用。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-telephonyManager-function setDefaultData(admin: Want, slotId: number): void--><!--Device-telephonyManager-function setDefaultData(admin: Want, slotId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| slotId | number | 是 | 卡槽ID，目前仅支持单卡槽设备和双卡槽设备，取值范围为0或1，其中0表示卡槽1，1表示卡槽2。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9201020](../errorcode-enterpriseDeviceManager.md#9201020-设置默认数据流量卡失败) | Failed to set the default data SIM card.The airplane mode is enabled or no SIM card is inserted. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 设置要作为默认数据流量卡的卡槽ID
let slotId: number = 0;
try {
  // 设置指定卡槽为默认数据流量卡
  telephonyManager.setDefaultData(wantTemp, slotId);
  console.info(`success to set default data SIM ID`);
} catch (err) {
  console.error(`Failed to set default data. Code: ${err.code}, message: ${err.message}`);
}

```

