# 管控Agent输入的交互事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

从API版本26.1.0开始，支持Agent输入管控和敏感节点输入监听。Agent输入管控用于设置组件对Agent输入事件的管控级别。应用还可以通过监听节点输入事件，在输入事件分发到节点前获取通知。例如，应用可允许Agent操作普通按钮，阻止Agent操作需要用户亲自确认的按钮，并通过监听记录被阻止的输入事件，用于监控Agent是否尝试输入密码等交互行为。

Agent输入事件包括系统Agent生成的输入事件，以及具有[ohos.permission.CONTROL_COMPONENT](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_component)权限的应用注入的事件。管控设置不影响用户生成的输入事件或其他注入事件。

## 约束与限制

1. 仅支持对触摸、鼠标和按键事件的管控与监听，其中按键事件仅支持对Enter键进行管控。
2. 使用组件管控能力需申请[ohos.permission.CONTROL_COMPONENT](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_component)权限。该权限为system_basic级别的系统授权权限，需按[声明权限](../security/AccessToken/declare-permissions.md)的要求完成配置；当应用权限等级低于所申请权限时，还需按[申请受限权限](../security/AccessToken/declare-permissions-in-acl.md)完成相应配置和授权。

## 接口说明

| 接口 | 说明 |
| --- | --- |
| [agentControlMode](../reference/apis-arkui/arkui-ts/ts-universal-attributes-agent-control-mode.md#agentcontrolmode) | 设置组件对Agent输入事件的管控级别。 |
| [AgentControlMode](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#agentcontrolmode) | 管控级别枚举，ALLOW允许Agent输入，DENY阻止Agent输入。 |
| [onNodeSensitiveInput](../reference/apis-arkui/arkts-apis-uicontext-uiobserver.md#onnodesensitiveinput) | 注册敏感节点输入监听，在事件分发前触发回调。 |
| [offNodeSensitiveInput](../reference/apis-arkui/arkts-apis-uicontext-uiobserver.md#offnodesensitiveinput) | 注销敏感节点输入监听。 |
| [NodeSensitiveInputInfo](../reference/apis-arkui/arkts-apis-uicontext-i.md#nodesensitiveinputinfo) | 监听回调携带的输入事件信息。 |
| [NodeSensitiveInputCallback](../reference/apis-arkui/arkts-apis-uicontext-t.md#nodesensitiveinputcallback) | 敏感节点输入监听的回调类型。 |
| [NodeSensitiveInputEventType](../reference/apis-arkui/arkts-apis-uicontext-e.md#nodesensitiveinputeventtype) | 敏感节点输入的事件类型枚举。 |

## 与相关Kit的关系

本能力依赖多模输入子系统。Agent输入事件由多模输入框架在注入链路上标识，ArkUI依据该标识区分Agent输入事件与用户输入事件，进而执行管控与监听。应用使用本指南时无需直接调用多模输入接口。如需了解输入事件注入能力，可参考多模输入的[输入事件注入](../reference/apis-input-kit/js-apis-inputeventclient.md)。

## 设置Agent输入管控

使用Agent输入管控前，需要在entry模块的module.json5中声明[ohos.permission.CONTROL_COMPONENT](../security/AccessToken/restricted-permissions.md#ohospermissioncontrol_component)权限，以下仅展示相关字段。

<!-- @[agent_input_control_permission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AgentInputControl/entry/src/main/module.json5) -->

```json5
{
  "module": {
    "requestPermissions": [
      {
        "name": "ohos.permission.CONTROL_COMPONENT"
      }
    ]
  }
}
```

声明权限后，开发者可根据实际业务场景完成如下功能实现。

- 设置Agent输入管控策略：在目标组件上设置[agentControlMode](../reference/apis-arkui/arkui-ts/ts-universal-attributes-agent-control-mode.md#agentcontrolmode)，选择允许或阻止Agent输入。
- 监听节点交互事件：注册敏感节点输入监听，获取节点的输入事件通知，包括被管控阻止的输入事件。

### 设置Agent输入管控策略

在目标组件上设置[agentControlMode](../reference/apis-arkui/arkui-ts/ts-universal-attributes-agent-control-mode.md#agentcontrolmode)，通过[AgentControlMode](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#agentcontrolmode)选择允许或阻止Agent输入：

- ALLOW：允许Agent生成的输入操作，无需用户确认。
- DENY：阻止Agent生成的输入操作。

传入undefined或不设置该属性时，组件默认允许Agent生成事件。

例如，容器组件设置DENY、其子按钮保持ALLOW时，Agent点击子按钮，子按钮仍可响应，但该容器及其祖先组件被阻止响应。

以下示例通过三个按钮切换目标组件的Agent输入管控级别。使用用户输入操作目标组件时，仍可触发其点击回调。

<!-- @[agent_control_mode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AgentInputControl/entry/src/main/ets/pages/AgentControlModeExample/AgentControlModeExample.ets) -->

```ts
@Entry
@Component
struct AgentControlModeExample {
  @State controlMode: AgentControlMode | undefined = AgentControlMode.ALLOW;

  build() {
    Column({ space: 12 }) {
      Button('目标组件')
        .agentControlMode(this.controlMode)
        .onClick(() => {
          console.info('目标组件收到点击事件');
        })
      Button('允许Agent输入')
        .onClick(() => {
          this.controlMode = AgentControlMode.ALLOW;
        })
      Button('阻止Agent输入')
        .onClick(() => {
          this.controlMode = AgentControlMode.DENY;
        })
      Button('传入undefined')
        .onClick(() => {
          this.controlMode = undefined;
        })
    }
    .width('100%')
    .padding(20)
  }
}
```

### 策略作用域与优先级

[agentControlMode](../reference/apis-arkui/arkui-ts/ts-universal-attributes-agent-control-mode.md#agentcontrolmode)是组件属性，作用于命中该组件的Agent输入，并沿手势树影响其祖先组件的响应。

Agent输入沿手势树从最深（最先命中）的组件向外逐层派发，因此管控级别按以下规则生效：

- 某组件设置为DENY时，该组件及其所有祖先组件被阻止响应该次Agent输入。
- 比该组件更深、且自身为ALLOW（或默认允许）的组件不受该DENY影响，仍可响应该次Agent输入。

## 监听节点交互事件

通过监听敏感节点输入，在输入事件分发到节点前获取通知。

### 注册与注销监听

监听主要分为如下几步：

1. 为目标组件设置[id](../reference/apis-arkui/arkui-ts/ts-universal-attributes-component-id.md#id)标识。
2. 节点创建后，通过UIContext的[getUIObserver()](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getuiobserver11)获取UIObserver，调用[onNodeSensitiveInput](../reference/apis-arkui/arkts-apis-uicontext-uiobserver.md#onnodesensitiveinput)注册监听，并保存回调函数引用。
3. 在回调中读取[NodeSensitiveInputInfo](../reference/apis-arkui/arkts-apis-uicontext-i.md#nodesensitiveinputinfo)，根据type读取对应的touchEvent、mouseEvent或keyEvent，并通过isAgent判断是否为Agent输入。
4. 不再需要监听时，调用[offNodeSensitiveInput](../reference/apis-arkui/arkts-apis-uicontext-uiobserver.md#offnodesensitiveinput)并传入原回调注销。不传回调时，注销该节点的全部敏感输入监听。页面退出时也应清理监听。

- 监听在输入事件分发到节点前触发。收到监听通知表示发生了输入尝试，不代表目标组件已执行其业务回调。
- 仅监听命中目标为节点自身的事件，不汇总其子节点的输入。需要监听子节点时，应为该子节点单独注册。
- 同一节点可注册多个回调，所有回调均在事件分发前执行。节点不存在时注册不生效，应确认节点已创建且标识正确。

以下示例点击“注册监听”后，可操作“被监听节点”查看输入日志。即使Agent输入被DENY阻止，监听仍可获取该次输入通知；点击注销按钮后，不再接收对应监听通知。

<!-- @[node_sensitive_input](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AgentInputControl/entry/src/main/ets/pages/NodeSensitiveInputExample/NodeSensitiveInputExample.ets) -->

```ts
import {
  NodeSensitiveInputCallback,
  NodeSensitiveInputEventType,
  NodeSensitiveInputInfo
} from '@kit.ArkUI';

@Entry
@Component
struct NodeSensitiveInputExample {
  private listening: boolean = false;
  private inputCallback: NodeSensitiveInputCallback = (info: NodeSensitiveInputInfo): void => {
    console.info('isAgent=' + info.isAgent + ', type=' + info.type);
    if (info.type === NodeSensitiveInputEventType.TOUCH && info.touchEvent) {
      console.info('触摸事件类型：' + info.touchEvent.type);
    } else if (info.type === NodeSensitiveInputEventType.MOUSE && info.mouseEvent) {
      console.info('鼠标事件动作：' + info.mouseEvent.action);
    } else if (info.type === NodeSensitiveInputEventType.KEY && info.keyEvent) {
      console.info('按键事件类型：' + info.keyEvent.type);
    }
  };

  aboutToDisappear(): void {
    this.getUIContext().getUIObserver().offNodeSensitiveInput('sensitiveButton', this.inputCallback);
  }

  build() {
    Column({ space: 12 }) {
      Button('被监听节点')
        .id('sensitiveButton')
        .agentControlMode(AgentControlMode.DENY)
        .onClick(() => {
          console.info('节点收到点击事件');
        })
      Button('注册监听')
        .onClick(() => {
          if (!this.listening) {
            this.getUIContext().getUIObserver().onNodeSensitiveInput('sensitiveButton', this.inputCallback);
            this.listening = true;
          }
        })
      Button('注销指定回调')
        .onClick(() => {
          this.getUIContext().getUIObserver().offNodeSensitiveInput('sensitiveButton', this.inputCallback);
          this.listening = false;
        })
      Button('注销该节点的全部敏感输入监听')
        .onClick(() => {
          this.getUIContext().getUIObserver().offNodeSensitiveInput('sensitiveButton');
          this.listening = false;
        })
    }
    .width('100%')
    .padding(20)
  }
}
```
