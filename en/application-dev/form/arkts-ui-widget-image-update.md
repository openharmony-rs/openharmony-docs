# Updating Local and Online Images in the Widget
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

Typically, a widget includes local images or online images downloaded from the network. To obtain local and online images, use the FormExtensionAbility. The following exemplifies how to show local and online images on a widget.


1. For the widget to download online images, declare the **ohos.permission.INTERNET** permission for the widget. For details, see [Declaring Permissions](../security/AccessToken/declare-permissions.md).

2. Import related modules to the **WgtImgUpdateEntryFormAbility.ts** file.

    <!-- @[refresh_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/wgtimgupdateentryformability/WgtImgUpdateEntryFormAbility.ts) --> 
    
    ``` TypeScript
    // entry/src/main/ets/wgtimgupdateentryformability/WgtImgUpdateEntryFormAbility.ts
    import { Want } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { fileIo } from '@kit.CoreFileKit';
    import { formBindingData, FormExtensionAbility, formInfo, formProvider } from '@kit.FormKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { http } from '@kit.NetworkKit';
    ```

3. Update local files in the **onAddForm** lifecycle callback of the EntryFormAbility.

    <!-- @[local_file_refresh](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/wgtimgupdateentryformability/WgtImgUpdateEntryFormAbility.ts) --> 
    
    ``` TypeScript
    // entry/src/main/ets/wgtimgupdateentryformability/WgtImgUpdateEntryFormAbility.ts
    const TAG: string = 'WgtImgUpdateEntryFormAbility';
    const DOMAIN_NUMBER: number = 0xFF00;
    // ...
    
    export default class WgtImgUpdateEntryFormAbility extends FormExtensionAbility {
      // When the widget is added, a local image is opened and transferred to the widget page for display.
      onAddForm(want: Want): formBindingData.FormBindingData {
        // Assume that the local image head.PNG is in the tmp directory of the current widget.
        let tempDir = this.context.getApplicationContext().tempDir;
        hilog.info(DOMAIN_NUMBER, TAG, `tempDir: ${tempDir}`);
        let imgMap: Record<string, number> = {};
        try {
          // Open a local image and obtain its FD. The FD is released when the FormExtensionAbility process is destroyed.
          let file = fileIo.openSync(tempDir + '/' + 'head.PNG');
          imgMap['imgBear'] = file.fd;
        } catch (e) {
          hilog.error(DOMAIN_NUMBER, TAG, `openSync failed: ${JSON.stringify(e as BusinessError)}`);
        }
    
        class FormDataClass {
          text: string = 'Image: Bear';
          loaded: boolean = true;
          // If an image needs to be displayed in the widget, the value of imgName must be the same as the key 'imgBear' in formImages.
          imgName: string = 'imgBear';
          // If an image needs to be displayed in the widget, the formImages field is mandatory (formImages cannot be left blank or renamed), and 'imgBear' corresponds to the FD.
          formImages: Record<string, number> = imgMap;
        }
    
        let formData = new FormDataClass();
        // Encapsulate the FD in formData and return it to the widget page.
        return formBindingData.createFormBindingData(formData);
      }
    
      // ...
    }
    ```

