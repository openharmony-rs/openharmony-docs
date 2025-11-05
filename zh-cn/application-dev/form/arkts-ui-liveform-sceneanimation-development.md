# 场景动效类型互动卡片开发指导
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @chenmingze-->
<!--Adviser: @Brilliantry_Rui-->
本文档提供了场景动效类型互动卡片的开发指导，包括卡片非激活态和激活态UI界面开发、卡片配置文件开发。

## 接口说明

场景动效类型互动卡片关键接口如下表所示。

**表1** 主要接口

| 接口名                                                                                                                                                                                                 | 描述                 |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|
| [onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void](../reference/apis-form-kit/js-apis-app-form-LiveFormExtensionAbility.md#onliveformcreate)                  | 互动卡片界面对象创建的回调函数。   |
| [onLiveFormDestroy(liveFormInfo: LiveFormInfo): void](../reference/apis-form-kit/js-apis-app-form-LiveFormExtensionAbility.md#onliveformdestroy)                                                    | 互动卡片界面对象销毁、资源清理的回调函数。  |
| [startAbilityByLiveForm(want: Want): Promise&lt;void&gt;](../reference/apis-form-kit/js-apis-application-LiveFormExtensionContext.md#startabilitybyliveform)| 拉起互动卡片提供方（应用）的页面。 |
| [formProvider.requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise&lt;void&gt;](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderrequestoverflow20) | 卡片提供方发起互动卡片动效请求。   |
| [formProvider.cancelOverflow(formId: string): Promise&lt;void&gt;](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formprovidercanceloverflow20)                                        | 卡片提供方发起取消互动卡片动效请求。 |
| [formProvider.getFormRect(formId: string): Promise&lt;formInfo.Rect&gt;](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formprovidergetformrect20)                                        | 卡片提供方查询卡片位置、尺寸。 |

## 开发流程

### 卡片激活态UI开发

1. 创建互动卡片

   通过[LiveFormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-LiveFormExtensionAbility.md)创建互动卡片，创建时加载互动卡片页面。

    <!-- @[liveform_LiveFormExtensionAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormLiveDemo/entry/src/main/ets/myliveformextensionability/MyLiveFormExtensionAbility.ets) -->
    
    ``` TypeScript
    // entry/src/main/ets/myliveformextensionability/MyLiveFormExtensionAbility.ets
    import { formInfo, LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
    import { UIExtensionContentSession } from '@kit.AbilityKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    
    const DOMAIN = 0x0000;
    
    export default class MyLiveFormExtensionAbility extends LiveFormExtensionAbility {
      onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
        let storage: LocalStorage = new LocalStorage();
        storage.setOrCreate('context', this.context);
        storage.setOrCreate('session', session);
        let formId: string = liveFormInfo.formId;
        storage.setOrCreate('formId', formId);
    
        // 获取卡片圆角信息
        let borderRadius: number = liveFormInfo.borderRadius;
        storage.setOrCreate('borderRadius', borderRadius);
    
        // liveFormInfo.rect字段表示非激活态卡片组件相对激活态UI的位置和尺寸信息
        let formRect: formInfo.Rect = liveFormInfo.rect;
        storage.setOrCreate('formRect', formRect);
        hilog.info(DOMAIN, 'testTag', `startAbilityByLiveForm onSessionCreate formId: ${formId}` +
          `, borderRadius: ${borderRadius}, formRectInfo: ${JSON.stringify(formRect)}`);
    
        // 加载互动页面
        session.loadContent('myliveformextensionability/pages/MyLiveFormPage', storage);
      }
    
      onLiveFormDestroy(liveFormInfo: LiveFormInfo) {
        hilog.info(DOMAIN, 'testTag', `startAbilityByLiveForm onDestroy`);
      }
    };
    ```


2. 实现互动卡片页面

    <!-- @[liveform_MyLiveFormPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormLiveDemo/entry/src/main/ets/myliveformextensionability/pages/MyLiveFormPage.ets) -->


3. 互动卡片LiveFormExtensionAbility配置

   在module.json5配置文件中[extensionAbilities标签](../quick-start/module-configuration-file.md#extensionabilities标签)下配置LiveFormExtensionAbility。

    <!-- @[liveform_moudlejson5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormLiveDemo/entry/src/main/module.json5) -->


   在main_pages.json文件中声明互动卡片页面。

    ```ts
    // entry/src/main/resources/base/profile/main_pages.json
    {
      "src": [
        "pages/Index",
        "myliveformextensionability/pages/MyLiveFormPage"
      ]
    }
    ```

### 卡片非激活态UI开发

1. 非激活态卡片页面实现

   非激活态卡片页面开发同普通卡片开发流程完全一致，在widgetCard.ets中完成。widgetCard.ets文件在卡片创建时自动生成，卡片创建流程可以参考[创建ArkTS卡片](arkts-ui-widget-creation.md)。在非激活态卡片页面实现点击卡片时，发起卡片动效请求。

    <!-- @[liveform_WidgetCard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormLiveDemo/entry/src/main/ets/widget/pages/WidgetCard.ets) -->


2. form_config.json配置

   在form_config.json配置文件中新增sceneAnimationParams配置项。

    ```ts
    // entry/src/main/resources/base/profile/form_config.json
    {
      "forms": [
        {
          "name": "widget",
          "displayName": "$string:widget_display_name",
          "description": "$string:widget_desc",
          "src": "./ets/widget/pages/WidgetCard.ets",
          "uiSyntax": "arkts",
          "window": {
            "designWidth": 720,
            "autoDesignWidth": true
          },
          "colorMode": "auto",
          "isDefault": true,
          "updateEnabled": true,
          "scheduledUpdateTime": "10:30",
          "updateDuration": 1,
          "defaultDimension": "2*2",
          "supportDimensions": [
            "2*2"
          ],
          "formConfigAbility": "ability://EntryAbility",
          "dataProxyEnabled": false,
          "isDynamic": true,
          "transparencyEnabled": false,
          "metadata": [],
          "sceneAnimationParams": {
            "abilityName": "MyLiveFormExtensionAbility"
          }
        }
      ]
    }
    ```   

### 互动卡片动效实现

1. 触发互动卡片动效

   互动卡片通过调用[formProvider.requestOverflow](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderrequestoverflow20)接口触发动效，调用时需要明确：（1）动效申请范围。（2）动效持续时间。（3）是否使用系统提供的默认切换动效。具体可参考[formInfo.OverflowInfo](../reference/apis-form-kit/js-apis-app-form-formInfo.md#overflowinfo20)。其中，互动卡片可以通过调用[formProvider.getFormRect](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formprovidergetformrect20)接口获取卡片尺寸和在窗口内的位置信息。卡片提供方以此计算动效申请范围，单位为vp。计算规则具体请参考[互动卡片请求参数约束](arkts-ui-liveform-sceneanimation-overview.md#请求参数约束)。

    <!-- @[liveform_EntryFormAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormLiveDemo/entry/src/main/ets/entryformability/EntryFormAbility.ets) -->


2. 互动卡片动效工具函数实现

    <!-- @[liveform_Constants](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormLiveDemo/entry/src/main/ets/common/Constants.ets) -->


3. 需要的资源文件string.json

    ```json
    {
        "string": [
          {
            "name": "liveform_click1",
            "value": "点击触发互动卡片动效"
          },
          {
            "name": "button_cancel",
            "value": "强制取消动效"
          }
        ]
    }
    ```

## 实现效果
以下是按照本文档代码示例开发而成的效果demo，demo执行动效时，点击按钮，将调用 [formProvider.cancelOverflow](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formprovidercanceloverflow20) 接口，打断当前破框动效，卡片切换为非激活态。

![live-form-base-demo.gif](figures/live-form-base-demo.gif)