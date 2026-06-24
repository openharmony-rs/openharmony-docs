# getAlternateIcons

## getAlternateIcons

```TypeScript
function getAlternateIcons(): Promise<Array<AlternateIconInfo>>
```

��ѯ��ǰӦ����app.json5��[alternateIcons��ǩ](../../../../quick-start/app-configuration-file.md#alternateicons��ǩ)���õı���ͼ����Ϣ��ʹ��
Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AlternateIconInfo&gt;&gt; | Promise���󣬷��ص�ǰӦ�õı���ͼ����Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700311](../../errorcode-universal.md#17700311-Failed) | Failed to obtain the alternate icon. |

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

