# 管理ArkTS卡片生命周期
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->

创建ArkTS卡片，需实现[FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md)生命周期接口。

1. 在EntryFormAbility.ets中，导入相关模块。

    <!-- @[import_entry_form_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/entryformability/EntryFormAbility.ts) --> 
    
    ``` TypeScript
    // entry/src/main/ets/entryformability/EntryFormAbility.ts
    import { formBindingData, FormExtensionAbility, formInfo, formProvider } from '@kit.FormKit';
    import { Configuration, Want } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    ```
    
2. 在EntryFormAbility.ets中，实现[FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md)生命周期接口，其中在onAddForm的入参[want](../reference/apis-ability-kit/js-apis-app-ability-want.md)中可以通过[FormParam](../reference/apis-form-kit/js-apis-app-form-formInfo.md#formparam)取出卡片的相关信息。

    <!-- @[entry_form_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/entryformability/EntryFormAbility.ts) --> 
    
> **说明：**
>
> FormExtensionAbility进程不能常驻后台，即在卡片生命周期回调函数中无法处理长时间的任务，在生命周期调度完成后会继续存在10秒，若在10秒内未收到新的生命周期回调，则进程将自动退出。针对可能需要10秒以上才能完成的业务逻辑，建议[拉起主应用](arkts-ui-widget-event-overview.md)进行处理，处理完成后使用[updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform)通知卡片进行刷新。
