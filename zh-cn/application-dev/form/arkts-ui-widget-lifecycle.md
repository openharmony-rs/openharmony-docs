# 管理ArkTS卡片生命周期
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->

创建ArkTS卡片，需实现[FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md)生命周期接口。

1. 在EntryFormAbility.ets中，导入相关模块。

   ArkTS-Dyn示例：
    <!-- @[import_entry_form_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/entryformability/EntryFormAbility.ts) -->
    
    ``` TypeScript
    // entry/src/main/ets/entryformability/EntryFormAbility.ts
    import { formBindingData, FormExtensionAbility, formInfo, formProvider } from '@kit.FormKit';
    import { Configuration, Want } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    ```

   ArkTS-Sta示例：
    <!-- @[import_entry_form_abilitySta](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Form/FormSta/FormLifecycleSta/entry/src/main/ets/entryformability/EntryFormAbility.ets) -->
    
    ``` TypeScript
    // entry/src/main/ets/entryformability/EntryFormAbility.ets
    import formBindingData from '@ohos.app.form.formBindingData';
    import FormExtensionAbility from '@ohos.app.form.FormExtensionAbility';
    import formInfo from '@ohos.app.form.formInfo';
    import Want from '@ohos.app.ability.Want';
    import { Configuration } from '@ohos.app.ability.Configuration';
    import hilog from '@ohos.hilog';
    ```

