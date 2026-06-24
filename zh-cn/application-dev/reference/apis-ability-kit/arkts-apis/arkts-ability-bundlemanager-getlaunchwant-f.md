# getLaunchWant

## getLaunchWant

```TypeScript
function getLaunchWant(): Want
```

��ȡ��Ӧ��[���UIAbility](../../../../quick-start/application-package-glossary.md#uiability)��Want������

**起始版本：** 13

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Want | ���ؽ�����bundleName��abilityName��Want���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700072](../../errorcode-universal.md#17700072-The) | The launch want is not found. |

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

