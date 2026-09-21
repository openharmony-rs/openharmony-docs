# StartOptions

```TypeScript
declare class StartOptions
```

StartOptions can be used as an input parameter for APIs used to launch a UIAbility (for example, [startAbility()](arkts-ability-uiabilitycontext-c.md#startability-1)). It specifies the options for starting the target UIAbility, including but not limited to the window mode and the display where the target UIAbility is started.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { StartOptions } from '@kit.AbilityKit';
```

## completionHandler

```TypeScript
completionHandler?: CompletionHandler
```

Operation class used to handle the result of an application launch request.

**Type:** [CompletionHandler](arkts-ability-app-ability-completionhandler-completionhandler-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## displayId

```TypeScript
displayId?: number
```

Display ID, which is an integer greater than or equal to -1.

- The value **-1** means the current screen.  
- The value **0** means the primary screen.  
- A positive integer means a specific screen with that ID.

**NOTE:** 

Starting from API version 14, the default value is **-1**, indicating the current screen.

In versions earlier than API version 14, the default value is **0**, indicating the primary screen.

**Type:** number

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## hideStartWindow

```TypeScript
hideStartWindow?: boolean
```

Whether to hide the starting window for the UIAbility of the current application upon startup. The options include **true** (yes) and **false** (no). For details about the starting window and its specifications, see [StartWindow](../../../quick-start/module-configuration-file.md#startwindow).

**Constraints**:

1. This property takes effect only on tablets in free windows mode and 2-in-1 devices.
2. This property applies only for an attempt to launch the UIAbility of the current application.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## maxWindowHeight

```TypeScript
maxWindowHeight?: number
```

Maximum height of the window, in vp. You can call getWindowLimitsVP to obtain the size limit of the current window.

**Constraints**:

This function takes effect only in the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## maxWindowWidth

```TypeScript
maxWindowWidth?: number
```

Maximum width of the window, in vp. You can call getWindowLimitsVP to obtain the size limit of the current window.

**Constraints**:

This function takes effect only in the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## minWindowHeight

```TypeScript
minWindowHeight?: number
```

Minimum height of the window, in vp. You can call getWindowLimitsVP to obtain the size limit of the current window.

**Constraints**:

This function takes effect only in the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## minWindowWidth

```TypeScript
minWindowWidth?: number
```

Minimum width of the window, in vp. You can call getWindowLimitsVP to obtain the size limit of the current window.

**Constraints**:

This function takes effect only in the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Type:** number

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## processMode

```TypeScript
processMode?: contextConstant.ProcessMode
```

Process mode of the UIAbility after it is started.

**Constraints**:

1. This property takes effect only on 2-in-1 devices and tablets.
2. This property takes effect only in
[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability).
3. **processMode** and **startupVisibility** must be set in pair.

**Type:** [contextConstant.ProcessMode](arkts-ability-contextconstant-processmode-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## splitRatio

```TypeScript
splitRatio?: window.SplitRatioPreference
```

Window allocation ratio when starting the UIAbility.

**Type:** [window.SplitRatioPreference](../../apis-arkui/arkts-apis/arkts-arkui-window-splitratiopreference-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## startupVisibility

```TypeScript
startupVisibility?: contextConstant.StartupVisibility
```

Visibility status of the UIAbility after it is started. If the target UIAbility is set to invisible, the window of the target UIAbility is not displayed in the foreground, there is no icon in the dock, and the **onForeground** lifecycle of the target UIAbility is not triggered.

**Constraints**:

1. This property takes effect only on 2-in-1 devices and tablets.
2. This property takes effect only in
[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability).
3. **processMode** and **startupVisibility** must be set in pair.

**Type:** [contextConstant.StartupVisibility](arkts-ability-contextconstant-startupvisibility-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## startWindowBackgroundColor

```TypeScript
startWindowBackgroundColor?: string
```

Background color of the window for the UIAbility of the current application upon startup. The value is in ARGB format, for example, **#E5FFFFFF**. If this property is not set, the value of **startWindowBackground** in the **module.json5** file is used by default.

**Constraints**:

- This property does not take effect for the UIAbility of another application.  
- This property takes effect only on 2-in-1 devices and tablets.  
- This property takes effect only in [UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability).

**Type:** string

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## startWindowIcon

```TypeScript
startWindowIcon?: image.PixelMap
```

Icon displayed on the starting window for the UIAbility of the current application upon startup. If this property is not set, the value of **startWindowIcon** in the **module.json5** file is used by default.

**Constraints**:

- This property does not take effect for the UIAbility of another application.  
- This property takes effect only on 2-in-1 devices and tablets.  
- This property takes effect only in [UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability).  
- The maximum size of an image used as the startup icon is 600 MB.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## supportWindowModes

```TypeScript
supportWindowModes?: Array<bundleManager.SupportWindowMode>
```

Window mode supported by the UIAbility when it is started. The supported window mode specifies whether to display the maximize, minimize, or split-screen button. If this property is not set, the value of **supportWindowMode** configured under [abilities](../../../quick-start/module-configuration-file.md#abilities) in the [module.json5](../../../quick-start/module-configuration-file.md) file corresponding to the UIAbility is used by default.

- **FULL_SCREEN**: full-screen mode.  
- **FLOATING**: floating window mode.  
- **SPLIT**: split-screen mode. Generally, **FULL_SCREEN** or **FLOATING** must be used together. You are not  
advised to configure only **SPLIT**. If only **SPLIT** is configured, the window on 2-in-1 devices is in floating window mode by default and can transition to the split-screen mode, and the window on tablets is in full-screen mode by default and can transition to the split-screen mode.

When **FULL_SCREEN** and **SPLIT** are both configured for a [freeform window](../../../windowmanager/window-terminology.md#freeform-window), the window will be started in floating window mode if the value of [targetAPIVersion](../../../quick-start/app-configuration-file.md#tags-in-the-configuration-file) is less than 15, and in full-screen mode if the value is greater than or equal to 15.

**Constraints**:

&lt;!--RP1--&gt;This property takes effect only on 2-in-1 devices and tablets.&lt;!--RP1End--&gt;

**Type:** Array&lt;[bundleManager.SupportWindowMode](arkts-ability-bundlemanager-supportwindowmode-e.md)&gt;

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## windowCreateParams

```TypeScript
windowCreateParams?: window.WindowCreateParams
```

Parameters for the window for the UIAbility upon startup.

**Type:** [window.WindowCreateParams](../../apis-arkui/arkts-apis/arkts-arkui-window-windowcreateparams-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## windowHeight

```TypeScript
windowHeight?: number
```

Window height, in px.

The value range is [**minWindowHeight**, **maxWindowHeight**], with the unit being vp. You can call [vp2px](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#vp2px) to convert it to the corresponding px value.

**Constraints**:

This function takes effect only in the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## windowLeft

```TypeScript
windowLeft?: number
```

Distance the window moves along the x-axis, with the top-left vertex of the screen specified by **displayId** as the starting point. The unit is px. A positive value means moving to the right, and a negative value means moving to the left. The value is an integer. Non-integer values will be rounded down. When the top-left vertex of the window exceeds the screen area of the specified **displayId**, the window is restricted to be visible only within the screen range of the specified **displayId**. When configuring this field, you are advised to configure **windowTop** at the same time.

**Constraints**:

This function takes effect only in the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## windowMode

```TypeScript
windowMode?: number
```

Window mode for the UIAbility upon startup. For details, see [WindowMode](arkts-ability-abilityconstant-windowmode-e.md).

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## windowTop

```TypeScript
windowTop?: number
```

Distance the window moves along the y-axis, with the top-left vertex of the screen specified by **displayId** as the starting point. The unit is px. A positive value means moving downward, and a negative value means moving upward. The value is an integer. Non-integer values will be rounded down. When the top of the window exceeds the screen area of the specified **displayId**, the window is restricted to be visible only within the screen range of the specified **displayId**. When configuring this field, you are advised to also configure **windowLeft**.

**Constraints**:

This function takes effect only in the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## windowWidth

```TypeScript
windowWidth?: number
```

Window width, in px.

The value range is [**minWindowWidth**, **maxWindowWidth**], with the unit being vp. You can call [vp2px](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#vp2px) to convert it to the corresponding px value.

**Constraints**:

This function takes effect only in the [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## withAnimation

```TypeScript
withAnimation?: boolean
```

Whether animation effects are used for the UIAbility upon startup.

When **true** is passed, the system default animation effect is used. When **false** is passed, the animation effect for starting the UIAbility is disabled.

**Constraints**:

This property takes effect only in the free window state, and the caller and target must be the same application.

If this parameter is not specified, the default value is **undefined**, and the system default animation effect is used.

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
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

```TypeScript
import { UIAbility, Want, StartOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {

  onForeground() {
    let want: Want = {
      deviceId: '',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };
    let options: StartOptions = {
      displayId: 0
    };

    try {
      // Start the specified ability, passing in the Want and StartOptions parameters.
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
  }
}
```
