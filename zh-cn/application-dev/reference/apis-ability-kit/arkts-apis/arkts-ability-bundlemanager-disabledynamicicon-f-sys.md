# disableDynamicIcon（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

<a id="disabledynamicicon"></a>
## disableDynamicIcon

```TypeScript
function disableDynamicIcon(bundleName: string): Promise<void>
```

根据给定的bundleName禁用动态图标。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_DYNAMIC_ICON

<!--Device-bundleManager-function disableDynamicIcon(bundleName: string): Promise<void>--><!--Device-bundleManager-function disableDynamicIcon(bundleName: string): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要禁用动态图标的应用名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700305](../errorcode-bundle.md#17700305-动态图标去使能失败) | Failed to disable the dynamic icon. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';

try {
  bundleManager.disableDynamicIcon(bundleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'disableDynamicIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'disableDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'disableDynamicIcon failed. Cause: %{public}s', message);
}

```


<a id="disabledynamicicon-1"></a>
## disableDynamicIcon

```TypeScript
function disableDynamicIcon(bundleName: string, option?: BundleOptions): Promise<void>
```

根据给定的bundleName和option禁用动态图标。使用Promise异步回调。

禁用当前用户下的动态图标信息时需要申请权限ohos.permission.ACCESS_DYNAMIC_ICON。

禁用其他用户下的动态图标信息时需要申请权限ohos.permission.ACCESS_DYNAMIC_ICON 和 ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_DYNAMIC_ICON or (ohos.permission.ACCESS_DYNAMIC_ICON and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

<!--Device-bundleManager-function disableDynamicIcon(bundleName: string, option?: BundleOptions): Promise<void>--><!--Device-bundleManager-function disableDynamicIcon(bundleName: string, option?: BundleOptions): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要禁用动态图标的应用包名。 |
| option | [BundleOptions](arkts-ability-bundle-bundleoptions-i.md) | 否 | 指定需要禁用动态图标的用户和分身索引。缺省时禁用应用所有用户和所有分身的动态图标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range. |
| [17700305](../errorcode-bundle.md#17700305-动态图标去使能失败) | Failed to disable the dynamic icon. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';
let option: bundleManager.BundleOptions = { 'userId': 100, 'appIndex': 0 };

try {
  bundleManager.disableDynamicIcon(bundleName, option).then(() => {
    hilog.info(0x0000, 'testTag', 'disableDynamicIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'disableDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'disableDynamicIcon failed. Cause: %{public}s', message);
}

```

