# Launching UIAbility to the Background (call Event)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

There may be cases you want to provide in a widget access to features available in your application running in the foreground, for example, the play, pause, and stop buttons in a music application widget. This is where the **call** capability of the [postCardAction](../reference/apis-arkui/js-apis-postCardAction.md#postcardaction-1) API comes in handy. This capability, when used in a widget, can start the specified UIAbility of the widget provider in the background. It also allows the widget to call the specified method of the application and transfer data so that the application, while in the background, can behave accordingly in response to touching of the buttons on the widget.

> **NOTE**
>
> This topic describes development for dynamic widgets. For static widgets, see [FormLink](../reference/apis-arkui/arkui-ts/ts-container-formlink.md).

## How to Develop
1. Create a dynamic widget.

    Create a dynamic widget named WidgetEventCall.

2. Implement page layout.

    In this example, two buttons (A and B) are laid out on the widget page. When one button is touched, the **postCardAction** API is called to send a call event to the target UIAbility, with the method to be called defined in the event. Button A and button B correspond to the funA and funB methods, respectively. The funA method carries the **formID** parameter, and the funB method carries the **formID** and **num** parameters. Pass parameters as required during development. In **postCardAction**, the **method** parameter is mandatory and identifies the name of the method to be invoked, which should match the method listened for by the UIAbility in step 3. Other parameters are optional.

    <!-- @[widget_event_call_card](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/widgeteventcall/pages/WidgetEventCallCard.ets) -->
    
    ``` TypeScript
    //src/main/ets/widgeteventcall/pages/WidgetEventCallCard.ets
    let storageEventCall = new LocalStorage();
    
    @Entry(storageEventCall)
    @Component
    struct WidgetEventCallCard {
      @LocalStorageProp('formId') formId: string = '12400633174999288';
      // Replace $r('app.string.ButtonA_label') and $r('app.string.ButtonB_label') with the resource files you use.
      private funA: Resource = $r('app.string.ButtonA_label');
      private funB: Resource = $r('app.string.ButtonB_label');
    
      build() {
        RelativeContainer() {
          Button(this.funA)
            .id('funA__')
            .fontSize(14)
            .fontWeight(FontWeight.Bold)
            .alignRules({
              center: { anchor: '__container__', align: VerticalAlign.Center },
              middle: { anchor: '__container__', align: HorizontalAlign.Center }
            })
            .onClick(() => {
              postCardAction(this, {
                action: 'call',
                // Only the UIAbility of the current application is allowed. The ability name must be the same as that defined in module.json5.
                abilityName: 'WidgetEventCallEntryAbility',
                params: {
                  formId: this.formId,
                  // Name of the method to be called.
                  method: 'funA'
                }
              });
            })
    
          Button(this.funB)
            .id('funB__')
            .fontSize(14)
            .fontWeight(FontWeight.Bold)
            .margin({ top: 10 })
            .alignRules({
              top: { anchor: 'funA__', align: VerticalAlign.Bottom },
              middle: { anchor: '__container__', align: HorizontalAlign.Center }
            })
            .onClick(() => {
              postCardAction(this, {
                action: 'call',
                abilityName: 'WidgetEventCallEntryAbility',
                params: {
                  formId: this.formId,
                  // Name of the method to be called.
                  method: 'funB',
                  num: 1
                }
              });
            })
        }
        .height('100%')
        .width('100%')
      }
    }
    ```

3. Create a UIAbility.
    
    Listen for the call event in the UIAbility, call the corresponding method based on the **method** parameter, and obtain the parameter by using [rpc.Parcelable](../reference/apis-ipc-kit/js-apis-rpc.md#parcelable9). The method in the UIAbility must be the same as that in step 2.

    <!-- @[widget_event_call_card_entry_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/widgeteventcallentryability/WidgetEventCallEntryAbility.ets) -->
    
    ``` TypeScript
    //src/main/ets/WidgetEventCallEntryAbility/WidgetEventCallEntryAbility.ets
    import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { rpc } from '@kit.IPCKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    
    const TAG: string = 'WidgetEventCallEntryAbility';
    const DOMAIN_NUMBER: number = 0xFF00;
    const CONST_NUMBER_1: number = 1;
    const CONST_NUMBER_2: number = 2;
    
    // Implementation of the IPC return type, which is used for data serialization and deserialization.
    class MyParcelable implements rpc.Parcelable {
      private num: number;
      private str: string;
    
      constructor(num: number, str: string) {
        this.num = num;
        this.str = str;
      }
    
      marshalling(messageSequence: rpc.MessageSequence): boolean {
        messageSequence.writeInt(this.num);
        messageSequence.writeString(this.str);
        return true;
      }
    
      unmarshalling(messageSequence: rpc.MessageSequence): boolean {
        this.num = messageSequence.readInt();
        this.str = messageSequence.readString();
        return true;
      }
    }
    
    export default class WidgetEventCallEntryAbility extends UIAbility {
      // If the UIAbility is started, the onCreate lifecycle callback is triggered after the call event is received.
      onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
          // Listen for the method required by the call event and call the method.
          this.callee.on('funA', (data: rpc.MessageSequence) => {
            // Obtain all parameters passed in the call event.
            hilog.info(DOMAIN_NUMBER, TAG, `FunACall param:  ${JSON.stringify(data.readString())}`);
            return new MyParcelable(CONST_NUMBER_1, 'aaa');
          });
          this.callee.on('funB', (data: rpc.MessageSequence) => {
            // Obtain all parameters passed in the call event.
            hilog.info(DOMAIN_NUMBER, TAG, `FunBCall param:  ${JSON.stringify(data.readString())}`);
            return new MyParcelable(CONST_NUMBER_2, 'bbb');
          });
        } catch (err) {
          hilog.error(DOMAIN_NUMBER, TAG, `Failed to register callee on. Cause: ${JSON.stringify(err as BusinessError)}`);
        }
      }
    
      // Deregister the listener when the process exits.
      onDestroy(): void | Promise<void> {
        try {
          this.callee.off('funA');
          this.callee.off('funB');
        } catch (err) {
          hilog.error(DOMAIN_NUMBER, TAG, `Failed to register callee off. Cause: ${JSON.stringify(err as BusinessError)}`);
        }
      }
    }
    ```

4. Configure the background running permission.

    To receive the call event, the widget provider must add the background running permission ([ohos.permission.KEEP_BACKGROUND_RUNNING](../security/AccessToken/permissions-for-all.md#ohospermissionkeep_background_running)) to the **module.json5** file.

    <!-- @[module_json5_request_permissions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/module.json5) -->
    
    ``` JSON5
    //src/main/module.json5
    "requestPermissions": [
      {
        "name": "ohos.permission.KEEP_BACKGROUND_RUNNING",
      },
    // ···
      // [EndExclude jscard_extension_ability]
    ]
    ```

5. Configure the UIAbility.

    Add the WidgetEventCallEntryAbility configuration information to the abilities array in the **module.json5** file.

    <!-- @[module_json5_abilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/module.json5) -->
    
    ``` JSON5
    //src/main/module.json5
    "abilities": [
    // ···
      {
        "name": "WidgetEventCallEntryAbility",
        "srcEntry": "./ets/widgeteventcallentryability/WidgetEventCallEntryAbility.ets",
        "description": "$string:WidgetEventCallEntryAbility_desc",
        "icon": "$media:icon",
        "label": "$string:WidgetEventCallEntryAbility_label",
        "startWindowIcon": "$media:icon",
        "startWindowBackground": "$color:start_window_background"
      }
    ],
    ```
