# InteractionEventBindingInfo

组件的交互事件绑定状态信息。如果当前节点上绑定了所要查询的交互事件，调用查询接口时返回一个InteractionEventBindingInfo对象，指示事件绑定详细信息。

**起始版本：** 19

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## baseEventRegistered

```TypeScript
baseEventRegistered: boolean
```

是否以声明方式绑定事件。

true表示以声明方式绑定事件，false表示没有以声明方式绑定事件。

**类型：** boolean

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builtInEventRegistered

```TypeScript
builtInEventRegistered: boolean
```

组件是否绑定内置事件(组件内部定义的事件, 无需开发者手动绑定)。

true表示组件绑定内置事件，false表示组件没有绑定内置事件。

**类型：** boolean

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## nativeEventRegistered

```TypeScript
nativeEventRegistered: boolean
```

是否以注册节点事件（
[registerNodeEvent](../../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)
）的方式绑定事件。

true表示以注册节点事件的方式绑定事件，false表示没有以注册节点事件的方式绑定事件。

**类型：** boolean

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## nodeEventRegistered

```TypeScript
nodeEventRegistered: boolean
```

是否以自定义组件节点的方式绑定事件，请参考[基础事件示例](../../../../reference/apis-arkui/js-apis-arkui-frameNode.md#基础事件示例)

true表示以自定义组件节点的方式绑定事件，false表示没有以自定义组件节点的方式绑定事件。

**类型：** boolean

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

