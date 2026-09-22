# filterBundleListByDeviceModeDistributionPolicies（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## filterBundleListByDeviceModeDistributionPolicies

```TypeScript
function filterBundleListByDeviceModeDistributionPolicies(
    policies: Array<DeviceModeDistributionPolicy>
  ): Promise<void>
```

支持按设备模式分发策略过滤应用列表。该接口使用promise返回结果。

> **说明：** 
> 
> 入参不能为空。所有值必须在的枚举值范围内。
> DeviceModeDistributePolicy，以及所有不同套餐的策略（通用差分包、部分兼容差分包和全兼容差分包）必须包含。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.SWITCH_MULTI_MODE_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policies | Array&lt;[DeviceModeDistributionPolicy](arkts-ability-bundlemanager-devicemodedistributionpolicy-e-sys.md)&gt; | 是 | DeviceModeDistributionPolicy值的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise 对象，无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Non-system APP calling system API. |
| [17700097](../errorcode-bundle.md#17700097-设备不支持双模式) | The device does not support the dual mode. |
| [17700098](../errorcode-bundle.md#17700098-入参无效) | The input parameter is invalid. It is either outside the range of valid enum values or does not include the following required enum values: [DeviceModeDistributionPolicy.UNIVERSAL_DIFFERENT_PACKAGE, DeviceModeDistributionPolicy.PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE, DeviceModeDistributionPolicy.FULL_COMPATIBLE_DIFFERENT_PACKAGE]. |
| [17700099](../errorcode-bundle.md#17700099-设备正在安装卸载应用或双模切换正在处理中) | The device is installing or uninstalling an application, or a previous API call is still being processed. Please try again. |

**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let policies: Array<bundleManager.DeviceModeDistributionPolicy> = [
  bundleManager.DeviceModeDistributionPolicy.UNIVERSAL_DIFFERENT_PACKAGE,
  bundleManager.DeviceModeDistributionPolicy.PARTIAL_COMPATIBLE_DIFFERENT_PACKAGE,
  bundleManager.DeviceModeDistributionPolicy.FULL_COMPATIBLE_DIFFERENT_PACKAGE
];

try {
  bundleManager.filterBundleListByDeviceModeDistributionPolicies(policies).then(() => {
    hilog.info(0x0000, 'testTag', 'filterBundleListByDeviceModeDistributionPolicies successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'filterBundleListByDeviceModeDistributionPolicies failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'filterBundleListByDeviceModeDistributionPolicies failed. Cause: %{public}s', message);
}
```
