# TemplateId（系统接口）

标记模板的数据结构，TemplateId是在[addTemplate](arkts-arkdata-datasharehelper-i-sys.md#addtemplate-1)中自动生成的，在
[addTemplate](arkts-arkdata-datasharehelper-i-sys.md#addtemplate-1)后，可以使用模板id来标记模板。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## bundleNameOfOwner

```TypeScript
bundleNameOfOwner: string
```

指定创建模板的模板所有者的bundleName，与[addTemplate](arkts-arkdata-datasharehelper-i-sys.md#addtemplate-1)中的bundleName相同。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## subscriberId

```TypeScript
subscriberId: string
```

指定处理回调的订阅者的id，与[addTemplate](arkts-arkdata-datasharehelper-i-sys.md#addtemplate-1)中的subscriberId相同，每个订阅者的ID是唯一的。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

