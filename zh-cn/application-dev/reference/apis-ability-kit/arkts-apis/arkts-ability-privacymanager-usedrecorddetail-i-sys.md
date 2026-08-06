# UsedRecordDetail（系统接口）

单次访问记录详情。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-privacyManager-interface UsedRecordDetail--><!--Device-privacyManager-interface UsedRecordDetail-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## accessDuration

```TypeScript
accessDuration: long
```

访问时长。 单位为：毫秒。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-UsedRecordDetail-accessDuration: long--><!--Device-UsedRecordDetail-accessDuration: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## count

```TypeScript
count?: int
```

访问次数。在accessRecords中表示成功访问次数，在rejectRecords中表示失败或拒绝次数。 默认值：0。

**类型：** int

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-UsedRecordDetail-count?: int--><!--Device-UsedRecordDetail-count?: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## lockScreenStatus

```TypeScript
lockScreenStatus?: int
```

访问时的锁屏状态。 - 1，表示非锁屏场景使用权限。 - 2，表示锁屏场景使用权限。 默认值：1。

**类型：** int

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-UsedRecordDetail-lockScreenStatus?: int--><!--Device-UsedRecordDetail-lockScreenStatus?: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: int
```

访问状态。0表示停止使用，1表示前台使用，2表示后台使用。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-UsedRecordDetail-status: int--><!--Device-UsedRecordDetail-status: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## timestamp

```TypeScript
timestamp: long
```

访问时的时间戳。 单位为：毫秒。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-UsedRecordDetail-timestamp: long--><!--Device-UsedRecordDetail-timestamp: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## usedType

```TypeScript
usedType?: PermissionUsedType
```

敏感权限访问方式。 默认值：NORMAL\_TYPE。

**类型：** PermissionUsedType

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-UsedRecordDetail-usedType?: PermissionUsedType--><!--Device-UsedRecordDetail-usedType?: PermissionUsedType-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

