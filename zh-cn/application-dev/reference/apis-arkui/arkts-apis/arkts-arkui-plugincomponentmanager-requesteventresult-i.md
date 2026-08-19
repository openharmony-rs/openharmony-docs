# RequestEventResult

注册request监听方法后，接收到请求事件时回应请求的数据类型。

**起始版本：** 8

<!--Device-pluginComponentManager-interface RequestEventResult--><!--Device-pluginComponentManager-interface RequestEventResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## data

```TypeScript
data?: KVObject
```

组件数据，以键值对形式存储，用于回应请求时传递的业务数据，键和值类型由业务定义。该字段为可选字段，不提供时默认不包含在返回结果中。

**类型：** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RequestEventResult-data?: KVObject--><!--Device-RequestEventResult-data?: KVObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraData

```TypeScript
extraData?: KVObject
```

request事件中传递的附加数据。该字段为可选字段，不提供时默认不包含在返回结果中。

**类型：** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RequestEventResult-extraData?: KVObject--><!--Device-RequestEventResult-extraData?: KVObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## template

```TypeScript
template?: string
```

组件模板。该字段为可选字段，不提供时默认不包含在返回结果中。当需要返回组件模板信息时设置此字段；不需要返回模板时可省略。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RequestEventResult-template?: string--><!--Device-RequestEventResult-template?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

