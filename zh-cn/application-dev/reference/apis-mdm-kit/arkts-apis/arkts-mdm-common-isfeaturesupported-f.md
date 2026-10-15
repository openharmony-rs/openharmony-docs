# isFeatureSupported

## 导入模块

```TypeScript
import { common } from '@kit.MDMKit';
```

## isFeatureSupported

```TypeScript
function isFeatureSupported(feature: ManagedFeature): boolean
```

查询是否支持某个管控特性

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-common-function isFeatureSupported(feature: ManagedFeature): boolean--><!--Device-common-function isFeatureSupported(feature: ManagedFeature): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| feature | [ManagedFeature](arkts-mdm-common-managedfeature-e.md) | 是 | 管控特性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示支持该特性，fasle表示不支持该特性。 |

**示例**

```TypeScript
import { common, systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// 需根据实际情况进行替换
let domain: string = "https://www.hotaExample.com";
// 调用接口前，先使用本接口查询设备是否支持本机HOTA域名特性
let isSupported: boolean = common.isFeatureSupported(common.ManagedFeature.LOCAL_HOTA_DOMAIN);
if (isSupported) {
  try {
    systemManager.setLocalHotaDomain(wantTemp, domain);
    console.info('Succeeded in setting local HOTA domain.');
  } catch (err) {
    console.error(`Failed to set local HOTA domain. Code is ${err.code}, message is ${err.message}`);
  }
} else {
  console.info('The local HOTA domain feature is not supported.');
}
```
