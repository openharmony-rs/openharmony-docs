# 根据卡片状态刷新不同内容
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @chenmingze-->
<!--Adviser: @Brilliantry_Rui-->

相同的卡片可以添加到桌面上实现不同的功能，比如添加两张桌面的卡片，一张显示杭州的天气，一张显示北京的天气，设置每天早上7点触发定时刷新，卡片需要感知当前的配置是杭州还是北京，然后将对应城市的天气信息刷新到卡片上，以下示例介绍了如何根据卡片的状态动态选择需要刷新的内容。


- 卡片配置文件：配置每30分钟自动刷新。

  ```json
  {
    "forms": [
      {
        "name": "WidgetUpdateByStatus",
        "description": "$string:UpdateByStatusFormAbility_desc",
        "src": "./ets/widgetupdatebystatus/pages/WidgetUpdateByStatusCard.ets",
        "uiSyntax": "arkts",
        "window": {
          "designWidth": 720,
          "autoDesignWidth": true
        },
        "isDefault": true,
        "updateEnabled": true,
        "scheduledUpdateTime": "10:30",
        "updateDuration": 1,
        "defaultDimension": "2*2",
        "supportDimensions": [
          "2*2"
        ]
      }
    ]
  }
  ```

- 卡片页面：卡片具备不同的状态选择，在不同的状态下需要刷新不同的内容，因此在状态发生变化时通过postCardAction通知EntryFormAbility。


<!-- @[widget_update_by_status_card](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/widgetupdatebystatus/pages/WidgetUpdateByStatusCard.ets) -->

- EntryFormAbility：将卡片的状态存储在本地数据库中，在刷新事件回调触发时，通过formId获取当前卡片的状态，然后根据卡片的状态选择不同的刷新内容。


<!-- @[update_by_status_form_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/updatebystatusformability/UpdateByStatusFormAbility.ts) -->



> **说明：**
>
> 通过本地数据库进行卡片信息的持久化时，建议先在[**onAddForm**](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonaddform)生命周期进行卡片信息持久化；同时需要在卡片销毁(**[onRemoveForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonremoveform)**)时删除当前卡片存储的持久化信息，避免反复添加删除卡片导致数据库文件持续变大。