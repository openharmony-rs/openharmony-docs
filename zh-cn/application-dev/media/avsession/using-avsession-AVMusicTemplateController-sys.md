# 音频模板开发指南(仅对系统应用开放)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->
从API version 23开始，OpenHarmony系统预置的媒体中心，作为音频模板控制方与音视频应用进行交互，包括获取媒体信息进行展示以及下发播控命令等。系统应用开发者也可以根据需要，按照本章节的内容自行开发一款新的系统应用，作为音频模板控制方的角色，与系统中的音视频应用进行交互。音频模板控制方支持音频和视频，且接入方式相同，以下仅以音频为例。

## 基本概念

音频模板控制器（AVMusicTemplateController）：包含标识媒体会话的ID（sessionId）和是否已销毁（isDestroy）等。可通过其查询和接受媒体应用相关信息，下发播控指令。


## 接口说明

详细的API说明请参考[AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md)。

## 开发步骤

系统应用作为音频模板控制方接入音频模板的基本步骤如下所示：

1. 创建音频模板控制器。每一个媒体应用对应唯一模板控制器，不需要重复创建。监听音频模板状态，音频模板创建时，按sessionId创建控制器，音频模板销毁时，同步销毁控制器。

   - [getAllAVMusicTemplateDescriptors](../../reference/apis-avsession-kit/js-apis-avsession-avMusicTemplate-sys.md#avmusictemplategetallavmusictemplatedescriptors)：获取所有的音频模板描述。
   - [onAVMusicTemplateCreate](../../reference/apis-avsession-kit/js-apis-avsession-avMusicTemplate-sys.md#avmusictemplateonavmusictemplatecreate)：音频模板创建事件。
   - [onAVMusicTemplateDestroy](../../reference/apis-avsession-kit/js-apis-avsession-avMusicTemplate-sys.md#avmusictemplateonavmusictemplatedestroy)：音频模板销毁事件。
   
   <!-- @[create_controller](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateController/entry/src/main/ets/manager/ControllerManager.ets) -->
   
   ``` TypeScript
   import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';
   // ...
   
   const TAG: string = 'ControllerManager';
   
   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
     private currentBundleName: string | undefined = undefined;
     // ...
     private templateCreateCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
       (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
         if (this.isInvalid(descriptor)) {
           console.warn(TAG, 'templateCreateCallback: descriptor is invalid');
           return;
         }
         console.info(TAG, `templateCreateCallback, bundleName: ${descriptor.bundleName}`);
         this.createController(descriptor.sessionId, descriptor.bundleName);
       };
     private templateDestroyCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
       (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
         if (this.isInvalid(descriptor)) {
           console.warn(TAG, 'templateDestroyCallback: descriptor is invalid');
           return;
         }
         if (this.isStringEmpty(this.currentBundleName)) {
           console.warn(TAG, 'templateDestroyCallback: current bundleName is empty');
           return;
         }
         if (this.currentBundleName !== descriptor.bundleName) {
           console.warn(TAG, 'templateDestroyCallback: not current bundleName');
           return;
         }
         this.unregisterListener();
         this.destroyController();
       };
     // ...
   
     /**
      * 通过getAllAVMusicTemplateDescriptors创建模板。
      */
     public createAvMusicTemplateController(bundleName: string) {
       if (this.isStringEmpty(bundleName)) {
         console.warn(TAG, 'createAvMusicTemplateController: bundleName is empty');
         return;
       }
       this.currentBundleName = bundleName;
       try {
         // 该方法需要权限ohos.permission.MANAGE_MEDIA_RESOURCES
         let descriptors: avMusicTemplate.AVMusicTemplateDescriptor[] = avMusicTemplate.getAllAVMusicTemplateDescriptors();
         if (this.isEmptyArray(descriptors)) {
           console.info(TAG, 'createAvMusicTemplateController: descriptors is empty');
           return;
         }
         for (let descriptor of descriptors) {
           if (descriptor === null || descriptor === undefined) {
             console.warn(TAG, 'createAvMusicTemplateController: descriptor is invalid continue');
             continue;
           }
           if (this.currentBundleName === descriptor.bundleName) {
             this.createController(descriptor.sessionId, descriptor.bundleName);
             return;
           }
         }
       } catch (e) {
         console.error(TAG, `getAllAVMusicTemplateDescriptors failed, errCode: ${e?.code}`);
       }
     };
   
     private isInvalid<T>(obj: T): boolean {
       return obj === undefined || obj === null;
     }
   
     private isStringEmpty(str: string | undefined): boolean {
       return str === undefined || str === null || str.trim().length === 0;
     }
   
     private isEmptyArray<T>(array: T[]): boolean {
       return this.isInvalid(array) || array.length <= 0;
     }
   
     /**
      * 注册模板监听。
      */
     public registerAVMusicTemplateListener() {
       try {
         // 该方法需要权限ohos.permission.MANAGE_MEDIA_RESOURCES
         avMusicTemplate.onAVMusicTemplateCreate(this.templateCreateCallback);
         // 该方法需要权限ohos.permission.MANAGE_MEDIA_RESOURCES
         avMusicTemplate.onAVMusicTemplateDestroy(this.templateDestroyCallback);
       } catch (e) {
         console.error(TAG, `registerAVMusicTemplateListener: errCode: ${e?.code}`);
       }
     }
   
     private createController(sessionId: string, bundleName: string) {
       if (this.currentBundleName === null || this.currentBundleName === undefined) {
         console.warn(TAG, 'createController: sessionId is invalid');
         return;
       }
       if (sessionId === null || sessionId === undefined) {
         console.warn(TAG, 'createController: sessionId is invalid');
         return;
       }
       if (bundleName === null || bundleName === undefined) {
         console.warn(TAG, 'createController: bundleName is invalid');
         return;
       }
       if (this.currentBundleName !== bundleName) {
         console.warn(TAG, 'createController: not current bundleName');
         return;
       }
       if (this.controller != undefined) {
         console.warn(TAG, 'createController: controller not undefined');
         return;
       }
       try {
         this.controller = avMusicTemplate.createAVMusicTemplateController(sessionId);
         console.info(TAG, `createController success, bundleName: ${this.currentBundleName}`);
         // ...
       } catch (e) {
         console.error(TAG, `createController: errCode: ${e?.code}`);
       }
     }
   
     // ...
     /**
      * 注销监听。
      */
     public unregisterListener() {
       // 注销用户信息改变的监听。
       this.controller?.offUserInfoChange();
   
       // 注销弹框命令改变的监听。
       this.controller?.offDialogCommandChange();
   
       // 注销当前单曲改变的监听。
       this.controller?.offCurrentSingleChange();
   
       // 注销媒体实体改变的监听。
       this.controller?.offMediaEntitiesChange();
   
       // 注销标签页内容改变的监听。
       this.controller?.offTabContentChange();
   
       // 注销播放列表改变的监听。
       this.controller?.offPlaylistChange();
   
       // 注销下载媒体状态改变的监听。
       this.controller?.offDownloadMediaEntityStatusChange();
   
       // 注销自定义元素改变的监听。
       this.controller?.offCustomElementsChange();
   
       // 注销设置改变的监听。
       this.controller?.offSettingsChange();
   
       // 注销上报执行动作的监听。
       this.controller?.offReportExecuteAction();
   
       // 注销通知媒体中心拉起指定三方应用界面的信息的监听。
       this.controller?.offExtensionAbilityChange();
     }
   
     /**
      * 销毁控制器。
      */
     public destroyController() {
       console.info(TAG, 'destroyController')
       this.controller?.destroy();
       this.controller = undefined;
       this.currentBundleName = undefined;
     }
   
     /**
      * 反注册模板监听。
      */
     public unregisterAVMusicTemplateListener() {
       try {
         avMusicTemplate.offAVMusicTemplateCreate();
         avMusicTemplate.offAVMusicTemplateDestroy();
       } catch (e) {
         console.error(TAG, `unregisterAVMusicTemplateListener: errCode: ${e?.code}`);
       }
     }
     // ...
   }
   ```
   
2. 音频模板控制方可查询媒体应用提供的数据，用于界面展示。查询接口详情请查看[API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md)。例如，音频模板控制方主界面显示需要先调用接口[queryMainTabs](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md#querymaintabs)获取媒体应用主标签数据，再调用接口[queryMediaTabContent](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md#querymediatabcontent)根据tabId获取媒体应用标签页内容。

   <!-- @[query_home_content](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateController/entry/src/main/ets/manager/ControllerManager.ets) -->
   
   ``` TypeScript
   import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';
   // ...
   
   const TAG: string = 'ControllerManager';
   
   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
     // ...
   
     /**
      * 查询主标签。
      */
     public async queryMainTabs(): Promise<avMusicTemplate.MediaTab[]> {
       let tabs: avMusicTemplate.MediaTab[] = [];
       if (!this.controller) {
         console.info(TAG, 'queryMainTabs: controller is undefined')
         return tabs;
       }
       try {
         console.info(TAG, 'queryMainTabs')
         tabs = await this.controller.queryMainTabs();
       } catch (e) {
         console.error(TAG, `queryMainTabs failed, errCode: ${e?.code}`)
       }
       return tabs;
     }
   
     /**
      * 模拟查询媒体标签页内容。
      *
      * @param tabId 标签页ID。
      */
     public async queryMediaTabContent(tabId: string): Promise<avMusicTemplate.MediaTabContent | undefined> {
       try {
         let tabContent: avMusicTemplate.MediaTabContent | undefined = await this.controller?.queryMediaTabContent(tabId);
         if (tabContent?.errorCode != 0) {
           console.warn(TAG, 'queryMediaTabContent fail')
           return undefined;
         }
         console.info(TAG, 'queryMediaTabContent success')
         return tabContent;
       } catch (e) {
         console.error(TAG, `queryMediaTabContent failed, errCode: ${e?.code}`)
         return undefined;
       }
     }
     // ...
   }
   ```
   
3. 下发媒体控制指令。音频模板控制方根据操作下发指令给媒体应用。接口详情请查看[API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md)。例如，搜播需要调用接口[playForSearch](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md#playforsearch)。该接口支持音视频，示例仅以音频为例。视频需将参数实体类SearchPlayInfo的成员变量更换为SearchPlayVideoInfo类型的videoInfo。

   <!-- @[play_for_search](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateController/entry/src/main/ets/manager/ControllerManager.ets) -->
   
   ``` TypeScript
   import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';
   // ...
   
   const TAG: string = 'ControllerManager';
   
   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
     // ...
   
     /**
      * 模拟搜播。
      *
      * @returns Promise类型操作结果。
      */
     public async playForSearch(): Promise<boolean> {
       let command: avMusicTemplate.SearchPlayInfoType = avMusicTemplate.SearchPlayInfoType.PLAY_MUSIC;
       let searchPlayMusicItems: avMusicTemplate.SearchPlayMusicItem[] = [{
         entityId: 'entityId',
         entityName: 'entityName'
       }];
       let searchPlayMusicInfo: avMusicTemplate.SearchPlayMusicInfo = {
         items: searchPlayMusicItems,
         displayName: 'displayName',
         description: 'description'
       };
       let searchPlayInfo: avMusicTemplate.SearchPlayInfo = {
         musicInfo: searchPlayMusicInfo
       };
       try {
         let operResult: avMusicTemplate.OperResult | undefined =
           await this.controller?.playForSearch(command, searchPlayInfo);
         if (operResult?.errorCode != 0) {
           console.warn(TAG, 'playForSearch fail')
           return false;
         }
         console.info(TAG, 'playForSearch success')
         return true;
       } catch (e) {
         console.error(TAG, `playForSearch failed, errCode: ${e?.code}`)
         return false;
       }
     };
     // ...
   }
   ```
   
4. 在不能实时获取数据的场景下，音频模板控制方需要注册监听，接受音频模板提供方主动同步过来的数据。监听接口详情请查看[API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md)。例如，登录导致用户信息变化的场景，需要注册监听[onUserInfoChange](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md#onuserinfochange)。因为用户在音频模板控制方界面扫码登录，而登录状态只有媒体应用才能感知。

      <!-- @[register_user_info_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateController/entry/src/main/ets/manager/ControllerManager.ets) -->

   ``` TypeScript
   import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';
   // ...
   
   const TAG: string = 'ControllerManager';
   
   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
     // ...
     private userInfoChangeCallback: Callback<avMusicTemplate.UserInfo> = (userInfo: avMusicTemplate.UserInfo) => {
       console.info(TAG, 'userInfoChangeCallback');
     };
     // ...
   
     private registerListener() {
       // 注册用户信息改变的监听。
       this.controller?.onUserInfoChange(this.userInfoChangeCallback);
       // ...
     }
     // ...
   }
   ```
   
5. 在音频模板控制方应用退出时及时取消事件监听，并释放资源。注销音频模板接口详情请查看[音频模板API](../../reference/apis-avsession-kit/js-apis-avsession-avMusicTemplate-sys.md)，注销事件监听接口详情请查看[AVMusicTemplateController API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md)。

   <!-- @[release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateController/entry/src/main/ets/manager/ControllerManager.ets) -->
   
   ``` TypeScript
   import avMusicTemplate from '@ohos.multimedia.avMusicTemplate';
   // ...
   
   const TAG: string = 'ControllerManager';
   
   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
     private currentBundleName: string | undefined = undefined;
     // ...
     /**
      * 注销监听。
      */
     public unregisterListener() {
       // 注销用户信息改变的监听。
       this.controller?.offUserInfoChange();
   
       // 注销弹框命令改变的监听。
       this.controller?.offDialogCommandChange();
   
       // 注销当前单曲改变的监听。
       this.controller?.offCurrentSingleChange();
   
       // 注销媒体实体改变的监听。
       this.controller?.offMediaEntitiesChange();
   
       // 注销标签页内容改变的监听。
       this.controller?.offTabContentChange();
   
       // 注销播放列表改变的监听。
       this.controller?.offPlaylistChange();
   
       // 注销下载媒体状态改变的监听。
       this.controller?.offDownloadMediaEntityStatusChange();
   
       // 注销自定义元素改变的监听。
       this.controller?.offCustomElementsChange();
   
       // 注销设置改变的监听。
       this.controller?.offSettingsChange();
   
       // 注销上报执行动作的监听。
       this.controller?.offReportExecuteAction();
   
       // 注销通知媒体中心拉起指定三方应用界面的信息的监听。
       this.controller?.offExtensionAbilityChange();
     }
   
     /**
      * 销毁控制器。
      */
     public destroyController() {
       console.info(TAG, 'destroyController')
       this.controller?.destroy();
       this.controller = undefined;
       this.currentBundleName = undefined;
     }
   
     /**
      * 反注册模板监听。
      */
     public unregisterAVMusicTemplateListener() {
       try {
         avMusicTemplate.offAVMusicTemplateCreate();
         avMusicTemplate.offAVMusicTemplateDestroy();
       } catch (e) {
         console.error(TAG, `unregisterAVMusicTemplateListener: errCode: ${e?.code}`);
       }
     }
     // ...
   }
   ```
