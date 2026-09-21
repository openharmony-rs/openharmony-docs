# Resource

```TypeScript
declare type Resource = import('../api/global/resource').Resource
```

资源引用类型，用于设置组件属性的值。各类资源文件，需要放入特定子目录中存储管理，资源目录的示例请参考[资源分类](../../../quick-start/resource-categories-and-access.md#资源分类)。

> **说明：** 
> 
> - 引用资源类型时，需确保资源类型对象内的数据类型与当前以资源类型作为参数的属性方法本身的类型一致。例如某个属性方法支持设置string | Resource，那么在使用Resource引用类型时，其数据类型也应当为string。
> 
> - 引用资源类型时，需确保资源类型对象用法为当前支持的用法，否则当前以资源类型作为参数的属性效果将和不设置该属性相同。
> 
> - $rawfile不支持通过[预览器](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-previewer-arkts-js)预览。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**类型：** import('../api/global/resource').Resource
