# Glass Material Adaptation for ArkTS Widgets (for System Applications Only)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

Starting from API version 22, Form Kit supports the glass material effect for system applications, which enhances visual presentation and delivers a premium and refined user experience.

> **NOTE**
>
> - This feature requires high power and performance, and is only supported on some flagship models.

## How to Develop
1. [Create an ArkTS widget](arkts-ui-widget-creation.md).

2. Configure **form_config.json**.

   - Add the `visualEffectType` configuration to `metadata` in the **form_config.json** file. `lightAnimationEffect` indicates the glass material.
   - To achieve the optimal display effect, you are advised to enable widget transparency by adding `"transparencyEnabled": true` to the **form_config.json** file.

   ``` json
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
         "isDynamic": true,
         "isDefault": true,
         "updateEnabled": false,
         "scheduledUpdateTime": "10:30",
         "updateDuration": 1,
         "defaultDimension": "2*4",
         "transparencyEnabled": true,
         "metadata": [
           {
             "name": "visualEffectType",
             "value": "lightAnimationEffect"
           }
         ],
         "supportDimensions": [
           "2*4"
         ]
       }
     ]
   }
   ```

3. Set the current widget display mode based on the immersive mode switch status.

   - The widget provider imports the basic dependency package. Add the following code to `EntryFormAbility.ets`:

   ``` TypeScript
   import { formBindingData, FormExtensionAbility, formInfo, formProvider } from '@kit.FormKit';

   import { Want } from '@kit.AbilityKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';

   const TAG: string = 'EntryFormAbility';
   const DOMAIN_NUMBER: number = 0xFF00;
   ```

   - The widget provider transfers the `visualEffectType` configuration in the [onAddForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonaddform) callback.

   ``` TypeScript
   onAddForm(want: Want) {
     // Called to return a FormBindingData object.
     let formData: Record<string, Object> = {};
     let wantParams = want.parameters;
     formData.visualEffectType = String(wantParams?.visualEffectType || 'none');
     return formBindingData.createFormBindingData(formData);
   }
   ```

   - The widget provider updates the `visualEffectType` configuration in the [onUpdateForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform) callback.

   ``` TypeScript
   onUpdateForm(formId: string, wantParams?: Record<string, Object>) {
     // Called to notify the form provider to update a specified form.
     let style: Record<string, Object> = {};
     if (wantParams?.visualEffectType) {
       style.visualEffectType = wantParams?.visualEffectType;
       let formData: formBindingData.FormBindingData = formBindingData.createFormBindingData(style);
       formProvider.updateForm(formId, formData).then(() => {
         hilog.info(DOMAIN_NUMBER, TAG, `onUpdateForm style execute successed:${formId}`);
       }).catch((err: BusinessError) => {
         hilog.error(DOMAIN_NUMBER, TAG, `onUpdateForm style execute failed:${formId} code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message})`);
       });
     }
   }
   ```

4. Implement the complete code.

   > **NOTE**
   >
   > - The package must be signed with a system application certificate.

   ``` TypeScript
   import { HdsSceneController, HdsSceneType, HdsVisualComponent, HdsVisualComponentAttribute } from '@kit.UIDesignKit';

   let storage: LocalStorage = new LocalStorage();

   @Entry (storage)
   @Component
   struct WidgetCard {
     readonly TAG: string = 'WidgetCard'
     @LocalStorageProp('formId') formId: string = '';
     @LocalStorageProp('visualEffectType') @Watch('dataChange') visualEffectType: string = '';
     @State isHarmoniumStyle: boolean = this.visualEffectType === 'lightAnimationEffect';

     @State sceneController: HdsSceneController = new HdsSceneController();
     @State sigma: number = 5;
     @State message: string = "Hello World";
     @State fontSize: number = 200;
     @State minFontSize: number = 20;
     @State maxFontSize: number = 100;
     @State mirrorFontFamily: string = 'Arial, Noto Sans Regular';
     @State fontWeight: FontWeight = FontWeight.Regular;
     @State color: ResourceColor = Color.White; // Specify the R channel.
     @State maxLines: number = 1;
     @State fontFeature: string = '\"ss10\" on';
     @State maskProgress: number = 0;
     @State distortFactor: number = 0;
     @State rate: number = 0.156;
     @State lightUpDegree: number = 0.5035;
     @State cubicCoeff: number = -0.5076;
     @State quadCoeff: number = 1;
     @State saturation: number = 1.22;
     @State posRGB: number[] = [0.47, 1, 0.21];
     @State negRGB: number[] = [1, 1, 0.8];
     @State fraction: number = 0.75;
     // Visual effect parameters.
     @State params: Map<string, Object> = new Map<string, Object>([
       ['sigma', this.sigma],
       ['content', this.message],
       ['fontSize', this.fontSize],
       ['maxFontSize', this.maxFontSize],
       ['minFontSize', this.minFontSize],
       ['fontFamily', this.mirrorFontFamily],
       ['fontWeight', this.fontWeight],
       ['fontColor', this.color],
       ['fontFeature', this.fontFeature],
       ['maxLines', this.maxLines],
       ['maskProgress', this.maskProgress],
       ['distortFactor', this.distortFactor],
       ['rate', this.rate],
       ['lightUpDegree', this.lightUpDegree],
       ['cubicCoeff', this.cubicCoeff],
       ['quadCoeff', this.quadCoeff],
       ['saturation', this.saturation],
       ['posRGB', this.posRGB],
       ['negRGB', this.negRGB],
       ['fraction', this.fraction],
     ]);

     aboutToAppear(): void {
       this.sceneController.setSceneParams(this.params, false);
     }

     build() {
       Column() {
         if (this.isHarmoniumStyle) {
           Column() {
             Row() {
               HdsVisualComponent() {
                 Text(this.message)
                   .fontColor(this.color)
                   .fontFamily(this.mirrorFontFamily)
                   .fontSize(this.fontSize)
                   .minFontSize(this.minFontSize)
                   .maxFontSize(this.maxFontSize)
                   .fontWeight(this.fontWeight)
                   .fontFeature(this.fontFeature)
                   .maxLines(this.maxLines)
                   .id(`WidgetCard_1`)
                   .fontFeature('\"ss10\" on')
                   .accessibilityLevel('no')
                   .visibility(Visibility.Hidden)
               }
               .scene(HdsSceneType.HARMONIUM_MATERIAL_FONT_SCENE,
                 this.sceneController, () => {console.info('callback...');})
             }
           }
         } else {
           Stack() {
             Column() {
               Text(this.message)
                 .fontColor(this.color)
                 .fontFamily(this.mirrorFontFamily)
                 .fontSize(this.fontSize)
                 .minFontSize(this.minFontSize)
                 .maxFontSize(this.maxFontSize)
                 .fontWeight(this.fontWeight)
                 .fontFeature(this.fontFeature)
                 .maxLines(this.maxLines)
                 .id(`WidgetCard_1`)
                 .fontFeature('\"ss10\" on')
                 .accessibilityLevel('no')
             }
           }
           .height('100%')
           .width('100%')
         }
       }
     }

     // Handle property changes.
     dataChange(propName: string) {
       switch (propName) {
         case 'visualEffectType':
           {
             console.info(this.TAG,
               `visualEffectType changed with form=${this.formId},visualEffectType=${this.visualEffectType}`);
             this.isHarmoniumStyle = this.visualEffectType === 'lightAnimationEffect';
             this.sceneController.setSceneParams(this.params, false);
             break;
           }
         default:
           console.info(this.TAG, `${propName} changed with form=${this.formId}.`);
           break;
       }
     }
   }
   ```
