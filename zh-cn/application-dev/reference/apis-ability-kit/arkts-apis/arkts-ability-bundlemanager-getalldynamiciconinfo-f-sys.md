# getAllDynamicIconInfo（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllDynamicIconInfo

```TypeScript
function getAllDynamicIconInfo(userId?: number): Promise<Array<DynamicIconInfo>>
```

查询指定用户下所有应用和所有分身的动态图标信息。使用Promise异步回调。

查询当前用户下所有应用和所有分身的动态图标信息时需要申请权限ohos.permission.GET_BUNDLE_INFO_PRIVILEGED。

查询其他用户或者所有用户下所有应用和所有分身的动态图标信息时需要申请权限ohos.permission.GET_BUNDLE_INFO_PRIVILEGED 和ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS。

**起始版本：** 20

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-bundleManager-function getAllDynamicIconInfo(userId?: int): Promise<Array<DynamicIconInfo>>--><!--Device-bundleManager-function getAllDynamicIconInfo(userId?: int): Promise<Array<DynamicIconInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 否 | 标识用户ID。缺省时查询所有用户下所有应用和所有分身的动态图标信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<DynamicIconInfo>> | Promise对象，返回查询到的动态图标信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700306](../errorcode-bundle.md#17700306-动态图标查询失败) | Failed to obtain the dynamic icon. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let userId: number = 100;

try {
  bundleManager.getAllDynamicIconInfo(userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllDynamicIconInfo successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllDynamicIconInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllDynamicIconInfo failed. Cause: %{public}s', message);
}

```

