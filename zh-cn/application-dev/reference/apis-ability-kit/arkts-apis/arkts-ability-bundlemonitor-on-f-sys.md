# on（系统接口）

## on

```TypeScript
function on(type: BundleChangedEvent, callback: Callback<BundleChangedInfo>): void
```

注册监听应用的安装、卸载、更新。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | BundleChangedEvent | 是 | 注册监听的事件类型。 |
| callback | Callback&lt;BundleChangedInfo&gt; | 是 | 回调函数，当回调成功时，err为undefined，data为应用变更信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Verify) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```TypeScript
import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callbackFun = (bundleChangeInfo: bundleMonitor.BundleChangedInfo) => {
  console.info(`bundleName : ${bundleChangeInfo.bundleName} userId : ${bundleChangeInfo.userId}`);
};
try {
  bundleMonitor.on('add', callbackFun);
} catch (errData) {
  let message = (errData as BusinessError).message;
  let errCode = (errData as BusinessError).code;
  console.error(`errData is errCode:${errCode}  message:${message}`);
}

```

