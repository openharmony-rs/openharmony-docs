# Result（系统接口）

端云共享结果的返回值。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-sharing-interface Result<T>--><!--Device-sharing-interface Result<T>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## code

```TypeScript
code: int
```

错误码。

**类型：** int

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Result-code: int--><!--Device-Result-code: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## description

```TypeScript
description?: string
```

错误码详细描述，默认为undefined。

**类型：** string

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Result-description?: string--><!--Device-Result-description?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## value

```TypeScript
value?: T
```

返回结果的值，具体类型由参数T指定，默认为undefined。

**类型：** T

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Result-value?: T--><!--Device-Result-value?: T-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

