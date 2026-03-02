# 媒体应用接入指南
媒体应用在实现音频功能的同时，需要作为音频模板提供方接入媒体会话，在音频模板控制方（例如媒体中心）中展示音频相关信息，并响应音频模板控制方下发的播控命令。音频模板控制方支持音频和视频，接入方式相同，以下仅以音频为例。

## 基本概念

- 音频模板（AVMusicTemplate）： 用于描述音频模板相关属性，包含标识当前媒体会话的ID（sessionId），会话标签（sessionTag），操作方法等属性。


## 接口说明

详细的API说明请参考[AVMusicTemplate API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplate.md)。

## 开发步骤

音频应用作为音频模板提供方接入音频模板控制方的基本步骤如下所示：

1. 在进程启动时，创建音频模板（模板唯一，不需要重复创建），拉起音频模板控制方。需要如下接口，详情请查看[模板API接口](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplate-f.md)。

   > **说明：**
   >
   > 以下示例代码仅展示创建AVMusicTemplate对象的接口调用，应用在真正使用时，需要确保AVMusicTemplate对象实例在应用后台播放业务活动期间一直存在，避免被系统回收、释放，导致后台发声时被系统管控。

   - createAVMusicTemplate：创建音频模板。
   
   <!-- @[ability_create_template](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { TemplateManager } from '../manager/TemplateManager';
   
   export default class EntryAbility extends UIAbility {
     onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
       console.info('onCreate');
       TemplateManager.getInstance().createTemplate();
     }
   
     // ...
     onForeground(): void {
       console.info('onForeground');
       this.startTemplateControllerAbility();
     }
   
     private startTemplateControllerAbility() {
       let want: Want = {
         bundleName: 'com.example.templatecontroller',
         abilityName: 'EntryAbility',
         parameters: {
           bundleName: 'com.example.templateprovider'
         }
       }
       this.context.startAbility(want).then(() => {
         console.info('startTemplateControllerAbility: startAbility success');
       }).catch((e: BusinessError) => {
         console.error(`startTemplateControllerAbility: startAbility: errCode: ${e?.code}}`);
       });
     }
   }
   ```
   
   <!-- @[manager_create_template](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->
   
2. 根据需要注册事件监听，并提供相应信息的获取方法。音频应用设置的音频模板信息，会被音频模板控制方通过AVMusicTemplateController相关方法获取后进行显示或处理。例如主界面显示，需要如下接口，详情请查看[AVMusicTemplate API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplate.md)。
   
   - onQueryMainTabs：注册查询主标签事件监听。提供主界面展示的TAB数据集合，并约定我的界面的tabId（媒体中心的为"minePage"）。
   - onQueryMediaTabContent：注册查询媒体标签内容事件监听。根据tabId提供页面展示内容数据。
   
   <!-- @[template_register_listener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->


3. 在音频模板控制方无法直接感知的场景，需要媒体应用主动向音频模板控制方同步数据（需要音频模板控制方已经注册了对应的接口）。例如扫码登录成功的场景，需要如下接口，详情请查看[AVMusicTemplate API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplate.md)。
   
   - setUserInfo：向音频模板控制方同步用户信息。用户在音频模板控制方界面扫码登录，而登录状态只有音频模板控制方才能感知，此时需要主动同步数据。
   
   <!-- @[set_user_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->
   
4. 媒体应用根据实际注册，在退出时及时注销事件监听，并释放资源。详情请查看[AVMusicTemplate API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplate.md)。

   <!-- @[unregister_listener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->
