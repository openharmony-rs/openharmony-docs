# getApplicationLabel

## getApplicationLabel

```TypeScript
function getApplicationLabel(bundleName: string, appIndex: number): Promise<string>
```

获取指定包名和分身索引的应用名称。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用的包名。 |
| appIndex | number | 是 | 表示应用索引。取值范围0~5，取值为0表示主应用，取值1~5表示分身应用的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，调用成功返回应用名称；调用失败返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle is not found. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getApplicationLabel('com.hap.myapplication', 1).then((data: string) => {
    hilog.info(0x0000, 'testTag', 'getApplicationLabel succeed: Data: %{public}s', data);
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getApplicationLabel failed: %{public}d  %{public}s', err.code, err.message);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getApplicationLabel failed: error %{public}d  %{public}s', err.code, err.message);
}

```

