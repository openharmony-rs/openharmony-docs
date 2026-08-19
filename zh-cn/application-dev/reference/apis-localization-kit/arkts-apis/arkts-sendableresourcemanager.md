# @ohos.sendableResourceManager

本模块提供[Resource](arkts-localization-sendableresourcemanager-resource-t.md)对象与 [SendableResource](arkts-localization-sendableresourcemanager-sendableresource-t.md)对象之间的相互转换功能。SendableResource实现了 [ISendable](../../../arkts-utils/arkts-sendable.md#isendable)接口，支持跨线程传输。跨线程传输后，SendableResource对象可以再转换为Resource对象，作为 参数传递给[资源管理](arkts-resourcemanager.md)接口以获取资源。

**起始版本：** 12

<!--Device-unnamed-declare namespace sendableResourceManager--><!--Device-unnamed-declare namespace sendableResourceManager-End-->

**系统能力：** SystemCapability.Global.ResourceManager

## 导入模块

```TypeScript
import { sendableResourceManager } from '@kit.LocalizationKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [resourceToSendableResource](arkts-localization-sendableresourcemanager-resourcetosendableresource-f.md) | 将Resource对象转换为可用于跨线程传输的SendableResource对象。 |
| [sendableResourceToResource](arkts-localization-sendableresourcemanager-sendableresourcetoresource-f.md) | 将跨线程传输的SendableResource对象转换为Resource对象。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Resource](arkts-localization-sendableresourcemanager-resource-t.md) | 表示资源相关信息，包括应用包名、应用模块名、资源ID、资源类型和其他资源参数。 |
| [SendableResource](arkts-localization-sendableresourcemanager-sendableresource-t.md) | 表示跨线程传输的Sendable资源相关信息，包括应用包名、应用模块名、资源ID、资源类型和其他资源参数。 |

