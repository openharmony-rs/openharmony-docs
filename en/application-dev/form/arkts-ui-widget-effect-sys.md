# New Material Adaptation for ArkTS Widgets (for System Applications Only)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

Starting from API version 23, Form Kit allows system apps to use new materials that deliver iridescent and transparent visual effects, enhancing user experience.

> **NOTE**
>
> This feature has high requirements for product power consumption and performance, and is currently only supported on certain flagship models.

## New Material Content
This feature takes effect only on ArkTS widgets. To achieve the optimal display effect, you are advised to use this feature on transparent widgets (widgets with `transparencyEnabled` set to `true`).

### How to Develop
1. [Create an ArkTS widget](arkts-ui-widget-creation.md).
2. Configure the `entry/src/main/resources/base/profile/form_config.json` file. Add `visualEffectType` to `metadata` in the **form_config.json** file. `immersiveMaterial` indicates the new material.

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
             "value": "immersiveMaterial"
           }
         ],
         "supportDimensions": [
           "2*4"
         ]
       }
     ]
   }
   ```

3. Implement the complete code.

   > **NOTE**
   >
   > - The package must be signed with a system application certificate.

   Complete code of `entry/src/main/ets/widget/pages/WidgetCard.ets`:

   ``` TypeScript
   import  {hdsMaterial}  from '@hms.hds.hdsMaterial';

   @Entry
   @ComponentV2
   struct WidgetCard {
     build() {
       Stack() {
         Column() {
           // Call via scenario enumeration.
           Button('hdsMaterial button', {buttonStyle: ButtonStyleMode.NORMAL})
             .width(300)
             .height(80)
             .systemMaterial(new hdsMaterial.Material({
               backgroundMaterial: {
                 type: hdsMaterial.MaterialType.IMMERSIVE,   // Material type: immersive material
                 scenario: hdsMaterial.ScenarioType.GENERAL, // Scenario type: general scenario
                 level: hdsMaterial.MaterialLevel.ADAPTIVE   // Material level: adaptive level
               }
             }))
             .margin({top: 10})
         }
         .height('100%')
         .width('100%')
       }
     }
   }
   ```

## New Material Background
This feature takes effect only on the background of ArkTS widgets.

### Constraints
The new material background does not take effect on a transparent widget (widget with `transparencyEnabled` set to `true`).

### How to Develop
1. [Create an ArkTS widget](arkts-ui-widget-creation.md).
2. Configure the <idp:inline displayname="code" id="code145701445164313">entry/src/main/resources/base/profile/form_config.json</idp:inline> file. Add the `name` field (`materialBackground`) to the `metadata` configuration item in the **form_config.json** file. A `value` of `true` enables the new material background, while `false` (default value) disables it.

   ```json
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
         "defaultDimension": "2*2",
         "supportDimensions": [
           "2*2"
         ],
         "metadata": [
           {
             "name": "materialBackground",
             "value": "true"
           }
         ]
       }
     ]
   }
   ```
3. Adapt the `entry/src/main/ets/entryformability/EntryFormAbility.ets` file. After the new material background is configured, the [onAddForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonaddform) and [onUpdateform](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform) APIs will contain the `ohos.extra.param.key.form_enable_material_background` field. This field needs to be passed to the widget page to determine whether to set the widget background color.
   ```TypeScript
   import { formBindingData, FormExtensionAbility, formInfo, formProvider } from '@kit.FormKit';
   import { Want } from '@kit.AbilityKit';
   
   export default class EntryFormAbility extends FormExtensionAbility {
     onAddForm(want: Want) {
       console.info('enter onAddForm.')
       let param: Record<string, boolean> = {};
       if (want?.parameters?.['ohos.extra.param.key.form_enable_material_background'] !== undefined) {
         // Set the background to be transparent or restore the default color.
         param['isEnableMaterial'] =
           Boolean(want.parameters['ohos.extra.param.key.form_enable_material_background']);
       }
       return formBindingData.createFormBindingData(param);
     }
   
     onUpdateForm(formId: string, wantParams?: Record<string, Object>) {
       let param: Record<string, boolean> = {};
       if (wantParams?.['ohos.extra.param.key.form_enable_material_background'] !== undefined) {
         // Set the background to be transparent or restore the default color.
         param['isEnableMaterial'] = Boolean(wantParams['ohos.extra.param.key.form_enable_material_background']);
       }
       let formInfo: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
       formProvider.updateForm(formId, formInfo).then(() => {
         console.info(`onUpdateForm formId: ${formId}`);
       }).catch((error: BusinessError) => {
         console.error(`onUpdateForm failed, formId: ${formId}, code:${error.code}, message:${error.message}`);
       });
     }
   
     onFormEvent(formId: string, message: string) {
   
     }
   
     onRemoveForm(formId: string) {
   
     }
   
     onAcquireFormState(want: Want) {
       return formInfo.FormState.READY;
     }
   }
   ```
4. Adapt the `entry/src/main/ets/widget/pages/WidgetCard.ets` file.
   ```TypeScript
   @Entry
   @Component
   struct WidgetCard {
     readonly title: string = 'Hello World';
     readonly actionType: string = 'router';
     readonly abilityName: string = 'EntryAbility';
     readonly message: string = 'add detail';
     readonly fullWidthPercent: string = '100%';
     readonly fullHeightPercent: string = '100%';
     @LocalStorageProp('isEnableMaterial') isEnableMaterial: boolean = false;
   
     build() {
       Row() {
         Column() {
           Text(this.title)
             .fontSize($r('app.float.font_size'))
             .fontWeight(FontWeight.Medium)
             .fontColor($r('sys.color.font'))
         }
         .width(this.fullWidthPercent)
       }
       .height(this.fullHeightPercent)
       // The value true of this.isEnableMaterialBgr means enabling the new material background, while false means using the default background color.
       .backgroundColor(this.isEnableMaterial ? Color.Transparent : $r('sys.color.comp_background_primary'))
       .onClick(() => {
         postCardAction(this, {
           action: this.actionType,
           abilityName: this.abilityName,
           params: {
             message: this.message
           }
         });
       })
     }
   }
   ```
