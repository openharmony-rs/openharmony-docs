# getLauncherAbilityInfoSync

## getLauncherAbilityInfoSync

```TypeScript
function getLauncherAbilityInfoSync(bundleName: string, userId: int): Array<LauncherAbilityInfo>
```

查询指定bundleName及用户的[LauncherAbilityInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-launcherBundleManager-function getLauncherAbilityInfoSync(bundleName: string, userId: int): Array<LauncherAbilityInfo>--><!--Device-launcherBundleManager-function getLauncherAbilityInfoSync(bundleName: string, userId: int): Array<LauncherAbilityInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| userId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 被查询的用户ID，可以通过[getOsAccountLocalId接口]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;LauncherAbilityInfo&gt; | Array形式返回bundle包含的 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

**示例：**

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

