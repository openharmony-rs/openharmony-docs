# onRemove（系统接口）

## onRemove

```TypeScript
function onRemove(callback: Callback<BundleChangedInfo>): void
```

注册监听应用的卸载。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-bundleMonitor-function onRemove(callback: Callback<BundleChangedInfo>): void--><!--Device-bundleMonitor-function onRemove(callback: Callback<BundleChangedInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;BundleChangedInfo&gt; | 是 | 注册监听的AsyncCallback |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例：**

```TypeScript
'use static'

import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  bundleMonitor.onRemove((bundleChangeInfo) => {
    console.info(`bundleName : ${bundleChangeInfo.bundleName} userId : ${bundleChangeInfo.userId}`);
  })
} catch (errData) {
  let message = (errData as BusinessError).message;
  let errCode = (errData as BusinessError).code;
  console.error(`errData is errCode:${errCode}  message:${message}`);
}
```

