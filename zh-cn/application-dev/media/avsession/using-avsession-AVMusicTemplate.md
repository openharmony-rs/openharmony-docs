# 媒体应用接入指南
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->
媒体应用在实现音频功能时，需要作为音频模板提供方接入媒体会话系统。具体而言，媒体应用需要：
1. 在媒体中心（作为音频模板控制方）展示音频相关信息。
2. 响应媒体中心下发的播放控制命令。

需要注意的是，音频模板控制方不仅支持音频，还支持视频内容，两者的接入方式相同。本文档以音频场景为例进行说明。

## 基本概念

音频模板（AVMusicTemplate）： 用于描述音频模板相关属性，包含标识当前媒体会话的ID（sessionId）、会话标签（sessionTag）和操作方法等属性。


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
   
   ``` TypeScript
   import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';
   // ...
   
   export class TemplateManager {
     private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
     private static sInstance: TemplateManager;
     // ...
     private constructor() {
     }
   
     /**
      * 获取模板控制器实例。
      *
      * @returns 模板控制器实例。
      */
     public static getInstance(): TemplateManager {
       if (!TemplateManager.sInstance) {
         TemplateManager.sInstance = new TemplateManager();
       }
       return TemplateManager.sInstance;
     };
   
     /**
      * 创建音频模板。
      */
     public createTemplate() {
       if (this.template) {
         console.warn('createTemplate: template not undefined');
         return
       }
       try {
         this.template = avMusicTemplate.createAVMusicTemplate(avMusicTemplate.AVMusicTemplateType.DEFAULT);
         console.info('createTemplate: success');
         // ...
       } catch (e) {
         console.error(`createTemplate, errCode: ${e?.code}`);
       }
     }
     // ...
   }
   ```
   
