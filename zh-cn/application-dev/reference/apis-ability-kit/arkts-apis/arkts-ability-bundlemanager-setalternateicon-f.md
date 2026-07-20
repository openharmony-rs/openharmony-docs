# setAlternateIcon

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

<a id="setalternateicon"></a>
## setAlternateIcon

```TypeScript
function setAlternateIcon(alternateIconName: string): Promise<void>
```

根据给定的备用图标名称设置调用方自身的备用图标。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function setAlternateIcon(alternateIconName: string): Promise<void>--><!--Device-bundleManager-function setAlternateIcon(alternateIconName: string): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alternateIconName | string | 是 | 要设置的备用图标名称。备用图标名称须在app.json5中[alternateIcons标签](docroot://quick-start/app-configuration-file.md#alternateicons标签)的name字段内。<br/>alternateIconName为空时表示取消备用图标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700308](../errorcode-bundle.md#17700308-备用图标名称没有在配置文件中配置) | The alternateIconName must match the name field under alternateIcons in the app.json5 file. |
| [17700309](../errorcode-bundle.md#17700309-当前没有设置备用图标) | No alternate icon is enabled. |
| [17700310](../errorcode-bundle.md#17700310-设置备用图标失败) | Failed to set the alternate icon. |

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

