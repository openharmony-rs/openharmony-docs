# PluginComponent(System API) (System API)

提供外部应用组件嵌入式显示功能，即外部应用提供的UI可在本应用内显示。适用于需要跨应用复用UI组件的场景，如嵌入其他应用的页面或卡片，实现应用间的界面协同与数据交互。如需通过跨进程通信实现更新，请参考[@ohos.pluginComponent](../arkts-apis/arkts-arkui-plugincomponentmanager-n.md)。

## 子组件

不支持

## PluginComponent

```TypeScript
PluginComponent(options: PluginComponentOptions)
```

创建插件组件，用于显示外部应用提供的UI。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PluginComponentOptions](arkts-arkui-plugincomponentoptions-i-sys.md) | 是 | 插件组件选项 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [PluginComponentOptions](arkts-arkui-plugincomponentoptions-i-sys.md) | 定义用于构造插件组件的选项。 |
| [PluginComponentTemplate](arkts-arkui-plugincomponenttemplate-i-sys.md) | 定义插件组件模板信息，用于与提供方定义的组件绑定。 |
| [PluginErrorData](arkts-arkui-pluginerrordata-i-sys.md) | 发生错误时提供的数据。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [PluginErrorCallback](arkts-arkui-pluginerrorcallback-t-sys.md) | 发生错误时触发事件回调。 |
