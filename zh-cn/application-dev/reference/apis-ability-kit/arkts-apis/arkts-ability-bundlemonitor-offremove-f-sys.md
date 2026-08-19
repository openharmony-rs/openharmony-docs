# offRemove（系统接口）

## 导入模块

```TypeScript
import { bundleMonitor } from '@kit.AbilityKit';
```

## offRemove

```TypeScript
function offRemove(callback?: Callback<BundleChangedInfo>): void
```

注销监听应用的卸载。

**起始版本：** 23

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-bundleMonitor-function offRemove(callback?: Callback<BundleChangedInfo>): void--><!--Device-bundleMonitor-function offRemove(callback?: Callback<BundleChangedInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[BundleChangedInfo](arkts-ability-bundlemonitor-bundlechangedinfo-i-sys.md)&gt; | 否 | 注销监听的AsyncCallback，默认值：注销当前事件的所有callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例**

```TypeScript
'use static'

import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  bundleMonitor.offRemove();
} catch (errData) {
  let message = (errData as BusinessError).message;
  let errCode = (errData as BusinessError).code;
  console.error(`errData is errCode:${errCode}  message:${message}`);
}
```

