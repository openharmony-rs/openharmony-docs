# DataShareHelperOptions

指定[DataShareHelper]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的可选参数，包含是否在代理模式下，以及非静默访问的拉起等待时间。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-dataShare-interface DataShareHelperOptions--><!--Device-dataShare-interface DataShareHelperOptions-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## isProxy

```TypeScript
isProxy?: boolean
```

默认为false，如果为true，则要创建的[DataShareHelper]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_处于代理模式，所有操作都不会打开数据提供者APP，除非数据库不存在， 当数据库不存在时， [createDataShareHelper]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 会拉起数据提供者创建数据库。

**类型：** boolean

**默认值：** false

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelperOptions-isProxy?: boolean--><!--Device-DataShareHelperOptions-isProxy?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## waitTime

```TypeScript
waitTime?: int
```

拉起数据提供者进程的等待时间（单位：秒），默认值为2秒。

**类型：** int

**默认值：** 2

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareHelperOptions-waitTime?: int--><!--Device-DataShareHelperOptions-waitTime?: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

