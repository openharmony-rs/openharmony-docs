# FormLinkOptions

**起始版本：** 10

<!--Device-unnamed-declare interface FormLinkOptions--><!--Device-unnamed-declare interface FormLinkOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## abilityName

```TypeScript
abilityName?: string
```

action为router / call 类型时跳转的UIAbility名。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-FormLinkOptions-abilityName?: string--><!--Device-FormLinkOptions-abilityName?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: string
```

action的类型，支持三种预定义的类型： - router：跳转到提供方应用的指定UIAbility。 - message：自定义消息，触发后会调用提供方FormExtensionAbility的 [onFormEvent()](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md#onformevent)生命周期回调。 - call：后台启动提供方应用。触发后会拉起提供方应用的指定UIAbility（仅支持launchType为 [singleton](../../../application-models/uiability-launch-type.md#singleton启动模式)的UIAbility，即启动模式为单实例的UIAbility），但不会 调度到前台。提供方应用需要具备后台运行权限( [ohos.permission.KEEP_BACKGROUND_RUNNING](../../../security/AccessToken/permissions-for-all.md#ohospermissionkeep_background_running) )。 **说明：** 不推荐使用router事件刷新卡片UI。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-FormLinkOptions-action: string--><!--Device-FormLinkOptions-action: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bundleName

```TypeScript
bundleName?: string
```

action为router / call 类型时跳转的包名。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-FormLinkOptions-bundleName?: string--><!--Device-FormLinkOptions-bundleName?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## moduleName

```TypeScript
moduleName?: string
```

action为router / call 类型时跳转的模块名。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-FormLinkOptions-moduleName?: string--><!--Device-FormLinkOptions-moduleName?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## params

```TypeScript
params?: Object
```

当前action携带的额外参数，内容使用JSON格式的键值对形式。call 类型时需填入参数'method'，且类型需要为string类型，用于触发UIAbility中对应的方法。 **说明：** 不建议通过params传递卡片内部的状态变量。

**类型：** Object

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-FormLinkOptions-params?: Object--><!--Device-FormLinkOptions-params?: Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uri

```TypeScript
uri?: string
```

action为router 类型时跳转的UIAbility的统一资源标识符。uri和abilityName同时存在时，abilityName优先。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-FormLinkOptions-uri?: string--><!--Device-FormLinkOptions-uri?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

