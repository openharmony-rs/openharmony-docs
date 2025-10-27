# UIAbility组件与UI的数据同步

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->


基于当前的应用模型，可以通过以下几种方式来实现[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)组件与UI之间的数据同步。

- [使用EventHub进行数据通信](#使用eventhub进行数据通信)：在[基类Context](../reference/apis-ability-kit/js-apis-inner-application-context.md)中提供了[EventHub](../reference/apis-ability-kit/js-apis-inner-application-eventHub.md)对象，可以通过发布订阅方式来实现事件的传递。在事件传递前，订阅者需要先进行订阅，当发布者发布事件时，订阅者将接收到事件并进行相应处理。
- [使用AppStorage/LocalStorage进行数据同步](#使用appstoragelocalstorage进行数据同步)：ArkUI提供了[AppStorage](../ui/state-management/arkts-appstorage.md)和[LocalStorage](../ui/state-management/arkts-localstorage.md)两种应用级别的状态管理方案，可用于实现应用级别和UIAbility级别的数据同步。


## 使用EventHub进行数据通信

[EventHub](../reference/apis-ability-kit/js-apis-inner-application-eventHub.md)为[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)组件提供了事件机制，使它们能够进行订阅、取消订阅和触发事件等数据通信能力。

在[基类Context](../reference/apis-ability-kit/js-apis-inner-application-context.md)中，提供了EventHub对象，可用于在UIAbility组件实例内通信。使用EventHub实现UIAbility与UI之间的数据通信需要先获取EventHub对象，本章节将以此为例进行说明。

1. 在UIAbility中调用[eventHub.on()](../reference/apis-ability-kit/js-apis-inner-application-eventHub.md#eventhubon)方法注册一个自定义事件“event1”，eventHub.on()有如下两种调用方式，使用其中一种即可。

<!-- @[onCreate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityDataSync/entry/src/main/ets/entryability/EntryAbility.ets) -->

2. 在UI中通过[eventHub.emit()](../reference/apis-ability-kit/js-apis-inner-application-eventHub.md#eventhubemit)方法触发该事件，在触发事件的同时，根据需要传入参数信息。

<!-- @[EventHubPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityDataSync/entry/src/main/ets/pages/EventHubPage.ets) -->

3. 在UIAbility的注册事件回调中可以得到对应的触发事件结果，运行日志结果如下所示。

    ```json
    [Example].[Entry].[EntryAbility] 1. []
    [Example].[Entry].[EntryAbility] 1. [1]
    [Example].[Entry].[EntryAbility] 1. [2,"test"]
    ```
   
4. 在自定义事件“event1”使用完成后，可以根据需要调用[eventHub.off()](../reference/apis-ability-kit/js-apis-inner-application-eventHub.md#eventhuboff)方法取消该事件的订阅。

<!-- @[onDestroy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UIAbilityDataSync/entry/src/main/ets/entryability/EntryAbility.ets) -->

## 使用AppStorage/LocalStorage进行数据同步

ArkUI提供了[AppStorage](../ui/state-management/arkts-appstorage.md)和[LocalStorage](../ui/state-management/arkts-localstorage.md)两种应用级别的状态管理方案，可用于实现应用级别和[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)级别的数据同步。使用这些方案可以方便地管理应用状态，提高应用性能和用户体验。其中，AppStorage是一个全局的状态管理器，适用于多个UIAbility共享同一状态数据的情况；而LocalStorage则是一个局部的状态管理器，适用于单个UIAbility内部使用的状态数据。通过这两种方案，开发者可以更加灵活地控制应用状态，提高应用的可维护性和可扩展性。详细请参见[应用级变量的状态管理](../ui/state-management/arkts-application-state-management-overview.md)。

