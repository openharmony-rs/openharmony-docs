# Resource

```TypeScript
export type Resource = _Resource
```

资源引用类型，用于设置组件属性的值。各类资源文件，需要放入特定子目录中存储管理，资源目录的示例请参考 [资源分类](../../../quick-start/resource-categories-and-access.md#资源分类)。 可以通过`\$r`或者`\$rawfile`创建Resource类型对象，不可以修改Resource中的各属性的值。 - `\$r('belonging.type.name')` belonging：系统资源或者应用资源，相应的取值为'sys'和'app'； type：资源类型，支持'boolean'、'color'、'float'、'intarray'、'integer'、'pattern'、'plural'、'strarray'、'string'、'media'； name：资源名称，在资源定义时确定。 - `\$rawfile('filename')` filename：工程中resources/rawfile目录下的文件名称。 > **说明：** > > - 引用资源类型时，需确保资源类型对象内的数据类型与当前以资源类型作为参数的属性方法本身的类型一致。例如某个属性方法支持设置string | Resource，那么在使用Resource引用类型时，其数据类型也应当为string。 > > - 引用资源类型时，需确保资源类型对象用法为当前支持的用法，否则当前以资源类型作为参数的属性效果将和不设置该属性相同。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type Resource = _Resource--><!--Device-unnamed-export type Resource = _Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**属性类型：** _Resource

