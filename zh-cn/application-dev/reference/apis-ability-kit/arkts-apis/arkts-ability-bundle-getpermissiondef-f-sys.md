# getPermissionDef（系统接口）

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getPermissionDef

```TypeScript
function getPermissionDef(permissionName: string, callback: AsyncCallback<PermissionDef>): void
```

按权限名称获取权限的详细信息，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getPermissionDef(permissionName: string, callback: AsyncCallback<PermissionDef>): void--><!--Device-bundle-function getPermissionDef(permissionName: string, callback: AsyncCallback<PermissionDef>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | string | 是 | 需要查询的权限的名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<PermissionDef> | 是 | 程序启动作为入参的回调函数，返回定义的权限信息。 |


## getPermissionDef

```TypeScript
function getPermissionDef(permissionName: string): Promise<PermissionDef>
```

按权限名称获取权限的详细信息，使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getPermissionDef(permissionName: string): Promise<PermissionDef>--><!--Device-bundle-function getPermissionDef(permissionName: string): Promise<PermissionDef>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | string | 是 | 需要查询的权限的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PermissionDef> | Promise对象，获取成功时返回权限详细信息。 |

