# DistributedField（系统接口）

用于谓词查询条件的特殊字段。请使用枚举名称而非枚举值。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-relationalStore-enum DistributedField--><!--Device-relationalStore-enum DistributedField-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## ORIGIN

```TypeScript
ORIGIN = '#_origin'
```

用于查找或更新时指定数据来源的字段名。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedField-ORIGIN = '#_origin'--><!--Device-DistributedField-ORIGIN = '#_origin'-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## ORIGIN_ORIDEVICE

```TypeScript
ORIGIN_ORIDEVICE = '#_ori_device'
```

用于查找或更新时指定数据产生者的设备id，该值传入若为空，则表示本地设备；若不为空，则表示其他组网设备。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedField-ORIGIN_ORIDEVICE = '#_ori_device'--><!--Device-DistributedField-ORIGIN_ORIDEVICE = '#_ori_device'-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## CURSOR_FIELD

```TypeScript
CURSOR_FIELD = '#_cursor'
```

用于cursor查找的字段名。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedField-CURSOR_FIELD = '#_cursor'--><!--Device-DistributedField-CURSOR_FIELD = '#_cursor'-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## DELETED_FLAG_FIELD

```TypeScript
DELETED_FLAG_FIELD = '#_deleted_flag'
```

用于cursor查找的结果集返回时填充的字段。true表示对端删除的数据，同步到本端。false表示对端写入或更新的数据，同步到本端；或者本端写入或更新的数据。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedField-DELETED_FLAG_FIELD = '#_deleted_flag'--><!--Device-DistributedField-DELETED_FLAG_FIELD = '#_deleted_flag'-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

