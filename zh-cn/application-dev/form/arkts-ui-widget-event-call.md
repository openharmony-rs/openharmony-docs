# 卡片拉起应用UIAbility到后台（call事件）
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @chenmingze-->
<!--Adviser: @Brilliantry_Rui-->

许多应用希望借助卡片的能力，实现和应用在前台时相同的功能。例如音乐卡片，卡片上提供播放、暂停等按钮，点击不同按钮将触发音乐应用的不同功能，进而提高用户的体验。在卡片中使用[postCardAction](../reference/apis-arkui/js-apis-postCardAction.md#postcardaction-1)接口的call能力，能够将卡片提供方应用的指定的UIAbility拉到后台。同时，call能力提供了调用应用指定方法、传递数据的功能，使应用在后台运行时可以通过卡片上的按钮执行不同的功能。

> **说明：**
>
> 本文主要介绍动态卡片的事件开发。对于静态卡片，请参见[FormLink](../reference/apis-arkui/arkui-ts/ts-container-formlink.md)。

## 开发步骤
1. 创建动态卡片

    新建一个名为WidgetEventCall的ArkTs动态卡片。

2. 页面布局代码实现

    在卡片页面中布局两个按钮，点击按钮A或按钮B，会调用postCardAction向指定UIAbility发送call事件，在call事件内定义了需要调用的方法。按钮A和按钮B分别对应调用funA、funB方法，其中funA携带了formID参数，funB携带了formID和num参数，开发过程中请根据实际需要传参。postCardAction中的method参数为必填参数，用于标识需要调用的方法名称，与步骤3中UIAbility监听的方法一致，其他参数为非必填。

<!-- @[widget_event_call_card](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/widgeteventcall/pages/WidgetEventCallCard.ets) -->

3. 创建指定的UIAbility
    
    在UIAbility中监听call事件，根据监听到的method参数中的方法名称调用对应方法，并通过[rpc.Parcelable](../reference/apis-ipc-kit/js-apis-rpc.md#parcelable9)获取参数。UIAbility中监听的方法与步骤2中调用的方法需保持一致。

<!-- @[widget_event_call_card_entry_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/widgeteventcallentryability/WidgetEventCallEntryAbility.ets) -->

4. 配置后台运行权限

    call事件存在约束限制，卡片提供方应用需要在module.json5下添加后台运行权限([ohos.permission.KEEP_BACKGROUND_RUNNING](../security/AccessToken/permissions-for-all.md#ohospermissionkeep_background_running))。

<!-- @[module_json5_request_permissions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/module.json5) -->

5. 配置指定的UIAbility

    在module.json5的abilities数组内添加WidgetEventCallEntryAbility对应的配置信息。

<!-- @[module_json5_abilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/module.json5) -->
