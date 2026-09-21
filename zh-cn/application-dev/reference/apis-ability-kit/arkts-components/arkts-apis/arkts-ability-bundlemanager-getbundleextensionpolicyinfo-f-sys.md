# getBundleExtensionPolicyInfo（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getBundleExtensionPolicyInfo

```TypeScript
function getBundleExtensionPolicyInfo(bundleName: string, userId: number): BundleExtensionPolicyInfo
```

获取指定应用的包扩展策略信息。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or (ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示应用的包名。 |
| userId | number | 是 | 用户ID，可通过调用getOsAccountLocalId获取。值大于等于0。<br>该值应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BundleExtensionPolicyInfo](arkts-ability-bundlemanager-bundleextensionpolicyinfo-t-sys.md) | 返回包扩展策略信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Non-system APP calling system API. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
