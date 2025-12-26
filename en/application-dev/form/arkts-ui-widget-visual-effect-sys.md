# Blur Effect and Glass Material Adaptation for ArkTS Widgets (for System Applications Only)
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

   - Add the `visualEffectType` configuration to `metadata` in the **form_config.json** file. `blurEffect` represents the blur effect and `lightAnimationEffect` indicates the glass material effect.
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
             "value": "blurEffect,lightAnimationEffect"
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
         hilog.warn(DOMAIN_NUMBER, TAG, `onUpdateForm style execute successed:${formId}`);
       }).catch((err: BusinessError) => {
         hilog.error(DOMAIN_NUMBER, TAG, `onUpdateForm style execute failed:${formId}`, err);
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
   import { uiEffect } from '@kit.ArkGraphics2D';

   let storage: LocalStorage = new LocalStorage();

   @Entry (storage)
   @Component
   struct WidgetCard {
     readonly TAG: string = 'WidgetCard'
     @LocalStorageProp('formId') formId: string = '';
     @LocalStorageProp('visualEffectType') @Watch('dataChange') visualEffectType: string = '';
     @State isBlurStyle: boolean = this.visualEffectType === 'blurEffect';
     @State isHarmoniumStyle: boolean = this.visualEffectType === 'lightAnimationEffect';
     @State whiteEffect: uiEffect.VisualEffect | undefined = undefined;

     @State sceneController: HdsSceneController = new HdsSceneController();
     @State sigma: number = 5;
     @State message: string = "Hello World";
     @State fontSize: number = 200;
     @State minFontSize: number = 20;
     @State maxFontSize: number = 100;
     @State mirrorFontFamily: string = 'Arial, HarmonyOS Sans';
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

       this.whiteEffect = uiEffect.createEffect();
       let whiteBlender: uiEffect.BrightnessBlender = uiEffect.createBrightnessBlender({
         cubicRate: 0,
         quadraticRate: 0,
         linearRate: 0.415,
         degree: 195.95 / 255,
         saturation: 1.7,
         positiveCoefficient: [1, 2, 0.4],
         negativeCoefficient: [3, 4, 3],
         fraction: 0
       })
       this.whiteEffect.backgroundColorBlender(whiteBlender);
     }

     build() {
       Column() {
         if (this.isBlurStyle) {
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
             this.effectRender(this)
           }
           .blendMode(BlendMode.SRC_OVER, BlendApplyType.OFFSCREEN)
           .height('100%')
           .width('100%')
         }

         if (this.isHarmoniumStyle) {
           Column() {
             Row(){
               Stack().useEffect(true)
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
                 this.sceneController, () => {console.log('callback...');})
             }
           }
         }
       }
     }

     @Builder
     effectRender($$: WidgetCard) {
       // Blur layer.
       Column() {}
       .zIndex(1001)
       .useEffect(true)
       .width('100%')
       .height('100%')
       .enabled(false)
       .blendMode(BlendMode.SRC_IN)
       .accessibilityLevel('no')

       // Highlight layer.
       Column() {}
       .zIndex(1002)
       .width('100%')
       .height('100%')
       .backgroundColor(Color.Black)
       .enabled(false)
       .visualEffect($$?.whiteEffect)
       .accessibilityLevel('no')
     }

     // Handle property changes.
     dataChange(propName: string) {
       switch (propName) {
         case 'visualEffectType':
           {
             console.warn(this.TAG,
               `visualEffectType changed with form=${this.formId},visualEffectType=${this.visualEffectType}`);
             this.isBlurStyle = this.visualEffectType === 'blurEffect';
             this.isHarmoniumStyle = this.visualEffectType === 'lightAnimationEffect';
             break;
           }
         default:
           console.info(this.TAG, `${propName} changed with form=${this.formId}.`);
           break;
       }
     }
   }
   ```
