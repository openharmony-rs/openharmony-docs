# getLauncherAbilityInfoSync

## getLauncherAbilityInfoSync

```TypeScript
function getLauncherAbilityInfoSync(bundleName: string, userId: int): Array<LauncherAbilityInfo>
```

查询指定bundleName及用户的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-launcherBundleManager-function getLauncherAbilityInfoSync(bundleName: string, userId: int): Array<LauncherAbilityInfo>--><!--Device-launcherBundleManager-function getLauncherAbilityInfoSync(bundleName: string, userId: int): Array<LauncherAbilityInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| userId | int | 是 | 被查询的用户ID，可以通过 [getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;LauncherAbilityInfo&gt; | Array形式返回bundle包含的 [LauncherAbilityInfo]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |

## 示例

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let launcherAbilityInfos = launcherBundleManager.getLauncherAbilityInfoSync("com.example.demo", 100);
  console.info("data is " + JSON.stringify(launcherAbilityInfos));
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

