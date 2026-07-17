# PermissionUsedResponse（系统接口）

表示所有应用或设备的访问记录。

**起始版本：** 9

<!--Device-privacyManager-interface PermissionUsedResponse--><!--Device-privacyManager-interface PermissionUsedResponse-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## beginTime

```TypeScript
beginTime: number
```

查询记录的起始时间。单位为：毫秒。

**类型：** number

**起始版本：** 9

<!--Device-PermissionUsedResponse-beginTime: long--><!--Device-PermissionUsedResponse-beginTime: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## bundleRecords

```TypeScript
bundleRecords: Array<BundleUsedRecord>
```

每个元素表示一个应用维度下的权限访问记录，开发者可进一步遍历permissionRecords获取具体权限使用详情。

**类型：** Array<BundleUsedRecord>

**起始版本：** 9

<!--Device-PermissionUsedResponse-bundleRecords: Array<BundleUsedRecord>--><!--Device-PermissionUsedResponse-bundleRecords: Array<BundleUsedRecord>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## endTime

```TypeScript
endTime: number
```

查询记录的终止时间。单位为：毫秒。

**类型：** number

**起始版本：** 9

<!--Device-PermissionUsedResponse-endTime: long--><!--Device-PermissionUsedResponse-endTime: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

