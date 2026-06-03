# Using Audio Template
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:22:03.202Z pushedAt=2026-06-03T10:01:26.364Z -->

Starting from API version 23, media applications can use the audio template to access the Playback Control Center (a system application), enabling unified UI display and playback control management for audio and video in the Playback Control Center, thereby reducing the development workload on the application side. This document introduces the audio template interface capabilities and the basic development process, including accessing the Playback Control Center through the audio template, reporting media-related information (such as title, author, and playback status) to the Playback Control Center, and responding to operation commands (such as play, pause, search, and favorite) issued by the Playback Control Center.

The audio template supports both audio and video content, and the access method is the same for both. This document uses an audio scenario as an example for illustration.

> **NOTE**
>
> This feature is only supported in Car device projects with API version 23 or later. When creating a project, select "Car" in **Device type**.

## Basic Concepts

Audio template (AVMusicTemplate): A class that describes audio template-related capabilities, including attributes such as the ID identifying the current media session (sessionId) and session tag (sessionTag), as well as operation methods for data interaction with the Playback Control Center. Media applications can report media-related information to the Playback Control Center through the audio template and respond to operation commands from the Playback Control Center.

## API Description

For details about the API, see [AVMusicTemplate](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md).

## How to Develop

The basic steps for a media application to access the audio template are as follows:

1. When the process starts, call the API [createAVMusicTemplate](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-f.md#avmusictemplatecreateavmusictemplate) to create an audio template instance (each media application creates one audio template instance; repeated creation is unnecessary) and launch the audio template.

   The following sample code only demonstrates the API call for creating an AVMusicTemplate object. When actually using it, the application needs to refer to the API [@ohos.backgroundTaskManager (Background Task Management)](../../reference/apis-backgroundtasks-kit/js-apis-backgroundTaskManager.md) to ensure that the AVMusicTemplate object instance persists throughout the application's background playback activity, preventing it from being reclaimed or released by the system, which would cause the system to restrict background audio playback.

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
   import { avMusicTemplate } from '@kit.AVSessionKit';
   // ...
   
   export class TemplateManager {
     private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
     private static sInstance: TemplateManager;
     // ...
     private constructor() {
     }
   
     /**      * Obtains the template controller instance.
      *
      * @returns Template controller instance.
      */
     public static getInstance(): TemplateManager {
       if (!TemplateManager.sInstance) {
         TemplateManager.sInstance = new TemplateManager();
       }
       return TemplateManager.sInstance;
     };
   
     /**      * Creates an audio template.
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

2. Register event listeners. After listening for events, you can provide application data for the audio template to use. For details about the listener APIs, see [AVMusicTemplate](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md).

   The main interface of the audio template requires the following two interfaces to be registered simultaneously:

   - [onQueryMainTabs](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md#onquerymaintabs): Registers a listener for querying main tab events. Provides the TAB data set displayed on the main interface, and specifies that the tabId of "My Homepage" is "minePage".
   - [onQueryMediaTabContent](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md#onquerymediatabcontent): Registers a listener for querying media tab content events. Provides page display content data based on the tabId.

   <!-- @[template_register_listener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->

   ``` TypeScript
   import { avMusicTemplate } from '@kit.AVSessionKit';
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
   
     /**      * Registers a listener.
      */
     private registerListener() {
       this.template?.onQueryMainTabs(this.queryMainTabsEvent);
       this.template?.onQueryMediaTabContent(this.queryMediaTabContentEvent);
       // ...
     };
   
     // ...
     /**      * Simulates obtaining all TABs on the main interface.
      *
      * @returns Promise type MediaTab array.
      */
     private async getMainTabs(): Promise<avMusicTemplate.MediaTab[]> {
       let homeTab: avMusicTemplate.MediaTab = {
         tabId: 'home',
         tabName: 'Home'
       };
       let mineTab: avMusicTemplate.MediaTab = {
         tabId: 'mine',
         tabName: 'Mine'
       };
       let mainTabs: avMusicTemplate.MediaTab[] = [homeTab, mineTab];
       return mainTabs;
     };
   
     /**      * Simulates obtaining TAB content.
      *
      * @returns Tab content.
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
   
     /**      * Simulates obtaining collection data.
      *
      * @returns Collection.
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
   
     /**      * Simulates obtaining media data.
      *
      * @returns Media data.
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


3. In scenarios that the audio template cannot directly perceive (such as login and download), the media application needs to actively synchronize data to the audio template. For details about the synchronization APIs, see [AVMusicTemplate](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md).

   For example, in a scenario where QR code login is successful. When a user logs in by scanning a QR code on the audio template UI, the login status can only be perceived by the media application. Therefore, you need to call the [setUserInfo](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md#setuserinfo) API to synchronize data to the audio template.

   <!-- @[set_user_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->

   ``` TypeScript
   import { avMusicTemplate } from '@kit.AVSessionKit';
   // ...
   
   export class TemplateManager {
     private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
     // ...
     private isLogin: boolean = false;
     // ...
   
     /**      * Simulates a login status change.
      *
      * @param isLogin Whether the user is logged in.
      */
     public setLoginState(isLogin: boolean) {
       this.isLogin = isLogin;
       this.setUserInfo();
     }
   
     /**      * Notifies the UI to refresh user information after the user information changes, for example, after logging in to an account.
      */
     public setUserInfo() {
       let userInfo: avMusicTemplate.UserInfo = {
         userInfoId: this.isLogin ? 'userInfoId' : '',
         nickName: this.isLogin ? 'Nickname' : '',
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

4. The event listeners registered when the media application starts must be unregistered when the application exits to release resources. For details about the unregistration API, see [AVMusicTemplate](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md).

   <!-- @[unregister_listener](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->

   ``` TypeScript
   import { avMusicTemplate } from '@kit.AVSessionKit';
   // ...
   
   export class TemplateManager {
     private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
     // ...
     /**      * Unregister listeners.
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