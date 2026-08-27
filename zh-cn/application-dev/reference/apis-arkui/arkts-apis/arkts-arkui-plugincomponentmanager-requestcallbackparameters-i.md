# RequestCallbackParameters

pluginComponentManager.request方法接收到的回调结果。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## componentTemplate

```TypeScript
componentTemplate: PluginComponentTemplate
```

组件模板。

**类型：** [PluginComponentTemplate](arkts-arkui-plugincomponent-plugincomponenttemplate-i.md)

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## data

```TypeScript
data: KVObject
```

组件数据，以键值对形式存储，键和值类型由业务定义。

**类型：** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraData

```TypeScript
extraData: KVObject
```

附加数据。该字段为可选字段，不提供时默认不包含在返回结果中。

**类型：** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
