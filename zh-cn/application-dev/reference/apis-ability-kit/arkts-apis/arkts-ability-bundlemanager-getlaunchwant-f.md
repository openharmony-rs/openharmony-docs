# getLaunchWant

## getLaunchWant

```TypeScript
function getLaunchWant(): Want
```

获取本应用\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的Want参数。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-bundleManager-function getLaunchWant(): Want--><!--Device-bundleManager-function getLaunchWant(): Want-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回仅包含bundleName和abilityName的Want对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700072](../errorcode-bundle.md#17700072-launch-want不存在) | The launch want is not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let want = bundleManager.getLaunchWant();
  hilog.info(0x0000, 'testTag', 'getLaunchWant ability name: %{public}s', want.abilityName);
  hilog.info(0x0000, 'testTag', 'getLaunchWant bundle name: %{public}s', want.bundleName);
} catch (error) {
  let message = (error as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLaunchWant failed: %{public}s', message);
}
```

