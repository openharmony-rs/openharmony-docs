# PushParameterForStage（系统接口）

用于设置Stage模型下使用pluginComponentManager.push方法时需要传递的参数。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-pluginComponentManager-interface PushParameterForStage--><!--Device-pluginComponentManager-interface PushParameterForStage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: KVObject
```

组件数据，以键值对形式存储。用于向组件使用方传递业务数据，如页面路径（key为'js'，value为模板路径字符串）及自定义数据字段。

**类型：** [KVObject](../../apis-na/arkts-apis/arkts-na-plugincomponentmanager-kvobject-t.md)

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-PushParameterForStage-data: KVObject--><!--Device-PushParameterForStage-data: KVObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## extraData

```TypeScript
extraData: KVObject
```

附加数据，用于在发送组件时传递额外的自定义数据，与组件数据（data）区分，可根据业务需要设置。

**类型：** [KVObject](../../apis-na/arkts-apis/arkts-na-plugincomponentmanager-kvobject-t.md)

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-PushParameterForStage-extraData: KVObject--><!--Device-PushParameterForStage-extraData: KVObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## jsonPath

```TypeScript
jsonPath?: string
```

存放模板路径的external.json文件的路径。当需要从external.json文件加载模板路径而非通过Push通信发送模板时传入此参数。 当jsonPath字段不为空时不触发Push通信，组件模板路径从external.json文件中读取；当jsonPath为空（默认）时，通过Push通信向组件使用方发送组件模板。

**类型：** string

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-PushParameterForStage-jsonPath?: string--><!--Device-PushParameterForStage-jsonPath?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

组件名称，当jsonPath不为空时需与external.json文件中的键名一致。

**类型：** string

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-PushParameterForStage-name: string--><!--Device-PushParameterForStage-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## owner

```TypeScript
owner: Want
```

组件提供方Ability信息。

**类型：** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-PushParameterForStage-owner: Want--><!--Device-PushParameterForStage-owner: Want-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## target

```TypeScript
target: Want
```

组件使用方Ability信息。

**类型：** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-PushParameterForStage-target: Want--><!--Device-PushParameterForStage-target: Want-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

