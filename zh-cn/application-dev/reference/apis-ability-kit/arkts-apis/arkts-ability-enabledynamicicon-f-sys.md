# enableDynamicIcon（系统接口）

## enableDynamicIcon

```TypeScript
function enableDynamicIcon(bundleName: string, moduleName: string): Promise<void>
```

根据给定的bundleName、moduleName使能动态图标。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_DYNAMIC_ICON

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要使能动态图标的应用名称。 |
| moduleName | string | 是 | 要使能动态图标的模块名称。 |

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
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified moduleName is not found. |
| [17700304](../errorcode-bundle.md#17700304-动态图标使能失败) | Failed to enable the dynamic icon. |
| [17700307](../errorcode-bundle.md#17700307-由于存在自定义主题动态图标无法生效) | Dynamic icons cannot take effect due to existing custom themes.<br>**适用版本：** 20+ |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';
let moduleName: string = 'moduleTest';

try {
  bundleManager.enableDynamicIcon(bundleName, moduleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'enableDynamicIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', message);
}

```


## enableDynamicIcon

```TypeScript
function enableDynamicIcon(bundleName: string, moduleName: string, option?: BundleOptions): Promise<void>
```

根据给定的bundleName、moduleName和option使能动态图标。使用Promise异步回调。

使能当前用户下的动态图标信息时需要申请权限ohos.permission.ACCESS_DYNAMIC_ICON。

使能其他用户下的动态图标信息时需要申请权限ohos.permission.ACCESS_DYNAMIC_ICON 和 ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_DYNAMIC_ICON or (ohos.permission.ACCESS_DYNAMIC_ICON and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要使能动态图标的应用包名。 |
| moduleName | string | 是 | 要使能动态图标的模块名。 |
| option | BundleOptions | 否 | 指定需要使能动态图标的用户和分身索引。缺省时使能应用所有用户和所有分身的动态图标。 |

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
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified moduleName is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range. |
| [17700304](../errorcode-bundle.md#17700304-动态图标使能失败) | Failed to enable the dynamic icon. |
| [17700307](../errorcode-bundle.md#17700307-由于存在自定义主题动态图标无法生效) | Dynamic icons cannot take effect due to existing custom themes. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';
let moduleName: string = 'moduleTest';
let option: bundleManager.BundleOptions = { 'userId': 100, 'appIndex': 0 };

try {
  bundleManager.enableDynamicIcon(bundleName, moduleName, option).then(() => {
    hilog.info(0x0000, 'testTag', 'enableDynamicIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', message);
}

```