2. 根据需要注册事件监听，并提供相应信息的获取方法。音频应用设置的音频模板信息，会被音频模板控制方通过AVMusicTemplateController相关方法获取后进行显示或处理。例如主界面显示，需要如下接口，详情请查看[AVMusicTemplate API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplate.md)。
   
   - onQueryMainTabs：注册查询主标签事件监听。提供主界面展示的TAB数据集合，并规定“我的主页”的tabId（媒体中心的为"minePage"）。
   - onQueryMediaTabContent：注册查询媒体标签内容事件监听。根据tabId提供页面展示内容数据。
   
   <!-- @[template_register_listener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->
   
   ``` TypeScript
   import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';
   // ...
   
   export class TemplateManager {
     private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
     // ...
     private queryMainTabsEvent: avMusicTemplate.QueryMainTabsEvent = async () => {
       return new Promise<avMusicTemplate.MediaTab[]>(async (resolve, reject) => {
         try {
           let tabs: avMusicTemplate.MediaTab[] = await this.getMainTabs();
           resolve(tabs);
         } catch (e) {
           console.error(`queryMainTabsEvent fail, errCode: ${e?.code}`);
           reject(e);
         }
       });
     };
     private queryMediaTabContentEvent: avMusicTemplate.QueryMediaTabContentEvent = async (tabId: string) => {
       return new Promise<avMusicTemplate.MediaTabContent>(async (resolve, reject) => {
         try {
           let tabContent: avMusicTemplate.MediaTabContent = await this.createMediaTabContent();
           resolve(tabContent);
         } catch (e) {
           console.error(`queryMediaTabContentEvent fail, errCode: ${e?.code}`);
           reject(e);
         }
       });
     };
     // ...
   
     /**
      * 注册监听。
      */
     private registerListener() {
       this.template?.onQueryMainTabs(this.queryMainTabsEvent);
       this.template?.onQueryMediaTabContent(this.queryMediaTabContentEvent);
       // ...
     };
   
     // ...
     /**
      * 模拟获取主界面的所有TAB。
      *
      * @returns Promise类型MediaTab数组
      */
     private async getMainTabs(): Promise<avMusicTemplate.MediaTab[]> {
       let homeTab: avMusicTemplate.MediaTab = {
         tabId: 'home',
         tabName: '首页'
       };
       let mineTab: avMusicTemplate.MediaTab = {
         tabId: 'mine',
         tabName: '我的'
       };
       let mainTabs: avMusicTemplate.MediaTab[] = [homeTab, mineTab];
       return mainTabs;
     };
   
     /**
      * 模拟获取TAB内容。
      *
      * @returns 标签页内容。
      */
     private async createMediaTabContent(): Promise<avMusicTemplate.MediaTabContent> {
       let compilation: avMusicTemplate.Compilation = await this.createCompilation();
       let mediaTabContent: avMusicTemplate.MediaTabContent = {
         errorCode: 0,
         tabId: 'tabId',
         compilations: [compilation]
       }
       return mediaTabContent;
     };
   
     /**
      * 模拟获取合集数据。
      *
      * @returns 合集
      */
     private async createCompilation(): Promise<avMusicTemplate.Compilation> {
       let mediaEntity: avMusicTemplate.MediaEntity = await this.createMediaEntity();
       let compilation: avMusicTemplate.Compilation = {
         errorCode: 0,
         id: '',
         title: '',
         hasMoreData: false,
         totalSize: 1,
         memberMediaType: avMusicTemplate.EntityType.SINGLE,
         topElements: [mediaEntity],
       }
       return compilation;
     };
   
     /**
      * 模拟获取媒体数据
      *
      * @returns 媒体数据
      */
     private async createMediaEntity(): Promise<avMusicTemplate.MediaEntity> {
       let mediaEntity: avMusicTemplate.MediaEntity = {
         mediaId: 'mediaId',
         mediaType: avMusicTemplate.EntityType.SINGLE,
         parentId: 'parentId',
         parentMediaType: avMusicTemplate.EntityType.SINGLE,
         title: 'title',
         imageUrl: 'imageUrl',
         playState: avMusicTemplate.PlaybackState.PLAYBACK_STATE_PREPARE
       };
       return mediaEntity;
     };
     // ...
   }
   ```


3. 在音频模板控制方无法直接感知的场景，需要媒体应用主动向已注册了对应接口的音频模板控制方同步数据。例如扫码登录成功的场景，需要如下接口，详情请查看[AVMusicTemplate API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplate.md)。
   
   - setUserInfo：向音频模板控制方同步用户信息。用户在音频模板控制方界面扫码登录，由于登录状态只有音频模板控制方能感知，所以需要主动同步数据。
   
   <!-- @[set_user_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->
   
   ``` TypeScript
   import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';
   // ...
   
   export class TemplateManager {
     private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
     // ...
     private isLogin: boolean = false;
     // ...
   
     /**
      * 模拟登录状态改变。
      *
      * @param isLogin 是否登录。
      */
     public setLoginState(isLogin: boolean) {
       this.isLogin = isLogin;
       this.setUserInfo();
     }
   
     /**
      * 用户信息发生变化后通知界面刷新用户信息，如登陆账号后。
      */
     public setUserInfo() {
       let userInfo: avMusicTemplate.UserInfo = {
         userInfoId: this.isLogin ? 'userInfoId' : '',
         nickName: this.isLogin ? '昵称' : '',
         profilePicUrl: this.isLogin ? 'profilePicUrl' : '',
         tips: this.isLogin ? 'tips' : '',
         isLogin: this.isLogin,
         isVip: false
       };
       this.template?.setUserInfo(userInfo);
     };
     // ...
   }
   ```
   
4. 媒体应用根据实际注册，在退出时及时注销事件监听，并释放资源。详情请查看[AVMusicTemplate API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplate.md)。

   <!-- @[unregister_listener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->
   
   ``` TypeScript
   import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';
   // ...
   
   export class TemplateManager {
     private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
     // ...
     /**
      * 注销监听。
      */
     public unregisterListener() {
       this.template?.offQueryMainTabs();
       this.template?.offQueryMediaTabContent();
       this.template?.offQueryMediaEntity();
       this.template?.offQueryCompilation();
       this.template?.offQueryPlaylist();
       this.template?.offQueryCurrentSingle();
       this.template?.offQueryCompilationByKeyword();
       this.template?.offQueryMediaEntityByKeyword();
       this.template?.offQueryRecommendMediaEntityList();
       this.template?.offQueryHotWords();
       this.template?.offQuerySearchHistory();
       this.template?.offClearSearchHistory();
       this.template?.offLogin();
       this.template?.offRequestDialogInfo();
       this.template?.offHandleMemberPurchase();
       this.template?.offQueryMemberPurchase();
       this.template?.offQueryCustomContent();
       this.template?.offDownloadMediaEntity();
       this.template?.offSettingsChange();
       this.template?.offProblemAndAdvice();
       this.template?.offPlayForSearch();
       this.template?.offExecuteAction();
       this.template?.offPlayMediaEntity();
       this.template?.offFavoriteMediaEntity();
       this.template?.destroy();
       this.template = undefined;
     };
     // ...
   }
   ```