4. Update online files in the **onFormEvent** lifecycle callback of the EntryFormAbility.

    <!-- @[network_file_refresh](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/wgtimgupdateentryformability/WgtImgUpdateEntryFormAbility.ts) --> 
    
    ``` TypeScript
    // entry/src/main/ets/wgtimgupdateentryformability/WgtImgUpdateEntryFormAbility.ts
    const TAG: string = 'WgtImgUpdateEntryFormAbility';
    const DOMAIN_NUMBER: number = 0xFF00;
    const TEXT1: string = 'Updating...'
    const TEXT2: string = 'Update failed'
    
    
    export default class WgtImgUpdateEntryFormAbility extends FormExtensionAbility {
      // ...
      async onFormEvent(formId: string, message: string): Promise<void> {
        let param: Record<string, string> = {
          'text': TEXT1
        };
        let formInfo: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
        formProvider.updateForm(formId, formInfo);
    
        // Note: After being started with the triggering of the lifecycle callback, the FormExtensionAbility can run in the background for only 5 seconds.
        // When possible, limit the size of the image to download. If an image cannot be downloaded within 5 seconds, it will not be updated to the widget page.
        let netFile =
          'https://cn-assets.gitee.com/assets/mini_app-e5eee5a21c552b69ae6bf2cf87406b59.jpg';
        // Specify the URL of the image to download.
        let tempDir = this.context.getApplicationContext().tempDir;
        let fileName = 'file' + Date.now();
        let tmpFile = tempDir + '/' + fileName;
        let imgMap: Record<string, number> = {};
    
        class FormDataClass {
          text: string = 'Image: Bear' + fileName;
          loaded: boolean = true;
          // If an image needs to be displayed in the widget, the value of imgName must be the same as the key fileName in formImages.
          imgName: string = fileName;
          // If an image needs to be displayed in the widget, the formImages field is mandatory (formImages cannot be left blank or renamed), and fileName corresponds to the FD.
          formImages: Record<string, number> = imgMap;
        }
    
        let httpRequest = http.createHttp()
        let data = await httpRequest.request(netFile);
        if (data?.responseCode == http.ResponseCode.OK) {
          try {
            let imgFile = fileIo.openSync(tmpFile, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
            imgMap[fileName] = imgFile.fd;
            try {
              let writeLen: number = await fileIo.write(imgFile.fd, data.result as ArrayBuffer);
              hilog.info(DOMAIN_NUMBER, TAG, "write data to file succeed and size is:" + writeLen);
              hilog.info(DOMAIN_NUMBER, TAG, 'ArkTSCard download complete: %{public}s', tmpFile);
              try {
                let formData = new FormDataClass();
                let formInfo = formBindingData.createFormBindingData(formData);
                await formProvider.updateForm(formId, formInfo);
                hilog.info(DOMAIN_NUMBER, TAG, '%{public}s', 'FormAbility updateForm success.');
              } catch (error) {
                hilog.error(DOMAIN_NUMBER, TAG, `FormAbility updateForm failed: ${JSON.stringify(error)}`);
              }
            } catch (err) {
              hilog.error(DOMAIN_NUMBER, TAG,
                "write data to file failed with error message: " + err.message + ", error code: " + err.code);
            } finally {
              fileIo.closeSync(imgFile);
            }
          } catch (e) {
            hilog.error(DOMAIN_NUMBER, TAG, `openSync failed: ${JSON.stringify(e as BusinessError)}`);
          }
    
        } else {
          hilog.error(DOMAIN_NUMBER, TAG, `ArkTSCard download task failed`);
          let param: Record<string, string> = {
            'text': TEXT2
          };
          let formInfo: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
          formProvider.updateForm(formId, formInfo);
        }
        httpRequest.destroy();
      }
    
      onAcquireFormState(want: Want): formInfo.FormState {
        // Called when the widget host queries the widget state. The initial state is returned by default.
        return formInfo.FormState.READY;
      }
    
    }
    
    ```

5. On the widget page, use the **backgroundImage** attribute to display the widget content passed from the EntryFormAbility.

    <!-- @[widget_image_update_card](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/widgetimageupdate/pages/WidgetImageUpdateCard.ets) --> 
    
    ``` TypeScript
    // entry/src/main/ets/widgetimageupdate/pages/WidgetImageUpdateCard.ets
    let storageWidgetImageUpdate = new LocalStorage();
    
    @Entry(storageWidgetImageUpdate)
    @Component
    struct WidgetImageUpdateCard {
      // Replace $r('app.string.loading') with the resource file you use.
      @LocalStorageProp('text') text: ResourceStr = $r('app.string.loading');
      @LocalStorageProp('loaded') loaded: boolean = false;
      // Replace $r('app.string.imgName') with the resource file you use.
      @LocalStorageProp('imgName') imgName: ResourceStr = $r('app.string.imgName');
    
      build() {
        Column() {
          Column() {
            Text(this.text)
              .fontColor('#FFFFFF')
              .opacity(0.9)
              .fontSize(12)
              .textOverflow({ overflow: TextOverflow.Ellipsis })
              .maxLines(1)
              .margin({ top: '8%', left: '10%' })
          }.width('100%').height('50%')
          .alignItems(HorizontalAlign.Start)
    
          Row() {
            Button() {
              // Replace $r('app.string.update') with the resource file you use.
              Text($r('app.string.update'))
                .fontColor('#45A6F4')
                .fontSize(12)
            }
            .width(120)
            .height(32)
            .margin({ top: '30%', bottom: '10%' })
            .backgroundColor('#FFFFFF')
            .borderRadius(16)
            .onClick(() => {
              postCardAction(this, {
                action: 'message',
                params: {
                  info: 'refreshImage'
                }
              });
            })
          }.width('100%').height('40%')
          .justifyContent(FlexAlign.Center)
        }
        .width('100%').height('100%')
        // Replace $r('app.media.ImageDisp') with the resource file you use.
        .backgroundImage(this.loaded ? 'memory://' + this.imgName : $r('app.media.ImageDisp'))
        .backgroundImageSize(ImageSize.Cover)
      }
    }
    ```

> **NOTE**
>
> - The **Image** component displays images in the remote memory based on the (**memory://**) identifier in the input parameter (**memory://fileName**). The value of **fileName** must be consistent with the key in the object (**'formImages': {key: fd}**) passed by the EntryFormAbility.
>
> - The **Image** component determines whether to update the image by comparing the values of **imgName** consecutively passed by the EntryFormAbility. It updates the image only when the values are different.
