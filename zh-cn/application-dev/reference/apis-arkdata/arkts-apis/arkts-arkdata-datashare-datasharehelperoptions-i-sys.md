# DataShareHelperOptions（系统接口）

指定[DataShareHelper](#DataShareHelperOptions（系统接口）)的可选参数，包含是否在代理模式下，以及非静默访问的拉起等待时间。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-dataShare-interface DataShareHelperOptions--><!--Device-dataShare-interface DataShareHelperOptions-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## isProxy

```TypeScript
isProxy?: boolean
```

默认为false，如果为true，则要创建的[DataShareHelper](#DataShareHelperOptions（系统接口）)处于代理模式，所有操作都不会打开数据提供者APP，除非数据库不存在， 当数据库不存在时， [createDataShareHelper](arkts-arkdata-datashare-createdatasharehelper-f-sys.md#createDataShareHelper（系统接口）) 会拉起数据提供者创建数据库。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelperOptions-isProxy?: boolean--><!--Device-DataShareHelperOptions-isProxy?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## waitTime

```TypeScript
waitTime?: int
```

拉起数据提供者进程的等待时间（单位：秒），默认值为2秒。

**类型：** int

**默认值：** 2

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelperOptions-waitTime?: int--><!--Device-DataShareHelperOptions-waitTime?: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

