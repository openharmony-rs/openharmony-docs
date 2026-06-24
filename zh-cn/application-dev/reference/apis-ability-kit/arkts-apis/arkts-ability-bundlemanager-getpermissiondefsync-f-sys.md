# getPermissionDefSync（系统接口）

## getPermissionDefSync

```TypeScript
function getPermissionDefSync(permissionName: string): PermissionDef
```

��ͬ���������ݸ�����permissionName��ȡȨ�޶���ṹ��PermissionDef��Ϣ��

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | string | 是 | ��ʾȨ�޲������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PermissionDef | PermissionDef���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700006](../../errorcode-universal.md#17700006-The) | The specified permission is not found. |

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

