# @ohos.app.ability.StartOptions (Optional Parameters of startAbility)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @dsz2025; @yangxuguang-huawei; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=17d3b236d2c2a3bbfc7bc46d7fe0f1415b7b5049 translatedAt=2026-09-03T10:36:05.144Z pushedAt=2026-09-05T10:47:30.446Z -->

StartOptions is used as an input parameter of the APIs for starting a UIAbility (for example, [startAbility()](js-apis-inner-application-uiAbilityContext.md#startability-1)) to specify the options for starting the target UIAbility, including but not limited to the window mode and the screen on which the target UIAbility is started.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { StartOptions } from '@kit.AbilityKit';
```

## StartOptions

StartOptions is used to specify the options for starting a UIAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| windowMode<sup>12+</sup> | number | No | Yes | Window mode when starting the UIAbility. For details, see [WindowMode](./js-apis-app-ability-abilityConstant.md#windowmode12). |
| splitRatio | [window.SplitRatioPreference](../apis-arkui/arkts-apis-window-e.md#splitratiopreference) | No | Yes | Window split ratio when starting the UIAbility.<br>**Since:** 26.0.0 |
| displayId | number | No | Yes | Screen ID, which is an integer greater than or equal to -1.<br>- The value -1 indicates the current screen.<br>- The value 0 indicates the primary screen.<br>- A positive integer indicates the screen with the specified ID.<br>**Note:**<br>Since API version 14, the default value is -1, which indicates the current screen.<br>Before API version 14, the default value is 0, which indicates the primary screen.<br>**Atomic service API**: This API is supported in atomic services since API version 11. |
| withAnimation<sup>11+</sup> | boolean | No | Yes | Whether to apply an animation effect when starting the UIAbility.<br>If true is passed, the system default animation effect is used. If false is passed, the animation effect for starting the UIAbility is disabled.<br> **Constraints**<br>This feature takes effect only in the [free window](../../windowmanager/window-terminology.md#freeform-window) state, and the caller and the target must be the same application.<br>If this parameter is not set, the default value is undefined, and the system default animation effect is used.<br>Supported since <!--RP2-->OpenHarmony 6.1<!--RP2End-->. |
| windowLeft<sup>11+</sup> | number | No | Yes | Offset of the window along the x-axis, in px, with the top-left vertex of the screen specified by displayId as the origin. A positive value indicates that the window is to the right of the origin, and a negative value indicates that the window is to the left of the origin. This parameter is an integer, and a non-integer value is rounded down. When the left vertex of the window exceeds the screen area specified by displayId, the window is constrained to be visible within the screen area specified by displayId. When configuring this field, you are advised to configure windowTop as well.<br> **Constraints**<br>This feature takes effect only in the [free window](../../windowmanager/window-terminology.md#freeform-window) state. |
| windowTop<sup>11+</sup> | number | No | Yes | Offset of the window along the y-axis, in px, with the top-left vertex of the screen specified by displayId as the origin. A positive value indicates that the window is below the origin, and a negative value indicates that the window is above the origin. This parameter is an integer, and a non-integer value is rounded down. When the top of the window exceeds the screen area specified by displayId, the window is constrained to be visible within the screen area specified by displayId. When configuring this field, you are advised to configure windowLeft as well.<br> **Constraints**<br>This feature takes effect only in the [free window](../../windowmanager/window-terminology.md#freeform-window) state. |
| windowWidth<sup>11+</sup> | number | No | Yes | Width of the window, in px.<br>The value range is [minWindowWidth, maxWindowWidth], in vp. You can refer to [vp2px](../apis-arkui/arkts-apis-uicontext-uicontext.md#vp2px12) to convert the value to px.<br> **Constraints**<br>This feature takes effect only in the [free window](../../windowmanager/window-terminology.md#freeform-window) state. |
| windowHeight<sup>11+</sup> | number | No | Yes | Height of the window, in px.<br>The value range is [minWindowHeight, maxWindowHeight], in vp. You can refer to [vp2px](../apis-arkui/arkts-apis-uicontext-uicontext.md#vp2px12) to convert the value to px.<br> **Constraints**<br>This feature takes effect only in the [free window](../../windowmanager/window-terminology.md#freeform-window) state. |
| processMode<sup>12+</sup> | [contextConstant.ProcessMode](js-apis-app-ability-contextConstant.md#processmode12) | No | Yes | Process mode after the UIAbility is started. If not specified, the system default process mode is used.<br>**Constraints**<br>1. This feature takes effect only on 2-in-1 and tablet devices.<br>2. It takes effect only in [UIAbilityContext.startAbility](js-apis-inner-application-uiAbilityContext.md#startability-1).<br>3. processMode and startupVisibility must be set at the same time. |
| startupVisibility<sup>12+</sup> | [contextConstant.StartupVisibility](js-apis-app-ability-contextConstant.md#startupvisibility12) | No | Yes | Visibility after the UIAbility is started. If not specified, the UIAbility is visible by default. When the user sets the target UIAbility to invisible, the window of the target UIAbility is not displayed in the foreground, no icon is displayed in the dock, and the onForeground lifecycle of the target UIAbility is not invoked.<br>**Constraints**<br>1. This feature takes effect only on 2-in-1 and tablet devices.<br>2. It takes effect only in [UIAbilityContext.startAbility](js-apis-inner-application-uiAbilityContext.md#startability-1).<br>3. processMode and startupVisibility must be set at the same time. |
| startWindowIcon<sup>14+</sup> | [image.PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md) | No| Yes|  Icon displayed on the starting window for the UIAbility of the current application upon startup. If this property is not set, the value of **startWindowIcon** in the **module.json5** file is used by default.<br>**Constraints**:<br>- This property does not take effect for the UIAbility of another application.<br>- This property takes effect only on 2-in-1 devices and tablets.<br>- This property takes effect only in [UIAbilityContext.startAbility](js-apis-inner-application-uiAbilityContext.md#startability-1).<br>- The maximum size of an image used as the startup icon is 600 MB.|
| startWindowBackgroundColor<sup>14+</sup> | string | No | Yes | Background color displayed on the startup page when starting the UIAbility of the current application. The value is in ARGB format, for example, `#E5FFFFFF`. If this field is not configured, the value of the startWindowBackground field in the module.json5 file is used by default.<br>**Constraints**<br>- This field does not take effect when starting the UIAbility of another application.<br>- This feature takes effect only on 2-in-1 and tablet devices.<br>- It takes effect only in [UIAbilityContext.startAbility](js-apis-inner-application-uiAbilityContext.md#startability-1). |
| supportWindowModes<sup>14+</sup> | Array\<[bundleManager.SupportWindowMode](./js-apis-bundleManager.md#supportwindowmode)> | No | Yes | Specifies whether to display the maximize/window/split buttons when starting the UIAbility. If this field is not configured, the value of the supportWindowMode field in the [abilities label](../../quick-start/module-configuration-file.md#abilities-label) of the [module.json5 configuration file](../../quick-start/module-configuration-file.md) corresponding to the UIAbility is used by default.<br>- FULL_SCREEN: supports the full-screen mode.<br>- FLOATING: supports the floating window mode.<br>- SPLIT: supports the split-screen mode. It is usually used together with FULL_SCREEN or FLOATING, and configuring only SPLIT is not recommended. When only SPLIT is configured, the window on a 2-in-1 device is in the floating window mode by default and supports entering the split-screen mode; the window on a tablet device is in the full-screen mode by default and supports entering the split-screen mode. <br> When both FULL_SCREEN and SPLIT are configured in the [free window](../../windowmanager/window-terminology.md#freeform-window) state, if the [targetAPIVersion](../../quick-start/app-configuration-file.md#configuration-file-label) of the application is earlier than 15, the window is started in the floating window mode; if the [targetAPIVersion](../../quick-start/app-configuration-file.md#configuration-file-label) of the application is 15 or later, the window is started in the full-screen mode. <br> **Constraints**<br><!--RP1-->This feature takes effect only on 2-in-1 and tablet devices.<!--RP1End-->|
| minWindowWidth<sup>17+</sup> | number | No | Yes | Minimum width of the window, in vp. You can call [getWindowLimitsVP](../apis-arkui/arkts-apis-window-Window.md#getwindowlimitsvp22) to obtain the current window size limit.<br>**Constraints**<br>This feature takes effect only in the [free window](../../windowmanager/window-terminology.md#freeform-window) state. |
| minWindowHeight<sup>17+</sup> | number | No | Yes | Minimum height of the window, in vp. You can call [getWindowLimitsVP](../apis-arkui/arkts-apis-window-Window.md#getwindowlimitsvp22) to obtain the current window size limit.<br>**Constraints**<br>This feature takes effect only in the [free window](../../windowmanager/window-terminology.md#freeform-window) state. |
| maxWindowWidth<sup>17+</sup> | number | No | Yes | Maximum width of the window, in vp. You can call [getWindowLimitsVP](../apis-arkui/arkts-apis-window-Window.md#getwindowlimitsvp22) to obtain the current window size limit.<br>**Constraints**<br>This feature takes effect only in the [free window](../../windowmanager/window-terminology.md#freeform-window) state. |
| maxWindowHeight<sup>17+</sup> | number | No | Yes | Maximum height of the window, in vp. You can call [getWindowLimitsVP](../apis-arkui/arkts-apis-window-Window.md#getwindowlimitsvp22) to obtain the current window size limit.<br>**Constraints**<br>This feature takes effect only in the [free window](../../windowmanager/window-terminology.md#freeform-window) state. |
| completionHandler<sup>20+</sup> | [CompletionHandler](js-apis-app-ability-completionHandler.md) | No | Yes | Operation class for the result of starting an application, used to process the result of starting the application. If not specified, the result of starting the application is not processed.<br/>**Atomic service API**: This API is supported in atomic services since API version 20. |
| hideStartWindow<sup>20+</sup> | boolean | No | Yes | Controls whether to hide the startup page of the window when starting the UIAbility of the current application. The value true indicates hiding the startup page, and the value false indicates not hiding the startup page. For details about the startup page, see [StartWindow](../../quick-start/module-configuration-file.md#startwindow-label).<br>**Constraints**<br/>1. This feature takes effect only on 2-in-1 devices and tablet devices in free multi-window mode.<br/>2. This feature takes effect only when starting the UIAbility of the current application. |
| windowCreateParams<sup>20+</sup> | [window.WindowCreateParams](../apis-arkui/arkts-apis-window-i.md#windowcreateparams20) | No| Yes| Parameters for the window for the UIAbility upon startup.|

**Example**

  ```ts
  import { UIAbility, Want, StartOptions, bundleManager, CompletionHandler } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { image } from '@kit.ImageKit';
  import { window } from '@kit.ArkUI';

  export default class EntryAbility extends UIAbility {
    onForeground() {
      let want: Want = {
        deviceId: '',
        bundleName: 'com.example.myapplication',
        abilityName: 'EntryAbility'
      };

      let completionHandler: CompletionHandler = {
        onRequestSuccess: (elementName: bundleManager.ElementName, message: string): void => {
          console.info(`${elementName.bundleName}-${elementName.moduleName}-${elementName.abilityName} start succeeded: ${message}`);
        },
        onRequestFailure: (elementName: bundleManager.ElementName, message: string): void => {
          console.error(`${elementName.bundleName}-${elementName.moduleName}-${elementName.abilityName} start failed: ${message}`);
        }
      };

      let color = new ArrayBuffer(512 * 512 * 4); // Create an ArrayBuffer object to store image pixels. The size of the object is (height * width * 4) bytes.
      let imagePixelMap: image.PixelMap;
      let windowParam: window.WindowCreateParams = {};
      let bufferArr = new Uint8Array(color);
      for (let i = 0; i < bufferArr.length; i += 4) {
        bufferArr[i] = 255;
        bufferArr[i+1] = 0;
        bufferArr[i+2] = 122;
        bufferArr[i+3] = 255;
      }
      image.createPixelMap(color, {
        editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 512, width: 512 }
      }).then((data) => {
        imagePixelMap = data;
        // Configure the options for starting the UIAbility.
        let options: StartOptions = {
          displayId: 0,
          startWindowIcon: imagePixelMap,
          startWindowBackgroundColor: '#E510FFFF',
          supportWindowModes: [
            bundleManager.SupportWindowMode.FULL_SCREEN,
            bundleManager.SupportWindowMode.SPLIT,
            bundleManager.SupportWindowMode.FLOATING
          ],
          minWindowWidth: 320,
          minWindowHeight: 240,
          maxWindowWidth: 2560,
          maxWindowHeight: 2560,
          completionHandler: completionHandler,
          hideStartWindow: true,
          windowCreateParams: windowParam
        };

        try {
          // Call the startAbility API to start the target UIAbility, passing in the Want parameter and start options.
          this.context.startAbility(want, options, (err: BusinessError) => {
            if (err.code) {
              // Process service logic errors.
              console.error(`startAbility failed, code is ${err.code}, message is ${err.message}`);
              return;
            }
            // Carry out normal service processing.
            console.info('startAbility succeed');
          });
        } catch (err) {
          // Process input parameter errors.
          let code = (err as BusinessError).code;
          let message = (err as BusinessError).message;
          console.error(`startAbility failed, code is ${code}, message is ${message}`);
        }
      }).catch((err: BusinessError) => {
        console.error(`createPixelMap failed, code is ${err.code}, message is ${err.message}`);
      });
    }
  }
  ```
