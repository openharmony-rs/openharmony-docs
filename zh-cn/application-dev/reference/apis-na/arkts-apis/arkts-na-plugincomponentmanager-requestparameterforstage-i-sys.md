# RequestParameterForStage（系统接口）

用于设置Stage模型下使用pluginComponentManager.request方法时需要传递的参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-pluginComponentManager-export interface RequestParameterForStage--><!--Device-pluginComponentManager-export interface RequestParameterForStage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: KVObject
```

附加数据，以键值对形式存储。用于向组件提供方传递请求时的自定义业务参数，以便提供方根据这些数据返回合适的组件模板。

**类型：** [KVObject](arkts-na-plugincomponentmanager-kvobject-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestParameterForStage-data: KVObject--><!--Device-RequestParameterForStage-data: KVObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## jsonPath

```TypeScript
jsonPath?: string
```

存放模板路径的external.json文件的路径。当需要从external.json文件加载模板路径而非通过Request通信获取模板时传入此参数。 当jsonPath字段不为空时不触发Request通信；当jsonPath为空（默认）时，通过Request通信向组件提供方请求组件模板。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestParameterForStage-jsonPath?: string--><!--Device-RequestParameterForStage-jsonPath?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

请求组件名称，当jsonPath不为空时需与external.json文件中的键名一致。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestParameterForStage-name: string--><!--Device-RequestParameterForStage-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## owner

```TypeScript
owner: Want
```

组件使用方Ability信息。

**类型：** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestParameterForStage-owner: Want--><!--Device-RequestParameterForStage-owner: Want-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## target

```TypeScript
target: Want
```

组件提供方Ability信息。

**类型：** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestParameterForStage-target: Want--><!--Device-RequestParameterForStage-target: Want-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

