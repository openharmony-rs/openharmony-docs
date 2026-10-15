# setAppClonePreference（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## setAppClonePreference

```TypeScript
function setAppClonePreference(bundleName: string, appClonePreference: AppClonePreference): Promise<void>
```

根据给定的bundleName设置应用分身偏好设置。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_CLONE_BUNDLE_PREFERENCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function setAppClonePreference(bundleName: string, appClonePreference: AppClonePreference): Promise<void>--><!--Device-bundleManager-function setAppClonePreference(bundleName: string, appClonePreference: AppClonePreference): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示目标应用的bundleName。 |
| appClonePreference | [AppClonePreference](arkts-ability-bundlemanager-appclonepreference-t-sys.md) | 是 | 表示要设置的应用分身偏好设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |
| [17700094](../errorcode-bundle.md#17700094-指定的应用未创建分身) | The specified bundle did not create a clone. |

<!--Del-->
**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let appClonePreference: bundleManager.AppClonePreference = {
  mode: bundleManager.AppClonePreferenceMode.CLONE_APP,
  appIndex: 1
};

try {
  bundleManager.setAppClonePreference(bundleName, appClonePreference).then(() => {
    hilog.info(0x0000, 'testTag', 'setAppClonePreference successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'setAppClonePreference failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setAppClonePreference failed. Cause: %{public}s', message);
}
```

<!--DelEnd-->
