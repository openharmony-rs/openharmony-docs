# getAppClonePreference（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAppClonePreference

```TypeScript
function getAppClonePreference(bundleName: string): Promise<AppClonePreference>
```

根据给定的bundleName查询应用分身偏好设置。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_CLONE_BUNDLE_PREFERENCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getAppClonePreference(bundleName: string): Promise<AppClonePreference>--><!--Device-bundleManager-function getAppClonePreference(bundleName: string): Promise<AppClonePreference>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示目标应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AppClonePreference](arkts-ability-bundlemanager-appclonepreference-t-sys.md)&gt; | Promise对象，返回应用的分身偏好设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700095](../errorcode-bundle.md#17700095-指定的应用未找到分身偏好) | The specified bundle not found app clone preference. |

<!--Del-->
**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';

try {
  bundleManager.getAppClonePreference(bundleName).then((res: bundleManager.AppClonePreference) => {
    hilog.info(0x0000, 'testTag', 'getAppClonePreference res: AppClonePreference = %{public}s',
      JSON.stringify(res));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAppClonePreference failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppClonePreference failed. Cause: %{public}s', message);
}
```

<!--DelEnd-->
