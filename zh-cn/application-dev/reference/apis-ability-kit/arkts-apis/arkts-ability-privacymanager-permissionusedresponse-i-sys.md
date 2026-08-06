# PermissionUsedResponse（系统接口）

表示所有应用或设备的访问记录。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-privacyManager-interface PermissionUsedResponse--><!--Device-privacyManager-interface PermissionUsedResponse-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## beginTime

```TypeScript
beginTime: long
```

查询记录的起始时间。 单位为：毫秒。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedResponse-beginTime: long--><!--Device-PermissionUsedResponse-beginTime: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## bundleRecords

```TypeScript
bundleRecords: Array<BundleUsedRecord>
```

每个元素表示一个应用维度下的权限访问记录，开发者可进一步遍历permissionRecords获取具体权限使用详情。

**类型：** Array&lt;BundleUsedRecord&gt;

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedResponse-bundleRecords: Array<BundleUsedRecord>--><!--Device-PermissionUsedResponse-bundleRecords: Array<BundleUsedRecord>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## endTime

```TypeScript
endTime: long
```

查询记录的终止时间。 单位为：毫秒。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedResponse-endTime: long--><!--Device-PermissionUsedResponse-endTime: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

