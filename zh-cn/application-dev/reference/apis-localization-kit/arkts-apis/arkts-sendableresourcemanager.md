# @ohos.sendableResourceManager

资源管理导入sendableResourceManager模块，通过调用
[resourceToSendableResource](arkts-localization-sendableresourcemanager-resourcetosendableresource-f.md#resourceToSendableResource-1)和
[sendableResourceToResource](arkts-localization-sendableresourcemanager-sendableresourcetoresource-f.md#sendableResourceToResource-1)方法可以将
[Resource](arkts-localization-sendableresourcemanager-resource-t.md#Resource)对象和
[SendableResource](arkts-localization-sendableresourcemanager-resourcetosendableresource-f.md#resourceToSendableResource-1)对象进行互转。
Resource对象通过转换为SendableResource对象后，可以被[Sendable类](../../../../arkts-utils/arkts-sendable.md)持有。Sendable类在跨线程传输后，取出持有的
SendableResource对象转为Resource对象，作为参数获取资源。

**起始版本：** 12

**系统能力：** SystemCapability.Global.ResourceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [resourceToSendableResource](arkts-localization-sendableresourcemanager-resourcetosendableresource-f.md#resourceToSendableResource-1) | 将Resource对象转换为SendableResource对象。<br/> |
| [sendableResourceToResource](arkts-localization-sendableresourcemanager-sendableresourcetoresource-f.md#sendableResourceToResource-1) | 将SendableResource对象转换为Resource对象。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Resource](arkts-localization-sendableresourcemanager-resource-t.md) | 表示Resource资源信息。<br/> |
| [SendableResource](arkts-localization-sendableresourcemanager-sendableresource-t.md) | 表示SendableResource资源信息。<br/> |

