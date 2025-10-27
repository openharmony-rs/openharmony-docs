# 使用通过UIServiceExtensionAbility实现的系统悬浮窗

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhangyafei-echo-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

## 概述

UIServiceExtensionAbility组件是带用户界面（UI）的扩展服务组件。系统应用可以通过UIServiceExtensionAbility组件实现一个具有特定功能、带UI的服务能力，并将其UI服务开放给其他三方应用调用。

本文描述中称被启动的UIServiceExtensionAbility组件为服务端，称UIServiceExtensionAbility组件的启动方为客户端。

应用可以通过启动和连接两种形式使用UIServiceExtensionAbility组件：
- 通过[UIExtensionContext](../reference/apis-ability-kit/js-apis-inner-application-uiExtensionContext.md)调用[startUIServiceExtensionAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startuiserviceextensionability14)方法启动UIServiceExtensionAbility。
- 通过[UIAbilityContext](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md)、[UIExtensionContext](../reference/apis-ability-kit/js-apis-inner-application-uiExtensionContext.md)调用[connectUIServiceExtensionAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectuiserviceextensionability14)方法连接UIServiceExtensionAbility。

## 约束限制

- 当前仅支持2in1设备。

- 三方应用需要在前台获焦的情况下才能连接系统提供的UIServiceExtensionAbility组件。

- UIServiceExtensionAbility组件的生命周期与绑定的窗口强关联，窗口销毁后UIServiceExtensionAbility组件也一起销毁。


## 启动UIServiceExtensionAbility组件

应用通过[startUIServiceExtensionAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startuiserviceextensionability14)方法启动一个UIServiceExtensionAbility组件。UIServiceExtensionAbility组件启动后，其生命周期独立于客户端，即使客户端已经销毁，该后台服务仍可继续运行，窗口创建失败或销毁后该服务会被销毁。


如下示例通过startUIServiceExtensionAbility方法启动一个UIServiceExtensionAbility组件，示例中的context的获取方式请参见[获取UIAbility的上下文信息](uiability-usage.md#获取uiability的上下文信息)。

<!-- @[service_ext_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIServiceExtensionAbility/entry/src/main/ets/pages/Start.ets) -->


## 客户端连接服务端

  客户端通过[connectUIServiceExtensionAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectuiserviceextensionability14)连接服务端，获取并保存[UIServiceProxy](../reference/apis-ability-kit/js-apis-inner-application-uiserviceproxy.md)对象。通过该proxy对象的[sendData()](../reference/apis-ability-kit/js-apis-inner-application-uiserviceproxy.md#uiserviceproxysenddata)方法发送数据给服务端。服务端通过UIServiceExtensionAbility类onData()（系统接口）方法接收客户端数据。

如下示例通过connectUIServiceExtensionAbility方法连接一个UIServiceExtensionAbility组件，示例中的context的获取方式请参见[获取UIAbility的上下文信息](uiability-usage.md#获取uiability的上下文信息)

<!-- @[connect_service_ext_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIServiceExtensionAbility/entry/src/main/ets/pages/Connect.ets) -->
