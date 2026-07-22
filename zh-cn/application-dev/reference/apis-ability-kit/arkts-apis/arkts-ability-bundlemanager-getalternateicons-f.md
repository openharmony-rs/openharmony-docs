# getAlternateIcons

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAlternateIcons

```TypeScript
function getAlternateIcons(): Promise<Array<AlternateIconInfo>>
```

查询当前应用在app.json5中[alternateIcons标签](../../../quick-start/app-configuration-file.md#alternateicons标签)配置的备用图标信息。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getAlternateIcons(): Promise<Array<AlternateIconInfo>>--><!--Device-bundleManager-function getAlternateIcons(): Promise<Array<AlternateIconInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AlternateIconInfo&gt;&gt; | Promise对象，返回当前应用的备用图标信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700311](../errorcode-bundle.md#17700311-查询备用图标失败) | Failed to obtain the alternate icon. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getAlternateIcons().then((data) => {
    hilog.info(0x0000, 'testTag', 'getAlternateIcons successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAlternateIcons failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAlternateIcons failed. Cause: %{public}s', message);
}

```

