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

## windowFocused

```TypeScript
windowFocused?: boolean
```

Whether the window has focus. The default value is **true**, indicating that the window has focus; **false** indicates that the window does not have focus.

**Constraints**:

1. This property takes effect only on 2-in-1 devices and tablets.
2. This property takes effect only in
[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability).

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

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
