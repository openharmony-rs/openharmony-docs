# StartOptions

StartOptions可以作为启动UIAbility接口（例如 [startAbility()](arkts-ability-uiabilitycontext-c.md#startability) ）的入参，用于指定目标UIAbility启动时的选项，包括但不局限于窗口模式、目标UIAbility启动时所在的屏幕等。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { StartOptions } from '@kit.AbilityKit';
```

## windowFocused

```TypeScript
windowFocused?: boolean
```

窗口是否获焦。默认是true，表示窗口获焦。  
**约束：**
1.该功能仅在2in1和Tablet设备上生效。
2.仅在[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability)中生效。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**示例**

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

    let color = new ArrayBuffer(512 * 512 * 4); // 创建一个ArrayBuffer对象，用于存储图像像素。该对象的大小为（height * width * 4）字节。
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
      // 配置启动UIAbility的选项参数
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
        // 调用startAbility接口启动目标UIAbility，传入Want参数和启动选项
        this.context.startAbility(want, options, (err: BusinessError) => {
          if (err.code) {
            // 处理业务逻辑错误
            console.error(`startAbility failed, code is ${err.code}, message is ${err.message}`);
            return;
          }
          // 执行正常业务
          console.info('startAbility succeed');
        });
      } catch (err) {
        // 处理入参错误异常
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
      // 启动指定的Ability，传入Want和StartOptions参数
      this.context.startAbility(want, options, (err: BusinessError) => {
        if (err.code) {
          // 处理业务逻辑错误
          console.error(`startAbility failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        // 执行正常业务
        console.info('startAbility succeed');
      });
    } catch (err) {
      // 处理入参错误异常
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`startAbility failed, code is ${code}, message is ${message}`);
    }
  }
}
```
