# RequestParameters

使用pluginComponentManager.request方法时需要传递的参数。

**起始版本：** 8

<!--Device-pluginComponentManager-interface RequestParameters--><!--Device-pluginComponentManager-interface RequestParameters-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## data

```TypeScript
data: KVObject
```

组件数据，以键值对形式存储，用于传递给组件提供方的业务数据，键和值类型由业务定义。

**类型：** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RequestParameters-data: KVObject--><!--Device-RequestParameters-data: KVObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## jsonPath

```TypeScript
jsonPath?: string
```

存放模板路径的external.json文件的路径。 当需要通过外部配置文件直接加载模板而非通过request通信获取时传入此参数；当jsonPath字段不为空时不触发request通信，直接从external.json中读取模板路径。 不传入或为空时，触发request通信向组件提供方请求模板。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RequestParameters-jsonPath?: string--><!--Device-RequestParameters-jsonPath?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

请求组件名称。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RequestParameters-name: string--><!--Device-RequestParameters-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## want

```TypeScript
want: Want
```

组件提供方Ability信息。

**类型：** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RequestParameters-want: Want--><!--Device-RequestParameters-want: Want-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

