# AppGroupCallbackInfo（系统接口）

应用分组变化回调返回的属性集合

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-usageStatistics-interface AppGroupCallbackInfo--><!--Device-usageStatistics-interface AppGroupCallbackInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

## appNewGroup

```TypeScript
appNewGroup: int
```

变化后的应用分组。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AppGroupCallbackInfo-appNewGroup: int--><!--Device-AppGroupCallbackInfo-appNewGroup: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

## appOldGroup

```TypeScript
appOldGroup: int
```

变化前的应用分组。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AppGroupCallbackInfo-appOldGroup: int--><!--Device-AppGroupCallbackInfo-appOldGroup: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

应用名称。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AppGroupCallbackInfo-bundleName: string--><!--Device-AppGroupCallbackInfo-bundleName: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

## changeReason

```TypeScript
changeReason: long
```

分组变化原因。 - 256:使用记录初创建时，默认匹配的原因。 - 512:计算优先级分组时异常。 - 768:使用时长变化。 - 1024:有其他应用为当前应用强制设置优先级分组。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AppGroupCallbackInfo-changeReason: long--><!--Device-AppGroupCallbackInfo-changeReason: long-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId: int
```

用户id。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AppGroupCallbackInfo-userId: int--><!--Device-AppGroupCallbackInfo-userId: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

