# getPermissionDef（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getPermissionDef

```TypeScript
function getPermissionDef(permissionName: string, callback: AsyncCallback<PermissionDef>): void
```

根据给定的permissionName获取权限定义结构体PermissionDef信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getPermissionDef(permissionName: string, callback: AsyncCallback<PermissionDef>): void--><!--Device-bundleManager-function getPermissionDef(permissionName: string, callback: AsyncCallback<PermissionDef>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | string | 是 | 表示权限名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<PermissionDef> | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，当获取成功时，err为undefined，data为获取到的Array&lt;PermissionDef&gt;；否则为错误对象。 |

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

let permission = "ohos.permission.GET_BUNDLE_INFO";
try {
  bundleManager.getPermissionDef(permission, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getPermissionDef failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getPermissionDef successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getPermissionDef failed: %{public}s', message);
}

```


## getPermissionDef

```TypeScript
function getPermissionDef(permissionName: string): Promise<PermissionDef>
```

根据给定的permissionName获取权限定义结构体PermissionDef信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getPermissionDef(permissionName: string): Promise<PermissionDef>--><!--Device-bundleManager-function getPermissionDef(permissionName: string): Promise<PermissionDef>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | string | 是 | 表示权限参数名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PermissionDef> | Promise对象，返回Array&lt;PermissionDef&gt;对象。 |

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
  bundleManager.getPermissionDef(permissionName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getPermissionDef successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getPermissionDef failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getPermissionDef failed. Cause: %{public}s', message);
}

```

