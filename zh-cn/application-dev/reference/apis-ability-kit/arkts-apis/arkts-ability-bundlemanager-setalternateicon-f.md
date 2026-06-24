# setAlternateIcon

## setAlternateIcon

```TypeScript
function setAlternateIcon(alternateIconName: string): Promise<void>
```

���ݸ����ı���ͼ���������õ��÷������ı���ͼ�ꡣʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alternateIconName | string | 是 | Ҫ���õı���ͼ�����ơ�����ͼ����������app.json5��<br/>[alternateIcons��ǩ](../../../../quick-start/app-configuration-file.md#alternateicons��ǩ)��name�ֶ��ڡ�<br/><br/>alternateIconNameΪ��ʱ��ʾȡ������ͼ�ꡣ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700308](../../errorcode-universal.md#17700308-The) | The alternateIconName must match the name field under alternateIcons<br/>in the app.json5 file. |
| [17700309](../../errorcode-universal.md#17700309-No) | No alternate icon is enabled. |
| [17700310](../../errorcode-universal.md#17700310-Failed) | Failed to set the alternate icon. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// alternateIconName需要替换为要设置的备用图标名称
let alternateIconName: string = 'com.ohos.demo';

try {
  bundleManager.setAlternateIcon(alternateIconName).then((data) => {
    hilog.info(0x0000, 'testTag', 'setAlternateIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'setAlternateIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setAlternateIcon failed. Cause: %{public}s', message);
}

```

