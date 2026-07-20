# off（系统接口）

## 导入模块

```TypeScript
import { bundleMonitor } from '@kit.AbilityKit';
```

<a id="off"></a>
## off

```TypeScript
function off(type: BundleChangedEvent, callback?: Callback<BundleChangedInfo>): void
```

注销监听应用的安装，卸载，更新。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-bundleMonitor-function off(type: BundleChangedEvent, callback?: Callback<BundleChangedInfo>): void--><!--Device-bundleMonitor-function off(type: BundleChangedEvent, callback?: Callback<BundleChangedInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [BundleChangedEvent](arkts-ability-bundlemonitor-bundlechangedevent-t-sys.md) | 是 | 注销监听的事件类型。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;BundleChangedInfo&gt; | 否 | 回调函数，当回调成功时，err为undefined，data为应用变更信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```TypeScript
import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 该方法变量需要和bundleMonitor.on方法是同一个，才能移除对应监听的方法，否则注销监听无效
let callbackFun = (bundleChangeInfo: bundleMonitor.BundleChangedInfo) => {
  console.info(`bundleName : ${bundleChangeInfo.bundleName} userId : ${bundleChangeInfo.userId}`);
};

try {
  bundleMonitor.off('add', callbackFun);
} catch (errData) {
  let message = (errData as BusinessError).message;
  let errCode = (errData as BusinessError).code;
  console.error(`errData is errCode:${errCode}  message:${message}`);
}

```

