# getPluginBundlePathForSelf

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getPluginBundlePathForSelf

```TypeScript
function getPluginBundlePathForSelf(pluginBundleName: string): string
```

获取指定插件在当前[应用沙箱](../../../file-management/app-sandbox-directory.md)内的安装路径。

**起始版本：** 22

<!--Device-bundleManager-function getPluginBundlePathForSelf(pluginBundleName: string): string--><!--Device-bundleManager-function getPluginBundlePathForSelf(pluginBundleName: string): string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pluginBundleName | string | 是 | 目标插件的包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 目标插件在当前应用沙箱内的安装路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 请开发者替换为实际插件对应的包名
let pluginBundleName = 'com.ohos.pluginDemo';
try {
  let path = bundleManager.getPluginBundlePathForSelf(pluginBundleName);
  hilog.info(0x0000, 'testTag', 'getPluginBundlePathForSelf successfully. path: %{public}s', path);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getPluginBundlePathForSelf failed. Cause: %{public}s', message);
}

```

