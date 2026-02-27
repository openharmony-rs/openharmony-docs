# ArkTS卡片玻璃材质适配（仅对系统应用开放）
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

从API version 22开始，Form Kit支持系统应用使用玻璃材质，提升视觉效果，提供高端精致的用户体验。

> **说明：**
>
> - 本特性对产品功耗、性能要求较高，当前仅在部分旗舰机型上支持，不支持机型上调用后不生效。

## 开发步骤
1. [创建ArkTS卡片](arkts-ui-widget-creation.md)

2. 配置`entry/src/main/resources/base/profile/form_config.json`

   - 在form_config.json文件中的`metadata`添加`visualEffectType`配置，`lightAnimationEffect`表示玻璃材质。
   - 为了达到最佳显示效果，建议开启透明卡片配置。需在form_config.json文件中添加`"transparencyEnabled": true`配置。

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

3. 根据沉浸模式开关状态，设置当前的卡片显示模式

   - 卡片提供方导入基础依赖包。在`entry/src/main/ets/entryformability/EntryFormAbility.ets`中添加以下代码:

   ``` TypeScript
   import { formBindingData, FormExtensionAbility, formInfo, formProvider } from '@kit.FormKit';

   import { Want } from '@kit.AbilityKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';

   const TAG: string = 'EntryFormAbility';
   const DOMAIN_NUMBER: number = 0xFF00;
   ```

   - 卡片提供方在[onAddForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonaddform)回调中，传递`visualEffectType`配置。

   ``` TypeScript
   onAddForm(want: Want) {
     // Called to return a FormBindingData object.
     let formData: Record<string, Object> = {};
     let wantParams = want.parameters;
     formData.visualEffectType = String(wantParams?.visualEffectType || 'none');
     return formBindingData.createFormBindingData(formData);
   }
   ```

   - 卡片提供方在[onUpdateForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform)回调中，更新`visualEffectType`配置。

   ``` TypeScript
   onUpdateForm(formId: string, wantParams?: Record<string, Object>) {
     // Called to notify the form provider to update a specified form.
     let style: Record<string, Object> = {};
     if (wantParams?.visualEffectType) {
       style.visualEffectType = wantParams?.visualEffectType;
       let formData: formBindingData.FormBindingData = formBindingData.createFormBindingData(style);
       formProvider.updateForm(formId, formData).then(() => {
         hilog.info(DOMAIN_NUMBER, TAG, `onUpdateForm style execute success:${formId}`);
       }).catch((err: BusinessError) => {
         hilog.error(DOMAIN_NUMBER, TAG, `onUpdateForm style execute failed:${formId} code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message})`);
       });
     }
   }
   ```

4. 完整卡片代码实现

   > **说明：**
   >
   > - 这里需要注意使用系统应用证书进行签名打包。

   `entry/src/main/ets/widget/pages/WidgetCard.ets`完整代码。

   ``` TypeScript
   import { HdsSceneController, HdsSceneType, HdsVisualComponent, HdsVisualComponentAttribute } from '@kit.UIDesignKit';

   let storage: LocalStorage = new LocalStorage();

   @Entry (storage)
   @Component
   struct WidgetCard {
     readonly TAG: string = 'WidgetCard';
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
     @State color: ResourceColor = Color.White; // 要指定R通道
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
     // 视效参数
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

     // 处理模式
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

### 运行结果
![WidgetvisualEffect](figures/WidgetVisualEffect.gif)