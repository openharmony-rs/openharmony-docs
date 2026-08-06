# @ohos.sendableResourceManager

本模块提供[Resource]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_对象与 [SendableResource]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_对象之间的相互转换功能。SendableResource实现了 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_接口，支持跨线程传输。跨线程传输后，SendableResource对象可以再转换为Resource对象，作为 参数传递给[资源管理]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_接口以获取资源。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare namespace sendableResourceManager--><!--Device-unnamed-declare namespace sendableResourceManager-End-->

**系统能力：** SystemCapability.Global.ResourceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [resourceToSendableResource](arkts-localization-sendableresourcemanager-resourcetosendableresource-f.md#resourcetosendableresource) | 将Resource对象转换为可用于跨线程传输的SendableResource对象。 |
| [sendableResourceToResource](arkts-localization-sendableresourcemanager-sendableresourcetoresource-f.md#sendableresourcetoresource) | 将跨线程传输的SendableResource对象转换为Resource对象。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Resource](arkts-localization-sendableresourcemanager-resource-t.md) | 表示资源相关信息，包括应用包名、应用模块名、资源ID、资源类型和其他资源参数。 |
| [SendableResource](arkts-localization-sendableresourcemanager-sendableresource-t.md) | 表示跨线程传输的Sendable资源相关信息，包括应用包名、应用模块名、资源ID、资源类型和其他资源参数。 |

