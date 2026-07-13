# checkPermissionInUse（系统接口）

## checkPermissionInUse

```TypeScript
function checkPermissionInUse(permissionName: Permissions): boolean
```

查询指定敏感权限是否正在被使用，可用于权限管理界面展示权限实时使用状态场景。
判断依据为当前是否存在通过[startUsingPermission](arkts-ability-startusingpermission-f-sys.md#startusingpermission-1)
标记开始使用且尚未通过[stopUsingPermission](arkts-ability-stopusingpermission-f-sys.md#stopusingpermission-1)标记停止使用的活跃调用。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.PERMISSION_USED_STATS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | Permissions | 是 | 需要查询的权限名称。权限名不能为空，且长度不能超过256个字符，传入无效值时返回错误码12100001。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 指定的敏感权限是否正在被使用。true：指定的敏感权限正在被使用；false：指定的敏感权限未被使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system application. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The permissionName is empty or exceeds 256 characters. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user_grant permission. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 查询指定权限是否正在被使用
  let isPermissionInUse = privacyManager.checkPermissionInUse('ohos.permission.CAMERA');
  console.info('checkPermissionInUse success, result: ' + isPermissionInUse);
} catch (err) {
  let error = err as BusinessError;
  console.error(`checkPermissionInUse fail, code: ${error.code}, message: ${error.message}`);
}

```

