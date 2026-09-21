# postCardAction
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->

用于卡片内部和提供方应用间的交互，当前支持router、message和call三种类型的事件，仅在卡片中可以调用。<!--Del-->此外，系统应用的卡片还支持insightIntent类型的事件，用于通过意图框架执行意图跳转。<!--DelEnd-->

> **说明：** 
>
> 本接口从API version 9开始支持。

## postCardAction

postCardAction(component: Object, action: Object): void

执行函数内部的交互，处理component和action对象的相关操作，不返回任何内容。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**


| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| component | Object | 是 | 当前自定义组件的实例，通常传入this。 |
| action | Object | 是 | action的具体描述，详情见下表。 |


action参数说明：


| **参数名** | **类型** |  **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| action | string | 是 |action的类型，支持三种<!--Del-->（系统应用还支持insightIntent类型）<!--DelEnd-->预定义的类型：<br/>-&nbsp;router：跳转到提供方应用的指定UIAbility，只允许在点击事件中触发。<br/>-&nbsp;message：自定义消息，触发后会调用提供方FormExtensionAbility的[onFormEvent()](../apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonformevent)生命周期回调。<br/>-&nbsp;call：后台启动提供方应用。触发后会拉起提供方应用的指定UIAbility（仅支持launchType为singleton的[UIAbility](../../application-models/uiability-launch-type.md)，即启动模式为单实例的UIAbility），但不会调度到前台。提供方应用需要具备后台运行权限([ohos.permission.KEEP_BACKGROUND_RUNNING](../../security/AccessToken/permissions-for-all.md#ohospermissionkeep_background_running))。<!--Del--><br/>-&nbsp;insightIntent<sup>26+</sup>：通过[意图框架](../apis-ability-kit/js-apis-app-ability-insightIntent.md)执行意图跳转到提供方应用，只允许在点击事件中触发，仅系统应用支持。<!--DelEnd--> |
| bundleName | string | 否 | action为router&nbsp;/&nbsp;call&nbsp;类型时跳转的包名。<!--Del-->action为insightIntent&nbsp;类型时可指定意图跳转目标的包名，缺省时使用卡片提供方应用的包名。<!--DelEnd--> |
| moduleName | string | 否 | action为router&nbsp;/&nbsp;call&nbsp;类型时跳转的模块名。<!--Del-->action为insightIntent&nbsp;类型时可指定意图跳转目标的模块名，缺省时使用卡片提供方应用的模块名。<!--DelEnd--> |
| abilityName | string | 否 | action为router&nbsp;/&nbsp;call&nbsp;类型时跳转的UIAbility名。<!--Del-->action为insightIntent&nbsp;类型时可指定意图跳转目标的UIAbility名，缺省时使用提供方应用[module.json5配置文件](../../quick-start/module-configuration-file.md)中入口UIAbility对应的名称。<!--DelEnd--> |
| uri<sup>11+</sup> | string   | 否   | action为router&nbsp;类型时跳转的UIAbility的统一资源标识符。uri和abilityName同时存在时，abilityName优先。<!--Del-->enableRouteSecondPage为true时，uri可与abilityName同时生效，用于跳转到提供方应用的二级页面，仅系统应用支持。<!--DelEnd--><!--Del-->
| enableRouteSecondPage<sup>26+</sup> | boolean | 否 | action为router&nbsp;类型时是否允许uri与abilityName同时生效，以跳转到提供方应用的二级页面，默认为false，仅系统应用支持。 |
| intentName<sup>26+</sup> | string | 否 | action为insightIntent&nbsp;类型时指定要执行的意图名称，action为insightIntent&nbsp;类型时必填，仅系统应用支持。<!--DelEnd-->
| params | Object | 否 | 当前action携带的额外参数，内容使用JSON格式的键值对形式。<!--Del-->action为insightIntent&nbsp;类型时，"params"中可填入参数'intentParams'和'executeMode'，详见下方说明。<!--DelEnd--> |

>**说明：**
>
>"action"为"call"&nbsp;类型时，"params"需填入参数'method'，且类型需为string类型，用于触发UIAbility中对应的方法。
><!--Del-->"action"为"insightIntent"&nbsp;类型时，"intentName"必填且类型需为string类型，用于指定要执行的意图名称；"params"中可填入参数'intentParams'和'executeMode'：'intentParams'类型为object，用于承载意图执行所需的业务参数，参数值仅支持string、number和boolean类型；'executeMode'类型为number，用于指定意图的执行模式，取值参考[ExecuteMode](../apis-ability-kit/js-apis-app-ability-insightIntent.md#executemode)，缺省为0。<!--DelEnd-->

**示例：** 

<!--code_no_check-->

```ts
Button('跳转')
  .width('40%')
  .height('20%')
  .onClick(() => {
    postCardAction(this, {
      action: 'router',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility',
      params: {
        message: 'testForRouter' // 自定义要发送的message
      }
    });
  })

Button('拉至后台')
  .width('40%')
  .height('20%')
  .onClick(() => {
    postCardAction(this, {
      action: 'call',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility',
      params: {
        method: 'fun', // 自定义调用的方法名，必填
        message: 'testForCall' // 自定义要发送的message
      }
    });
  })

Button('URI跳转')
  .width('40%')
  .height('20%')
  .onClick(() => {
    postCardAction(this, {
      action: 'router',
      uri: 'example://uri.ohos.com/link_page',
      params: {
        message: 'router msg for dynamic uri deeplink' // 自定义要发送的message
      }
    });
  })

```
<!--Del-->
<!--code_no_check-->
```ts
Button('意图跳转')
  .width('40%')
  .height('20%')
  .onClick(() => {
    postCardAction(this, {
      action: 'insightIntent',
      intentName: 'PlayMusic', // 意图名称，必填
      params: {
        intentParams: {
          musicId: '12345' // 意图执行的业务参数
        },
        executeMode: 0 // 意图执行模式，取值参考ExecuteMode，缺省为0
      }
    });
  })

Button('跳转二级页面')
  .width('40%')
  .height('20%')
  .onClick(() => {
    postCardAction(this, {
      action: 'router',
      abilityName: 'EntryAbility',
      uri: 'example://uri.ohos.com/link_page',
      enableRouteSecondPage: true, // 为true时uri与abilityName同时生效，跳转到提供方应用的二级页面
      params: {
        message: 'testForRouteSecondPage' // 自定义要发送的message
      }
    });
  })
```
<!--DelEnd-->

**待跳转应用 [module.json5](../../quick-start/module-configuration-file.md#skills标签) uris 配置示例：**

```json
"abilities": [
  {
    "skills": [
      {
        "uris": [
          {
            "scheme": "example",
            "host": "uri.ohos.com",
            "path": "link_page"
          }
        ]
      }
    ]
  }
]
```
