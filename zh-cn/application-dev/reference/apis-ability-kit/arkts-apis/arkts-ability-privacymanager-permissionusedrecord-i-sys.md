# PermissionUsedRecord（系统接口）

某个权限的访问记录。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-privacyManager-interface PermissionUsedRecord--><!--Device-privacyManager-interface PermissionUsedRecord-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## accessCount

```TypeScript
accessCount: int
```

该权限访问总次数，表示在查询时间窗口内成功使用该权限的累计次数。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedRecord-accessCount: int--><!--Device-PermissionUsedRecord-accessCount: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## accessRecords

```TypeScript
accessRecords: Array<UsedRecordDetail>
```

访问记录集合，仅当flag为FLAG\_PERMISSION\_USAGE\_DETAIL时生效。 默认值：查询最近10条成功访问记录。

**类型：** Array&lt;UsedRecordDetail&gt;

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedRecord-accessRecords: Array<UsedRecordDetail>--><!--Device-PermissionUsedRecord-accessRecords: Array<UsedRecordDetail>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## enhancedIdentity

```TypeScript
enhancedIdentity?: string
```

扩展身份，长度不超过48个字符。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionUsedRecord-enhancedIdentity?: string--><!--Device-PermissionUsedRecord-enhancedIdentity?: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## lastAccessDuration

```TypeScript
lastAccessDuration: long
```

最后一次访问时长。 单位为：毫秒。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedRecord-lastAccessDuration: long--><!--Device-PermissionUsedRecord-lastAccessDuration: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## lastAccessTime

```TypeScript
lastAccessTime: long
```

最后一次访问时间。 单位为：毫秒。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedRecord-lastAccessTime: long--><!--Device-PermissionUsedRecord-lastAccessTime: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## lastRejectTime

```TypeScript
lastRejectTime: long
```

最后一次拒绝时间。 单位为：毫秒。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedRecord-lastRejectTime: long--><!--Device-PermissionUsedRecord-lastRejectTime: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## permissionName

```TypeScript
permissionName: Permissions
```

权限名，用于标识当前统计记录对应的敏感权限。

**类型：** Permissions

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedRecord-permissionName: Permissions--><!--Device-PermissionUsedRecord-permissionName: Permissions-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## rejectCount

```TypeScript
rejectCount: int
```

该权限拒绝总次数，表示在查询时间窗口内权限访问失败或被拒绝的累计次数。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedRecord-rejectCount: int--><!--Device-PermissionUsedRecord-rejectCount: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## rejectRecords

```TypeScript
rejectRecords: Array<UsedRecordDetail>
```

拒绝记录集合，仅当flag为FLAG\_PERMISSION\_USAGE\_DETAIL时生效。 默认值：查询最近10条失败或拒绝记录。

**类型：** Array&lt;UsedRecordDetail&gt;

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-PermissionUsedRecord-rejectRecords: Array<UsedRecordDetail>--><!--Device-PermissionUsedRecord-rejectRecords: Array<UsedRecordDetail>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

