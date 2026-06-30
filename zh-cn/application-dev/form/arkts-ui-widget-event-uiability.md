# 通过router或call事件刷新卡片内容
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->

使用router事件，点击卡片可拉起对应应用的UIAbility至前台，并刷新卡片。使用call事件，点击卡片可拉起对应应用的UIAbility至后台，并刷新卡片。在卡片页面中可以通过[postCardAction](../reference/apis-arkui/js-apis-postCardAction.md#postcardaction-1)接口触发router事件或者call事件拉起UIAbility，然后由UIAbility刷新卡片内容，下面是这种刷新方式的简单示例。

> **说明：**
>
> 本文主要介绍动态卡片的事件开发。对于静态卡片，请参见[FormLink](../reference/apis-arkui/arkui-ts/ts-container-formlink.md)。

## 通过router事件刷新卡片内容

- 在卡片页面代码文件中，通过注册Button的onClick点击事件回调并在回调中调用postCardAction接口，触发router事件拉起UIAbility至前台。
  
    <!-- @[widget_update_router_card](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/widgetupdaterouter/pages/WidgetUpdateRouterCard.ets) --> 
    
    ``` TypeScript
    // entry/src/main/ets/widgetupdaterouter/pages/WidgetUpdateRouterCard.ets
    let storageUpdateRouter = new LocalStorage();
    
    @Entry(storageUpdateRouter)
    @Component
    struct WidgetUpdateRouterCard {
      // $r('app.string.init')需要替换为开发者所需的资源文件
      @LocalStorageProp('routerDetail') routerDetail: ResourceStr = $r('app.string.init');
    
      build() {
        Column() {
          Column() {
            Text(this.routerDetail)
              .fontColor('#FFFFFF')
              .opacity(0.9)
              .fontSize(14)
              .margin({ top: '8%', left: '10%', right: '10%' })
              .textOverflow({ overflow: TextOverflow.Ellipsis })
              .maxLines(2)
          }.width('100%').height('50%')
          .alignItems(HorizontalAlign.Start)
    
          Row() {
            Button() {
              // $r('app.string.JumpLabel')需要替换为开发者所需的资源文件
              Text($r('app.string.JumpLabel'))
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
                action: 'router',
                abilityName: 'WidgetEventRouterEntryAbility', // 只能跳转到当前应用下的UIAbility
                params: {
                  routerDetail: 'RouterFromCard',
                }
              });
            })
          }.width('100%').height('40%')
          .justifyContent(FlexAlign.Center)
        }
        .width('100%')
        .height('100%')
        .alignItems(HorizontalAlign.Start)
        // $r('app.media.CardEvent')需要替换为开发者所需的资源文件
        .backgroundImage($r('app.media.CardEvent'))
        .backgroundImageSize(ImageSize.Cover)
      }
    }
    ```
  
- 在UIAbility的onCreate或者onNewWant生命周期中可以通过入参want获取卡片的formID和传递过来的参数信息，然后调用[updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform)接口刷新卡片。
  
    <!-- @[widget_event_router_entry_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/widgetevententryability/WidgetEventRouterEntryAbility.ts) -->
    
## 通过call事件刷新卡片内容

- 在卡片页面代码文件中，通过注册Button的onClick点击事件回调并在回调中调用postCardAction接口，触发call事件拉起UIAbility至后台。
  
    <!-- @[widget_update_call_card](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/widgetupdatecall/pages/WidgetUpdateCallCard.ets) --> 
    
    ``` TypeScript
    // entry/src/main/ets/widgetupdatecall/pages/WidgetUpdateCallCard.ets
    let storageUpdateCall = new LocalStorage();
    
    @Entry(storageUpdateCall)
    @Component
    struct WidgetUpdateCallCard {
      @LocalStorageProp('formId') formId: string = '12400633174999288';
      // $r('app.string.init')需要替换为开发者所需的资源文件
      @LocalStorageProp('calleeDetail') calleeDetail: ResourceStr = $r('app.string.init');
    
      build() {
        Column() {
          Column() {
            Text(this.calleeDetail)
              .fontColor('#FFFFFF')
              .opacity(0.9)
              .fontSize(14)
              .margin({ top: '8%', left: '10%' })
          }.width('100%').height('50%')
          .alignItems(HorizontalAlign.Start)
    
          Row() {
            Button() {
              // $r('app.string.CalleeJumpLabel')需要替换为开发者所需的资源文件
              Text($r('app.string.CalleeJumpLabel'))
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
                action: 'call',
                abilityName: 'WidgetCalleeEntryAbility', // 只能拉起当前应用下的UIAbility
                params: {
                  method: 'funA',
                  formId: this.formId,
                  calleeDetail: 'CallFrom'
                }
              });
            })
          }.width('100%').height('40%')
          .justifyContent(FlexAlign.Center)
        }
        .width('100%')
        .height('100%')
        .alignItems(HorizontalAlign.Start)
        // $r('app.media.CardEvent')需要替换为开发者所需的资源文件
        .backgroundImage($r('app.media.CardEvent'))
        .backgroundImageSize(ImageSize.Cover)
      }
    }
    ```
  
- 在UIAbility的onCreate生命周期中监听call事件所需的方法，然后在对应方法中调用[updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform)接口刷新卡片。
  
    <!-- @[widget_callee_entry_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/ets/widgetcalleeentryability/WidgetCalleeEntryAbility.ts) -->
    
  要拉起UIAbility至后台，需要在`module.json5`配置文件中，配置`ohos.permission.KEEP_BACKGROUND_RUNNING`权限。
    <!-- @[module_json5_request_permissions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ApplicationModels/StageServiceWidgetCards/entry/src/main/module.json5) -->
    
    ``` JSON5
    //src/main/module.json5
    "requestPermissions": [
      {
        "name": "ohos.permission.KEEP_BACKGROUND_RUNNING",
      },
    // ···
    ]
    ```