# PushParameters

使用pluginComponentManager.push方法时需要传递的参数。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-pluginComponentManager-interface PushParameters--><!--Device-pluginComponentManager-interface PushParameters-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## data

```TypeScript
data: KVObject
```

组件数据，以键值对形式存储，用于传递给组件使用方的业务数据，键和值类型由业务定义。

**类型：** [KVObject](../../apis-na/arkts-apis/arkts-na-plugincomponentmanager-kvobject-t.md)

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PushParameters-data: KVObject--><!--Device-PushParameters-data: KVObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraData

```TypeScript
extraData: KVObject
```

附加数据，以键值对形式存储，用于传递额外的业务信息，键和值类型由业务定义。

**类型：** [KVObject](../../apis-na/arkts-apis/arkts-na-plugincomponentmanager-kvobject-t.md)

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PushParameters-extraData: KVObject--><!--Device-PushParameters-extraData: KVObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## jsonPath

```TypeScript
jsonPath?: string
```

存放模板路径的external.json文件的路径。 当需要通过外部配置文件直接加载模板而非通过push通信发送时传入此参数；当jsonPath字段不为空时不触发push通信，直接从external.json中读取模板路径进行加载。 不传入或为空时，触发push通信向组件使用方推送组件和数据。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PushParameters-jsonPath?: string--><!--Device-PushParameters-jsonPath?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

组件名称。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PushParameters-name: string--><!--Device-PushParameters-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## want

```TypeScript
want: Want
```

组件使用方Ability信息。

**类型：** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PushParameters-want: Want--><!--Device-PushParameters-want: Want-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

