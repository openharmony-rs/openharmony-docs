# getDynamicIcon（系统接口）

## getDynamicIcon

```TypeScript
function getDynamicIcon(bundleName: string): Promise<string>
```

根据给定的bundleName获得动态图标对应的moduleName。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundleManager-function getDynamicIcon(bundleName: string): Promise<string>--><!--Device-bundleManager-function getDynamicIcon(bundleName: string): Promise<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询扩展资源的应用名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回接口运行结果及动态图标对应的moduleName。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700306](../errorcode-bundle.md#17700306-动态图标查询失败) | Failed to obtain the dynamic icon. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';

try {
  bundleManager.getDynamicIcon(bundleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getDynamicIcon successfully %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getDynamicIcon failed. Cause: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
// 开发者需根据实际工程更新bundleName。
let bundleName : string = 'com.ohos.demo';

try {
  bundleManager.getDynamicIcon(bundleName).then((data: string) => {
    hilog.info(0x0000, 'testTag', 'getDynamicIcon successfully %s', JSON.stringify(data));
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'getDynamicIcon failed. Cause: %{public}s', (err as BusinessError).message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getDynamicIcon failed. Cause: %{public}s', message);
}
```

