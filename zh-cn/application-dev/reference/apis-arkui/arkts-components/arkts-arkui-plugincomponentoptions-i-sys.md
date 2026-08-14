# PluginComponentOptions（系统接口）

定义用于构造插件组件的选项。 > **说明：** > > 为了规范化匿名对象定义，此处的元素定义已在API版本18中进行修订。 > 虽然为匿名对象保留了历史版本信息，但可能会出现外层元素的@since版本号高于内层元素的情况。这不影响接口的可用性。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-unnamed-declare interface PluginComponentOptions--><!--Device-unnamed-declare interface PluginComponentOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: any
```

传给插件组件提供方使用的数据，类型不限（支持对象、字符串等）。具体数据格式由使用方与提供方协商定义。

**类型：** any

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-PluginComponentOptions-data: any--><!--Device-PluginComponentOptions-data: any-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## template

```TypeScript
template: PluginComponentTemplate
```

插件组件模板。

**类型：** [PluginComponentTemplate](arkts-arkui-plugincomponenttemplate-i-sys.md)

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-PluginComponentOptions-template: PluginComponentTemplate--><!--Device-PluginComponentOptions-template: PluginComponentTemplate-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

