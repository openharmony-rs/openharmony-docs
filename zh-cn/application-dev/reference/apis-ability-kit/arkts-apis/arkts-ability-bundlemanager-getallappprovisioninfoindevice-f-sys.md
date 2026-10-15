# getAllAppProvisionInfoInDevice（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllAppProvisionInfoInDevice

```TypeScript
function getAllAppProvisionInfoInDevice(userId: number): Promise<Array<AppProvisionInfo>>
```

获取所有应用的provision配置文件信息基于设备中给定的用户ID。该接口使用promise返回结果。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST or (ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getAllAppProvisionInfoInDevice(userId: int): Promise<Array<AppProvisionInfo>>--><!--Device-bundleManager-function getAllAppProvisionInfoInDevice(userId: int): Promise<Array<AppProvisionInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | <br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AppProvisionInfo](arkts-ability-bundlemanager-appprovisioninfo-t-sys.md)&gt;&gt; | Promise用于返回获取到的provision profile。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied. A non-system application is not allowed to call a system API. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user id is not found. |

<!--Del-->
**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let userId = 100;

try {
  bundleManager.getAllAppProvisionInfoInDevice(userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllAppProvisionInfoInDevice successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllAppProvisionInfoInDevice failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllAppProvisionInfoInDevice failed. Cause: %{public}s', message);
}
```

<!--DelEnd-->
