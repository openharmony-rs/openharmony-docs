# getPermissionDefSync（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

<a id="getpermissiondefsync"></a>
## getPermissionDefSync

```TypeScript
function getPermissionDefSync(permissionName: string): PermissionDef
```

以同步方法根据给定的permissionName获取权限定义结构体PermissionDef信息。

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getPermissionDefSync(permissionName: string): PermissionDef--><!--Device-bundleManager-function getPermissionDefSync(permissionName: string): PermissionDef-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | string | 是 | 表示权限参数名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PermissionDef](arkts-ability-permissiondef-i-sys.md) | PermissionDef对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700006](../errorcode-bundle.md#17700006-查询的权限不存在) | The specified permission is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let permissionName = "ohos.permission.GET_BUNDLE_INFO";
try {
  let PermissionDef = bundleManager.getPermissionDefSync(permissionName);
  hilog.info(0x0000, 'testTag', 'getPermissionDefSync successfully. Data: %{public}s', JSON.stringify(PermissionDef));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getPermissionDefSync failed. Cause: %{public}s', message);
}

```