2. 在EntryFormAbility.ets中，实现[FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md)生命周期接口，其中在onAddForm的入参[want](../reference/apis-ability-kit/js-apis-app-ability-want.md)中可以通过[FormParam](../reference/apis-form-kit/js-apis-app-form-formInfo.md#formparam)取出卡片的相关信息。

   ArkTS-Dyn示例：
    <!-- @[entry_form_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/entryformability/EntryFormAbility.ts) -->
    
    ``` TypeScript
    // entry/src/main/ets/entryformability/EntryFormAbility.ts
    const TAG: string = 'EntryFormAbility';
    const DOMAIN_NUMBER: number = 0xFF00;
    
    export default class EntryFormAbility extends FormExtensionAbility {
      onAddForm(want: Want): formBindingData.FormBindingData {
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onAddForm');
        hilog.info(DOMAIN_NUMBER, TAG, want.parameters?.[formInfo.FormParam.NAME_KEY] as string);
        // 卡片使用方创建卡片时触发，卡片提供方需要返回卡片数据绑定类
        let obj: Record<string, string> = {
          'title': 'titleOnAddForm',
          'detail': 'detailOnAddForm'
        };
        let formData: formBindingData.FormBindingData = formBindingData.createFormBindingData(obj);
        return formData;
      }
    
      onCastToNormalForm(formId: string): void {
        // 当前卡片使用方不会涉及该场景，无需实现该回调函数
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onCastToNormalForm');
      }
    
      onUpdateForm(formId: string): void {
        // 若卡片支持定时更新/定点更新/卡片使用方主动请求更新功能，则提供方需要重写该方法以支持数据更新
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onUpdateForm');
        let obj: Record<string, string> = {
          'title': 'titleOnUpdateForm',
          'detail': 'detailOnUpdateForm'
        };
        let formData: formBindingData.FormBindingData = formBindingData.createFormBindingData(obj);
        formProvider.updateForm(formId, formData).catch((error: BusinessError) => {
          hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] updateForm, error:' + JSON.stringify(error));
        });
      }
    
      onChangeFormVisibility(newStatus: Record<string, number>): void {
        // 卡片使用方发起可见或者不可见通知触发，提供方需要做相应的处理，仅系统应用生效
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onChangeFormVisibility');
      }
    
      onFormEvent(formId: string, message: string): void {
        // 若卡片支持触发事件，则需要重写该方法并实现对事件的触发
        hilog.info(DOMAIN_NUMBER, TAG, `FormAbility onFormEvent, formId = ${formId}, message: ${message}`);
        // ···
      }
    
      onRemoveForm(formId: string): void {
        // 删除卡片实例数据
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onRemoveForm');
        // 删除之前持久化的卡片实例数据
        // 此接口请根据实际情况实现，具体请参考：FormExtAbility Stage模型卡片实例
      }
    
      onConfigurationUpdate(config: Configuration) {
        // 当前formExtensionAbility存活时更新系统配置信息时触发的回调。
        // 需注意：formExtensionAbility创建后10秒内无操作将会被清理。
        hilog.info(DOMAIN_NUMBER, TAG, '[EntryFormAbility] onConfigurationUpdate:' + JSON.stringify(config));
      }
    
      onAcquireFormState(want: Want): formInfo.FormState {
        // 卡片提供方接收查询卡片状态通知接口，默认返回卡片初始状态。
        return formInfo.FormState.READY;
      }
    }
    ```

   ArkTS-Sta示例：
    <!-- @[entry_form_abilitySta](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Form/FormSta/FormLifecycleSta/entry/src/main/ets/entryformability/EntryFormAbility.ets) -->
    
    ``` TypeScript
    // entry/src/main/ets/entryformability/EntryFormAbility.ets
    
    const DOMAIN = 0x0000;
    
    function onAcquireFormStateCallback(want: Want): formInfo.FormState {
      hilog.info(DOMAIN, 'testTag', 'OnAcquireFormState register success');
      return formInfo.FormState.READY;
    }
    
    function onAcquireFormDataCallback(formId: string): Record<string, Object> {
      hilog.info(DOMAIN, 'testTag', 'onAcquireFormDataCallback success');
      let param: Record<string, Object> = {};
      param = {
        'title': 'onAcquireFormData'
      };
      return param;
    }
    
    function onShareFormCallback(formId: string): Record<string, Object> {
      hilog.info(DOMAIN, 'testTag', 'onAcquireFormDataCallback success');
      let param: Record<string, Object> = {};
      param = {
        'title': 'onShareForm'
      };
      return param;
    }
    
    export default class EntryFormAbility extends FormExtensionAbility {
      constructor() {
        hilog.info(DOMAIN, 'testTag', 'constructor register call');
        try {
          this.onStop = () => {
            hilog.info(DOMAIN, 'testTag', 'OnStop callback success');
          }
          hilog.info(DOMAIN, 'testTag', 'OnStop register success');
        } catch (err) {
          hilog.error(DOMAIN, 'testTag', `OnStop catch error code: ${err?.code}, message: ${err?.message}`);
        }
    
        this.onAcquireFormState = onAcquireFormStateCallback;
        this.onAcquireFormData = onAcquireFormDataCallback;
        this.onShareForm = onShareFormCallback;
      }
    
      onAddForm(want: Want): formBindingData.FormBindingData {
        // 卡片使用方创建卡片时触发，卡片提供方需要返回卡片数据绑定类
        let param: Record<string, string> = {};
        param = {
          'title1': 'description'
        };
        let data: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
        hilog.info(DOMAIN, 'testTag', `onAddForm testing FormBindingData`);
        return data;
      }
    
      onCastToNormalForm(formId: string): void {
        // 当前卡片使用方不会涉及该场景，无需实现该回调函数
        hilog.info(DOMAIN, 'testTag', 'onCastToNormalForm testing');
      }
    
      onUpdateForm(formId: string): void {
        // 若卡片支持定时更新/定点更新/卡片使用方主动请求更新功能，则提供方需要重写该方法以支持数据更新
        hilog.info(DOMAIN, 'testTag', 'onUpdateForm testing');
      }
    
      onChangeFormVisibility(newStatus: Record<string, int>): void {
        // 卡片使用方发起可见或者不可见通知触发，提供方需要做相应的处理，仅系统应用生效
        hilog.info(DOMAIN, 'testTag', 'onChangeFormVisibility testing');
      }
    
      onFormEvent(formId: string, message: string): void {
        // 若卡片支持触发事件，则需要重写该方法并实现对事件的触发
        hilog.info(DOMAIN, 'testTag', `onFormEvent testing ${message}`);
      }
    
      onRemoveForm(formId: string): void {
        // 删除卡片实例数据
        hilog.info(DOMAIN, 'testTag', 'onRemoveForm testing');
        // 删除之前持久化的卡片实例数据
        // 此接口请根据实际情况实现，具体请参考：FormExtAbility Stage模型卡片实例
      }
    
      onConfigurationUpdate(newConfig: Configuration): void {
        // 当前formExtensionAbility存活时更新系统配置信息时触发的回调。
        // 需注意：formExtensionAbility创建后10秒内无操作将会被清理。
        hilog.info(DOMAIN, 'testTag', 'onConfigurationUpdate testing');
      }
    
      onFormLocationChanged(formId: string, newFormLocation: formInfo.FormLocation): void {
        hilog.info(DOMAIN, 'testTag', 'onFormLocationChanged testing');
      }
    }
    ```

> **说明：**
>
> FormExtensionAbility进程不能常驻后台，即在卡片生命周期回调函数中无法处理长时间的任务，在生命周期调度完成后会继续存在10秒，若在10秒内未收到新的生命周期回调，则进程将自动退出。针对可能需要10秒以上才能完成的业务逻辑，建议[拉起主应用](arkts-ui-widget-event-overview.md)进行处理，处理完成后使用[updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform)通知卡片进行刷新。
