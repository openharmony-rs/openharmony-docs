# getPluginBundlePathForSelf

## getPluginBundlePathForSelf

```TypeScript
function getPluginBundlePathForSelf(pluginBundleName: string): string
```

��ȡָ������ڵ�ǰ[Ӧ��ɳ��](../../../../file-management/app-sandbox-directory.md)�ڵİ�װ·����

**起始版本：** 22

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pluginBundleName | string | 是 | Ŀ�����İ����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Ŀ�����ڵ�ǰӦ��ɳ���ڵİ�װ·���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |

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

