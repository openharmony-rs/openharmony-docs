# PluginComponentOptions（系统接口）

定义用于构造插件组件的选项。

> **说明：**
> 
> 为了规范化匿名对象定义，此处的元素定义已在API版本18中进行修订。
> 虽然为匿名对象保留了历史版本信息，但可能会出现外层元素的

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## data

```TypeScript
data: any
```

传给插件组件提供方使用的数据，类型不限（支持对象、字符串等）。具体数据格式由使用方与提供方协商定义。

**类型：** any

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## template

```TypeScript
template: PluginComponentTemplate
```

插件组件模板。

**类型：** [PluginComponentTemplate](arkts-arkui-plugincomponenttemplate-i-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
