# Overview of ArkTS Widget Editing
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->

ArkTS widgets provide widget page editing capabilities, allowing users to customize widget content. For example, users can edit a contact widget, modify the contact displayed in a widget, or edit a weather widget.

Widget page editing supports two modes: semi-modal widget editing and full-screen widget editing. Semi-modal widget editing is supported since API version 18.

## Semi-Modal Widget Editing

The following example describes how to use semi-modal widget editing.

### How It Works

![WidgetProject](figures/semi-modal-edit-page-process.png)

1. The user long-presses the widget to open the menu. At this point, the home screen determines whether to display the edit button based on the [formConfigAbility](./arkts-ui-widget-configuration.md#fields-in-configuration-file) field, which indicates whether the widget supports widget editing.
2. The user taps the **Edit** menu item. The home screen starts the corresponding page based on the field in `formConfigAbility` and opens the level-1 edit page. The level-1 edit page has limited editing space and is suitable for simple editing layouts.
   - Preview area: The gray area is the preview area, which displays the widget after editing. The layout of the preview area is determined by the home screen.
   - Edit area: The white area is the edit area, which is a custom layout area provided by the application to implement the widget editing layout. The widget edit area is drawn by the application after it inherits [FormEditExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formEditExtensionAbility.md), and is suitable for simple editing layouts.
   - **FormEditDemo**: This field indicates the application name of the widget host application. It is configured through the `label` field in the [app.json5](../quick-start/app-configuration-file.md#tags-in-the-configuration-file) configuration file.
   - **widget**: This field indicates the widget name. It is configured through the [name](./arkts-ui-widget-configuration.md#fields-in-configuration-file) field in the widget `form_config.json` configuration file.
   - **Done** button: After editing is complete, the user can tap this button to exit the semi-modal widget editing page.
3. In the widget edit area, after the user taps **Switch to: Shanghai**, the widget provider can update widget information by using [updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform), and the updated widget is displayed in the preview area.
4. In the widget edit area, after the user taps **Open level-2 edit page**, the widget uses the [startSecondPage](../reference/apis-form-kit/js-apis-inner-application-formEditExtensionContext.md#startsecondpage) method provided by **FormEditExtensionContext** to pass the level-2 edit page information of the widget provider to the home screen. The home screen then starts the corresponding page, that is, the level-2 edit page. The level-2 edit page is mainly used to implement complex editing layouts. You can decide whether to add a level-2 edit page based on service requirements.
5. After editing is complete, the user exits the edit page.

### How to Develop

1. [Create a widget](./arkts-ui-widget-creation.md).

2. Add the `EntryFormEditAbility` file to implement the semi-modal editing component of [FormEditExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formEditExtensionAbility.md), and configure the [formConfigAbility](./arkts-ui-widget-configuration.md#fields-in-configuration-file) field in the `form_config.json` file.
   - Implement the Ability for the semi-modal level-1 edit page.
   <!-- @[FormEditDemo_EntryFormEditAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditDemo/entry/src/main/ets/entryformeditability/EntryFormEditAbility.ets) -->

   ``` TypeScript
   // entry/src/main/ets/entryformeditability/EntryFormEditAbility.ets
   import { FormEditExtensionAbility } from '@kit.FormKit';
   import { UIExtensionContentSession, Want } from '@kit.AbilityKit';
   import { ExtensionEvent } from '../model/ExtensionEvent';
   
   const TAG: string = 'FormEditDemo[EntryFormEditAbility] -->';
   let storage: LocalStorage = ExtensionEvent.getStorage();
   
   export default class EntryFormEditAbility extends FormEditExtensionAbility {
     onCreate() {
       console.info(`${TAG} onCreate`);
     }
   
     onForeground(): void {
       console.info(`${TAG} EntryFormEditAbility onForeground.....`);
     }
   
     onBackground(): void {
       console.info(`${TAG} EntryFormEditAbility onBackground......`);
     }
   
     onDestroy(): void {
       console.info(`${TAG} EntryFormEditAbility onDestroy......`);
     }
   
     onSessionCreate(want: Want, session: UIExtensionContentSession) {
       // Obtain the ID of the widget being edited and the ID of the preview widget, and synchronize them to the level-1 edit page through storage.
       const formId: string | undefined = want.parameters?.cardId as string;
       const previewFormId: string | undefined = want.parameters?.previewCardId as string;
   
       if (formId) {
         console.info(`${TAG} form id is ${formId}`);
         storage.setOrCreate('formId', formId);
       }
       if (previewFormId) {
         console.info(`${TAG} preview form id is ${previewFormId}`);
         storage.setOrCreate('previewFormId', previewFormId);
       }
       let extensionEvent: ExtensionEvent = new ExtensionEvent();
       extensionEvent.setStartSecondPage((): void => this.startSecondPage());
       storage.setOrCreate('extensionEvent', extensionEvent);
       storage.setOrCreate('context', this.context);
       try {
         // Start the level-1 edit page.
         session.loadContent('pages/FormEditExtension', storage);
       } catch (e) {
         console.error(`${TAG} EntryFormEditAbility loadContent err, Code: ${e.code}, Message: ${e.message}`);
       }
     }
   
     onSessionDestroy(session: UIExtensionContentSession) {
       console.info(`${TAG} onSessionDestroy`);
     }
   
     private startSecondPage() {
       const bundleName: string = this.context.extensionAbilityInfo.bundleName;
       const secPageAbilityName: string = 'FormEditSecPageAbility';
       console.info(`${TAG} startSecondPage. bundleName: ${bundleName}, secPageAbilityName: ${secPageAbilityName}.`);
       try {
         // Start the level-2 edit page.
         this.context.startSecondPage({
           bundleName: bundleName,
           parameters: {
             'secPageAbilityName': secPageAbilityName
           }
         });
         console.info(`${TAG} startSecondPage success!`);
       } catch (err) {
         console.error(`${TAG} startSecondPage failed, Code: ${err.code}, Message: ${err.message}`);
       }
     }
   };
   ```

   - Implement the Ability for the semi-modal level-2 edit page.
   <!-- @[FormEditDemo_FormEditSecPageAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditDemo/entry/src/main/ets/entryformeditability/FormEditSecPageAbility.ets) -->

   ``` TypeScript
   // entry/src/main/ets/entryformeditability/FormEditSecPageAbility.ets
   import { FormEditExtensionAbility } from '@kit.FormKit';
   import { UIExtensionContentSession, Want } from '@kit.AbilityKit';
   import { ExtensionEvent } from '../model/ExtensionEvent';
   
   const TAG = 'FormEditExtensionAbility';
   
   export default class FormEditSecPageAbility extends FormEditExtensionAbility {
     public storage: LocalStorage = new LocalStorage();
   
     onCreate() {
       console.info(TAG, `Ability onCreate`);
     }
   
     onForeground(): void {
       console.info(TAG, `Ability onForeground`);
     }
   
     onBackground(): void {
       console.info(TAG, `Ability onBackground`);
     }
   
     onDestroy(): void {
       console.info(TAG, `Ability onDestroy`);
     }
   
     onSessionCreate(want: Want, session: UIExtensionContentSession) {
       let extensionEvent: ExtensionEvent = new ExtensionEvent();
       this.storage.setOrCreate('extensionEvent', extensionEvent);
       this.storage.setOrCreate('session', session);
   
       try {
         session.loadContent('pages/FormEditSecPage', this.storage);
         console.info(TAG, `loadContent first edit page success`);
       } catch (e) {
         console.error(TAG, `EntryFormEditAbility loadContent err, want: ${e?.message}`);
       }
     }
   
     onSessionDestroy(session: UIExtensionContentSession) {
       console.info(TAG, `onSessionDestroy`);
     }
   }
   ```

   - Configure the new `EntryFormEditAbility` in `module.json5` as follows.

   ```json5
   // entry/src/main/module.json5
   {
       "module": {
           // ...
           "extensionAbilities": [
               {
                   // Level-1 edit page.
                   "name": "EntryFormEditAbility",
                   "srcEntry": "./ets/entryformeditability/EntryFormEditAbility.ets",
                   "type": "formEdit"
               },
               {
                   // Level-2 edit page.
                   "name": "FormEditSecPageAbility",
                   "srcEntry": "./ets/entryformeditability/FormEditSecPageAbility.ets",
                   "type": "formEdit"
               }
           ]
       }
   }
   ```

   - Implement the widget `form_config.json` file.

   ```json5
   // entry/src/main/resources/base/profile/form_config.json
   {
       "forms": [
           {
               "name": "widget",
               "displayName": "$string:widget_display_name",
               "description": "$string:widget_desc",
               "src": "./ets/widget/pages/WidgetCard.ets",
               "uiSyntax": "arkts",
               "formConfigAbility": "ability://EntryFormEditAbility",
               "isDynamic": true,
               "isDefault": true,
               "updateEnabled": false,
               "scheduledUpdateTime": "10:30",
               "multiScheduledUpdateTime": "11:30,16:30",
               "updateDuration": 1,
               "defaultDimension": "1*2",
               "supportDimensions": [
                   "1*2",
                   "2*2",
                   "2*4",
                   "4*4",
                   "6*4"
               ]
           }
       ]
   }
   ```

3. Implement the level-1 edit page layout. Use [updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform) to refresh information about the widget being edited and the preview widget, and use [startSecondPage](../reference/apis-form-kit/js-apis-inner-application-formEditExtensionContext.md#startsecondpage) to start the level-2 edit page.
   - The level-1 edit page layout is implemented as follows.
   <!-- @[FormEditDemo_FormEditExtension](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditDemo/entry/src/main/ets/pages/FormEditExtension.ets) -->

   ``` TypeScript
   // entry/src/main/ets/pages/FormEditExtension.ets
   import { common, UIExtensionContentSession } from '@kit.AbilityKit';
   import { preferences } from '@kit.ArkData';
   import { formBindingData, formProvider } from '@kit.FormKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { ExtensionEvent } from '../model/ExtensionEvent';
   import { PreferencesUtil } from '../common/PreferencesUtil';
   import { FormData } from '../common/CommonData';
   
   const TAG: string = 'FormEditDemo[Extension] -->';
   let storage: LocalStorage = ExtensionEvent.getStorage();
   
   @Entry(storage)
   @Component
   struct FormEditExtension {
     @State message1: string = 'Beijing';
     @State message2: string = 'Shanghai';
     private formId: string = storage.get('formId') as string;
     private previewFormId: string = storage.get('previewFormId') as string;
     private session: UIExtensionContentSession =
       storage.get<UIExtensionContentSession>('session') as UIExtensionContentSession;
     private extensionEvent: ExtensionEvent = storage.get<ExtensionEvent>('extensionEvent') as ExtensionEvent;
     // Before API version 22, import LiveFormExtensionContext by using
     // import LiveFormExtensionContext from 'application/LiveFormExtensionContext'.
     // This import is highlighted in red in DevEco Studio, but it does not affect compilation or running.
     // LiveFormExtensionContext can be used directly. Since API version 22, importing LiveFormExtensionContext
     // through import { common } from '@kit.AbilityKit' is supported, and it can be used as common.LiveFormExtensionContext.
     private context: common.FormEditExtensionContext | undefined =
       storage.get<common.FormEditExtensionContext>('context');
   
     updateForm(message: string) {
       if (!this.formId && !this.previewFormId) {
         return;
       }
       if (this.context) {
         let util = PreferencesUtil.getInstance();
         let preferences = util.getPreferences(this.context) as preferences.Preferences;
         util.preferencesPut(preferences, this.formId, new FormData(this.formId, message));
       }
       let param: Record<string, string> = {
         'message': message
       }
       let obj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
       try {
         // Refresh information about the widget being edited.
         formProvider.updateForm(this.formId, obj, (error: BusinessError) => {
           if (error) {
             console.error(TAG, `callback error, code: ${error.code}, message: ${error.message})`);
             return;
           }
           console.info(TAG, `formProvider updateForm success`);
         });
       } catch (error) {
         console.error(TAG, `catch error, Code: ${error.code}, Message: ${error.message}`);
       }
       if (!this.previewFormId) {
         console.error(TAG, 'previewFormId is empty');
         return;
       }
       try {
         // Refresh information about the preview widget.
         formProvider.updateForm(this.previewFormId, obj, (error: BusinessError) => {
           if (error) {
             console.error(TAG, `callback error, code: ${error.code}, message: ${error.message})`);
             return;
           }
           console.info(TAG, `formProvider updateForm success`);
         });
       } catch (error) {
         console.error(TAG, `catch error, Code: ${error.code}, Message: ${error.message}`);
       }
     }
   
     onPageShow() {
       console.info(`${TAG} onPageShow. extensionEvent`);
     }
   
     build() {
       Row() {
         Column() {
           Button($r('app.string.button_one'))
             .width('80%')
             .type(ButtonType.Capsule)
             .margin({
               top: 20
             })
             .onClick(() => {
               console.info(`${TAG} Button1 onClick ${storage.get('message')}`);
               this.updateForm(this.message1);
               storage.setOrCreate('message', this.message1);
             })
           Button($r('app.string.button_two'))
             .width('80%')
             .type(ButtonType.Capsule)
             .margin({
               top: 20
             })
             .onClick(() => {
               console.info(`${TAG} Button2 onClick`);
               this.updateForm(this.message2);
               storage.setOrCreate('message', this.message2);
             })
           Button($r('app.string.button_three'))
             .width('80%')
             .type(ButtonType.Capsule)
             .margin({
               top: 20
             })
             .onClick(async () => {
               console.info(`${TAG} Button onClick`);
               // Start the level-2 edit page.
               this.extensionEvent?.startFormEditSecondPage();
             })
         }
       }
       .justifyContent(FlexAlign.Center)
       .width('100%')
     }
   }
   ```

   - Add the `FormEditSecPage.ets` file to implement the level-2 edit page layout.
   <!-- @[FormEditDemo_FormEditSecPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditDemo/entry/src/main/ets/pages/FormEditSecPage.ets) -->

   ``` TypeScript
   // entry/src/main/ets/pages/FormEditSecPage.ets
   @Entry
   @Component
   struct FormEditSecPage {
     @State message: string | ResourceStr = $r('app.string.button_three');
   
     build() {
       RelativeContainer() {
         Text(this.message)
           .id('HelloWorld')
           .fontSize($r('app.float.page_text_font_size'))
           .fontWeight(FontWeight.Bold)
           .alignRules({
             center: { anchor: '__container__', align: VerticalAlign.Center },
             middle: { anchor: '__container__', align: HorizontalAlign.Center }
           })
           .onClick(() => {
             this.message = 'Welcome';
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```

   - Load the layout files.

       ```json5
       // entry/src/main/resources/base/profile/main_pages.json
       {
           "src": [
               "pages/Index",
               "pages/FormEditExtension",
               "pages/FormEditSecPage"
           ]
       }
       ```

   - Add the `ExtensionEvent` file to encapsulate the [startSecondPage](../reference/apis-form-kit/js-apis-inner-application-formEditExtensionContext.md#startsecondpage) method into `startFormEditSecondPage` for service use.
   <!-- @[FormEditDemo_ExtensionEvent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditDemo/entry/src/main/ets/model/ExtensionEvent.ets) -->

   ``` TypeScript
   // entry/src/main/ets/model/ExtensionEvent.ets
   const TAG: string = 'FormEditDemo[ExtensionEvent] -->';
   const LOCAL: Record<string, string> = { 'formId': '', 'previewFormId': '', 'message': '' };
   
   export class ExtensionEvent {
     private static storage = new LocalStorage(LOCAL);
   
     public static getStorage(): LocalStorage {
       return ExtensionEvent.storage;
     }
   
     public setStartSecondPage(startSecondPage: () => void) {
       console.info(`${TAG} setStartSecondPage`);
       this.startSecondPage = startSecondPage;
     }
   
     public async startFormEditSecondPage() {
       console.info(`${TAG} startFormEditSecondPage call`);
       this.startSecondPage();
     }
   
     private startSecondPage: () => void = (): void => {
       console.info(`${TAG} startSecondPage is empty!`);
     };
   }
   ```

4. Persist widget information. Each time the widget edit page is opened, the preview widget must remain consistent with the widget being edited. Therefore, widget information must be persisted.
   - Add the `PreferencesUtil` file to encapsulate [Preferences](../database/data-persistence-by-preferences.md) for persisting service data.
   <!-- @[FormEditDemo_PreferencesUtil](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditDemo/entry/src/main/ets/common/PreferencesUtil.ets) -->

   ``` TypeScript
   // entry/src/main/ets/common/PreferencesUtil.ets
   import { preferences } from '@kit.ArkData';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { FormData } from './CommonData';
   
   const TAG: string = 'PreferencesUtil';
   const MY_STORE: string = 'myStore';
   
   export class PreferencesUtil {
     private static preferencesUtil: PreferencesUtil;
   
     public static getInstance(): PreferencesUtil {
       if (!PreferencesUtil.preferencesUtil) {
         PreferencesUtil.preferencesUtil = new PreferencesUtil();
       }
       return PreferencesUtil.preferencesUtil;
     }
   
     getPreferences(context: Context): preferences.Preferences | undefined {
       try {
         preferences.removePreferencesFromCacheSync(context, MY_STORE);
         return preferences.getPreferencesSync(context, { name: MY_STORE });
       } catch (error) {
         let err = error as BusinessError;
         console.error(TAG, `getPreferences failed, error code=${err.code}, message=${err.message}`);
         return undefined;
       }
     }
   
     preferencesFlush(preferences: preferences.Preferences) {
       preferences.flush((err) => {
         if (err) {
           console.error(TAG, `Failed to flush. Code:${err.code}, message:${err.message}`);
         }
       })
     }
   
     preferencesPut(preferences: preferences.Preferences, formID: string, value: FormData): void {
       try {
         preferences.putSync(formID, value);
         this.preferencesFlush(preferences);
       } catch (error) {
         let err = error as BusinessError;
         console.error(TAG, `preferencesPut failed, error code=${err.code}, message=${err.message}`);
       }
     }
   
     removePreferencesFromCache(context: Context): void {
       preferences.removePreferencesFromCache(context, MY_STORE).catch((err: BusinessError) => {
         console.error(TAG, `removePreferencesFromCache failed, error code=${err.code}, message=${err.message}`);
       });
     }
   
     getValue(preferences: preferences.Preferences, formID: string): FormData | undefined {
       if (preferences === null) {
         console.error(TAG, `preferences is null`);
         return undefined;
       }
       try {
         return preferences.getSync(formID, new FormData('')) as FormData;
       } catch (error) {
         let err = error as BusinessError;
         console.error(TAG, `getSync failed, error code=${err.code}, message=${err.message}`);
         return undefined;
       }
     }
   
     removeFormId(context: Context, formId: string) {
       try {
         let preferences = this.getPreferences(context);
         if (!preferences) {
           console.error(TAG, `preferences is null`);
           return;
         }
         if (preferences.hasSync(formId)) {
           preferences.deleteSync(formId);
           this.preferencesFlush(preferences);
         }
       } catch (error) {
         console.error(TAG, `Failed to get preferences. Code:${error.code}, message:${error.message}`);
       }
     }
   }
   ```

   - To ensure that the preview widget is synchronized with the widget being edited, when a new widget is created, determine whether the `ohos.extra.param.key.edit_form_id` field in the `onAddForm` callback carries a widget ID. If this field carries a widget ID, the new widget is a preview widget and must obtain the information about the widget being edited from the database.
   <!-- @[FormEditDemo_EntryFormAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditDemo/entry/src/main/ets/entryformability/EntryFormAbility.ets) -->

   ``` TypeScript
   // entry/src/main/ets/entryformability/WidgetCard.ets
   import { formBindingData, FormExtensionAbility, formInfo } from '@kit.FormKit';
   import { Want } from '@kit.AbilityKit';
   import { PreferencesUtil } from '../common/PreferencesUtil';
   import { FormData } from '../common/CommonData';
   
   export default class EntryFormAbility extends FormExtensionAbility {
     onAddForm(want: Want) {
       let editFormId: string = '';
       let formId: string = '';
       // Initialize the Preferences database.
       let util = PreferencesUtil.getInstance();
       let preferences = util.getPreferences(this.context);
       if (want.parameters) {
         formId = want.parameters[formInfo.FormParam.IDENTITY_KEY] as string;
         editFormId = want.parameters['ohos.extra.param.key.edit_form_id'] as string;
       }
       // If the widget is a preview widget on the edit page, update it with the information about the widget being edited when the preview widget is created.
       if (editFormId && preferences) {
         let formData: FormData = util.getValue(preferences, editFormId) as FormData;
         return formBindingData.createFormBindingData({
           'message': formData.text
         });
       }
   
       return formBindingData.createFormBindingData('');
     }
   
     onCastToNormalForm(formId: string) {
     }
   
     onUpdateForm(formId: string) {
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

   - The widget layout file is as follows.
   <!-- @[FormEditDemo_WidgetCard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditDemo/entry/src/main/ets/widget/pages/WidgetCard.ets) -->

   ``` TypeScript
   // entry/src/main/ets/widget/pages/WidgetCard.ets
   let storage: LocalStorage = new LocalStorage();
   
   @Entry(storage)
   @Component
   struct WidgetCard {
     @LocalStorageProp('message') title: string = 'Hello World';
     readonly actionType: string = 'router';
     readonly abilityName: string = 'EntryAbility';
     readonly message: string = 'add detail';
     readonly fullWidthPercent: string = '100%';
     readonly fullHeightPercent: string = '100%';
   
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
       .backgroundColor($r('sys.color.comp_background_primary'))
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

   - Add the `CommonData.ets` file to define the widget data structure.
   <!-- @[FormEditDemo_CommonData](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditDemo/entry/src/main/ets/common/CommonData.ets) -->

   ``` TypeScript
   // entry/src/main/ets/common/CommonData.ets
   export class FormData {
     public formId: string = '';
     public text: string = 'Hello World';
   
     constructor(formId: string, text?: string) {
       this.formId = formId;
       this.text = text ? text : 'Hello World';
     }
   }
   ```

5. The resource file is as follows.

   ```json5
   // entry/src/main/resources/base/element/string.json
   {
      "string": [
         // ...
         {
            "name": "button_one",
            "value": "Switch to: Beijing"
         },
         {
            "name": "button_two",
            "value": "Switch to: Shanghai"
         },
         {
            "name": "button_three",
            "value": "Open level-2 edit page"
         }
      ]
    }
   ```

## Full-Screen Widget Editing

### How It Works

![WidgetProject](figures/full-screen-edit-page-process.png)

1. The user long-presses the widget to open the menu. The home screen determines whether to display the edit button based on the [formConfigAbility](./arkts-ui-widget-configuration.md#fields-in-configuration-file) field, which indicates whether the widget supports widget editing.
2. The user taps the **Edit** menu item to enter the full-screen edit page. The home screen starts the widget edit page based on the information in the `formConfigAbility` field.
3. The user taps **Switch to: Shanghai** to edit the widget content. The provider updates information about the widget being edited by using [updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform).

### How to Develop

The following example shows how to open the edit menu by long-pressing a widget, tap **Edit** to enter the full-screen edit page, and modify widget content.

1. [Create a widget](./arkts-ui-widget-creation.md).

2. Add the `EntryEditAbility.ets` file, inherit from [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md), and implement the [onCreate](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate) and [onNewWant](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onnewwant) callbacks. The widget host passes the ID of the widget being edited through the `parameters` field of [Want](../reference/apis-ability-kit/js-apis-app-ability-want.md). In addition, configure the [formConfigAbility](./arkts-ui-widget-configuration.md#fields-in-configuration-file) field in the `form_config.json` file.
   - Implement the Ability for the edit page.
   <!-- @[FormEditUIAbility_EntryEditAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditUIAbility/entry/src/main/ets/entryability/EntryEditAbility.ets) -->

   ``` TypeScript
   // entry/src/main/ets/entryability/EntryEditAbility.ets
   import { AbilityConstant, ConfigurationConstant, UIAbility, Want } from '@kit.AbilityKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import { window } from '@kit.ArkUI';
   import { PreferencesUtil } from '../common/PreferencesUtil';
   import { preferences } from '@kit.ArkData';
   
   const DOMAIN = 0x0000;
   
   export default class EntryEditAbility extends UIAbility {
     onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
       const formId: string = want.parameters?.formId as string;
       hilog.info(DOMAIN, 'testTag', 'onCreate form id is' + formId)
       if (formId) {
         // Store the ID of the widget being edited for subsequent widget editing.
         let util = PreferencesUtil.getInstance();
         let preferences = util.getPreferences(this.context) as preferences.Preferences;
         util.preferencesPut(preferences, formId);
       }
       try {
         this.context.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
       } catch (err) {
         hilog.error(DOMAIN, 'testTag', 'Failed to set colorMode. Code:${err.code}, message:${err.message}');
       }
       hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onCreate');
     }
   
     onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam) {
       // Refresh the ID of the widget being edited when the edit page is warm-started.
       const formId: string = want.parameters?.formId as string;
       hilog.info(DOMAIN, 'testTag', 'onNewWant form id is' + formId)
       if (formId) {
         // Initialize the Preferences database.
         let util = PreferencesUtil.getInstance();
         let preferences = util.getPreferences(this.context) as preferences.Preferences;
         util.preferencesPut(preferences, formId);
       }
     }
   
     onDestroy(): void {
       hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onDestroy');
     }
   
     onWindowStageCreate(windowStage: window.WindowStage): void {
       // Main window is created, set main page for this ability
       hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
   
       windowStage.loadContent('pages/FormEditIndex', (err) => {
         if (err.code) {
           hilog.error(DOMAIN, 'testTag', 'Failed to load the content. Code:${err.code}, message:${err.message}');
           return;
         }
         hilog.info(DOMAIN, 'testTag', 'Succeeded in loading the content.');
       });
       AppStorage.setOrCreate('windowStage', this.context);
     }
   
     onWindowStageDestroy(): void {
       // Main window is destroyed, release UI related resources
       hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
     }
   
     onForeground(): void {
       // Ability has brought to foreground
       hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onForeground');
     }
   
     onBackground(): void {
       // Ability has back to background
       hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onBackground');
     }
   }
   ```

   - Configure the new `EntryEditAbility` in `module.json5` as follows.
   <!-- @[FormEditUIAbility_modulejson5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditUIAbility/entry/src/main/module.json5) -->

   ``` JSON5
   "abilities": [
     // ...
     {
       "name": "FormEditAbility",
       "srcEntry": "./ets/entryability/EntryEditAbility.ets",
       "description": "$string:EntryAbility_desc",
       "icon": "$media:layered_image",
       "label": "$string:EntryAbility_label",
       "startWindowIcon": "$media:startIcon",
       "startWindowBackground": "$color:start_window_background",
       "exported": true,
     }
   ],
   ```

   - Implement the widget `form_config.json` file.
   ```json5
   // entry/src/main/resources/base/profile/form_config.json
   {
     "forms": [
       {
         "name": "widget",
         "displayName": "$string:widget_display_name",
         "description": "$string:widget_desc",
         "src": "./ets/widget/pages/WidgetCard.ets",
         "uiSyntax": "arkts",
         "isDynamic": true,
         "isDefault": true,
         "updateEnabled": false,
         "formConfigAbility": "ability://FormEditAbility",
         "scheduledUpdateTime": "10:30",
         "updateDuration": 1,
         "defaultDimension": "2*2",
         "supportDimensions": [
           "2*2"
         ]
       }
     ]
   }
   ```

3. Add the `FormEditIndex.ets` file to implement the full-screen edit page layout. Use [updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform) to refresh information about the widget being edited.
   <!-- @[FormEditUIAbility_FormEditIndex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditUIAbility/entry/src/main/ets/pages/FormEditIndex.ets) -->

   ``` TypeScript
   // entry/src/main/ets/pages/FormEditIndex.ets
   import { formBindingData, formProvider } from '@kit.FormKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { PreferencesUtil } from '../common/PreferencesUtil';
   import { preferences } from '@kit.ArkData';
   
   const TAG: string = 'FormEdit -->';
   
   @Entry
   @Component
   struct FormEditIndex {
     @State message: string = 'Hello World';
     @State message1: string = 'Beijing';
     @State message2: string = 'Shanghai';
   
     updateForm(message: string) {
       // Obtain the ID of the widget that needs to be edited from the database.
       let util = PreferencesUtil.getInstance();
       let preferences = util.getPreferences(this.getUIContext().getHostContext() as Context) as preferences.Preferences;
       let formId: string = util.getValue(preferences) as string;
       if (!formId) {
         return;
       }
       console.info(TAG, `doy: formId: ${formId}, message: ${message}`)
       let param: Record<string, string> = {
         'message': message
       }
       let obj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
       try {
         formProvider.updateForm(formId, obj, (error: BusinessError) => {
           if (error) {
             console.error(TAG, `callback error, code: ${error.code}, message: ${error.message})`);
             return;
           }
           console.info(TAG, `formProvider updateForm success`);
         });
       } catch (error) {
         console.error(TAG, `catch error, Code:${error.code}, message:${error.message}`);
       }
     }
   
     build() {
       Row() {
         Column() {
           Button($r('app.string.button_one'))
             .width('80%')
             .type(ButtonType.Capsule)
             .margin({
               top: 20
             })
             .onClick(() => {
               this.updateForm(this.message1);
             })
           Button($r('app.string.button_two'))
             .width('80%')
             .type(ButtonType.Capsule)
             .margin({
               top: 20
             })
             .onClick(() => {
               this.updateForm(this.message2);
             })
         }
       }
       .justifyContent(FlexAlign.Center)
       .width('100%')
     }
   }
   ```

   - Load the full-screen edit page layout file.
   ```json5
   // entry/src/main/resources/base/profile/main_pages.json
   {
     "src": [
       "pages/Index",
       "pages/FormEditIndex"
     ]
   }
   ```

   - The widget layout file is as follows.
   <!-- @[FormEditUIAbility_WidgetCard](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditUIAbility/entry/src/main/ets/widget/pages/WidgetCard.ets) -->

   ``` TypeScript
   // entry/src/main/ets/widget/pages/WidgetCard.ets
   @Entry
   @Component
   struct WidgetCard {
     @LocalStorageProp('message') title: string = 'Hello World';
     readonly actionType: string = 'router';
     readonly abilityName: string = 'EntryAbility';
     readonly message: string = 'add detail';
     readonly fullWidthPercent: string = '100%';
     readonly fullHeightPercent: string = '100%';
   
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
       .backgroundColor($r('sys.color.comp_background_primary'))
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

4. Add the `PreferencesUtil` file to encapsulate [Preferences](../database/data-persistence-by-preferences.md) for persisting service data.
   <!-- @[FormEditUIAbility_PreferencesUtil](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormEditUIAbility/entry/src/main/ets/common/PreferencesUtil.ets) -->

   ``` TypeScript
   // entry/src/main/ets/common/PreferencesUtil.ets
   import { preferences } from '@kit.ArkData';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   const TAG: string = 'PreferencesUtil';
   const MY_STORE: string = 'myStore';
   const key: string = 'formID';
   
   export class PreferencesUtil {
     private static preferencesUtil: PreferencesUtil;
   
     public static getInstance(): PreferencesUtil {
       if (!PreferencesUtil.preferencesUtil) {
         PreferencesUtil.preferencesUtil = new PreferencesUtil();
       }
       return PreferencesUtil.preferencesUtil;
     }
   
     getPreferences(context: Context): preferences.Preferences | undefined {
       try {
         preferences.removePreferencesFromCacheSync(context, MY_STORE);
         return preferences.getPreferencesSync(context, { name: MY_STORE });
       } catch (error) {
         let err = error as BusinessError;
         console.error(TAG, `getPreferences failed, error code=${err.code}, message=${err.message}`);
         return undefined;
       }
     }
   
     preferencesFlush(preferences: preferences.Preferences) {
       preferences.flushSync();
     }
   
     preferencesPut(preferences: preferences.Preferences, formID: string): void {
       try {
         preferences.putSync(key, formID);
         preferences.flushSync();
       } catch (error) {
         let err = error as BusinessError;
         console.error(TAG, `preferencesPut failed, error code=${err.code}, message=${err.message}`);
       }
     }
   
     removePreferencesFromCache(context: Context): void {
       preferences.removePreferencesFromCache(context, MY_STORE).catch((err: BusinessError) => {
         console.error(TAG, `removePreferencesFromCache failed, error code=${err.code}, message=${err.message}`);
       });
     }
   
     getValue(preferences: preferences.Preferences): string | undefined {
       if (preferences === null) {
         console.error(TAG, `preferences is null`);
         return undefined;
       }
       try {
         return preferences.getSync(key, '') as string
       } catch (error) {
         let err = error as BusinessError;
         console.error(TAG, `getSync failed, error code=${err.code}, message=${err.message}`);
         return undefined;
       }
     }
   
     removeFormId(context: Context) {
       try {
         let preferences = this.getPreferences(context);
         if (!preferences) {
           console.error(TAG, `preferences is null`);
           return;
         }
         if (preferences.hasSync(key)) {
           preferences.deleteSync(key);
           preferences.flushSync();
           console.info(TAG, `deleteSync done.`)
         }
       } catch (error) {
         console.error(TAG, `Failed to get preferences. Code:${error.code}, message:${error.message}`);
       }
     }
   }
   ```

5. The resource file is as follows.
   ```json5
   // entry/src/main/resources/base/element/string.json
   {
     "string": [
       // ...
       {
         "name": "button_one",
         "value": "Switch to: Beijing"
       },
       {
         "name": "button_two",
         "value": "Switch to: Shanghai"
       }
     ]
   }
   ```
