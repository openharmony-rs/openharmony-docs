# OpenLinkOptions

```TypeScript
export default interface OpenLinkOptions
```

**OpenLinkOptions** can be used as an input parameter of [openLink()](arkts-ability-uiabilitycontext-c.md#openlink) to indicate whether to enable only App Linking and pass in optional parameters in the form of key-value pairs.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { OpenLinkOptions } from '@kit.AbilityKit';
```

## appLinkingOnly

```TypeScript
appLinkingOnly?: boolean
```

Whether the UIAbility must be started using &lt;!--RP1--&gt; [App Linking](../../../application-models/app-linking-startup.md)&lt;!--RP1End--&gt;.

- If this parameter is set to **true** and no UIAbility matches the URL in App Linking, the result is returned  
directly.  
- If this parameter is set to **false** and no UIAbility matches the URL in App Linking, App Linking falls back to [Deep Linking](../../../application-models/deep-linking-startup.md). The default value is **false**.

When the aa command is used to implicitly start an ability, you can set **--pb appLinkingOnly true** or **--pb appLinkingOnly false** to start the ability in App Linking mode.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## completionHandler

```TypeScript
completionHandler?: CompletionHandler
```

Operation class used to handle the result of an application launch request.

**Type:** [CompletionHandler](arkts-ability-app-ability-completionhandler-completionhandler-c.md)

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## hideFailureTipDialog

```TypeScript
hideFailureTipDialog?: boolean
```

Whether to display a "No app available" dialog box when a suitable application is not found using [Deep Linking](../../../application-models/deep-linking-startup.md).

- **true**: The "No app available" dialog box is not displayed.  
- **false**: The "No app available" dialog box is displayed. The default value is **false**.

Note: If **appLinkingOnly** is set to **true**, the Deep Linking process is not triggered, and this field does not take effect.

**Type:** boolean

**Default:** { false }

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, Object>
```

List of parameters in Want.

Note: For details about the usage rules, see **parameters** in [want](arkts-ability-app-ability-want-want-c.md).

**Type:** Record&lt;string, Object&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
import { common, OpenLinkOptions, wantConstant, CompletionHandler, bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

const DOMAIN = 0xeeee;
const TAG: string = '[openLinkDemo]';

@Entry
@Component
struct Index {
  @State message: string = 'I am caller';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
        Button('start browser', { type: ButtonType.Capsule, stateEffect: true })
          .width('87%')
          .height('5%')
          .margin({ bottom: '12vp' })
          .onClick(() => {
            // Obtain the UIAbilityContext.
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let link: string = 'https://www.example.com';
            let completionHandler: CompletionHandler = {
              onRequestSuccess: (elementName: bundleManager.ElementName, message: string): void => {
                console.info(`${elementName.bundleName}-${elementName.moduleName}-${elementName.abilityName} start succeeded: ${message}`);
              },
              onRequestFailure: (elementName: bundleManager.ElementName, message: string): void => {
                console.error(`${elementName.bundleName}-${elementName.moduleName}-${elementName.abilityName} start failed: ${message}`);
              }
            };
            let openLinkOptions: OpenLinkOptions = {
              appLinkingOnly: true,
              // hideFailureTipDialog takes effect only when appLinkingOnly is set to false.
              // hideFailureTipDialog: true,
              parameters: {
                [wantConstant.Params.CONTENT_TITLE_KEY]: 'contentTitle',
                keyString: 'str',
                keyNumber: 200,
                keyBool: false,
                keyObj: {
                  keyObjKey: 'objValue',
                }
              },
              completionHandler: completionHandler
            };
            try {
              // Launch the target application using the openLink API.
              context.openLink(
                link,
                openLinkOptions,
                // Result callback: err is the error information, and result contains the return code resultCode and the want parameter.
                (err, result) => {
                  if (err) {
                    hilog.error(DOMAIN, TAG, `openLink callback error.code: ${JSON.stringify(err.code)}, message: ${JSON.stringify(err.message)}`); 
                    return;
                  }
                  hilog.info(DOMAIN, TAG, `openLink callback result: ${JSON.stringify(result.resultCode)}`);
                  hilog.info(DOMAIN, TAG, `openLink callback result data: ${JSON.stringify(result.want)}`);
                }
              // Print a log if the call succeeds, and catch the error if the call fails.
              ).then(() => {
                hilog.info(DOMAIN, TAG, `open link success.`);
              }).catch ((err: BusinessError) => {
                hilog.error(DOMAIN, TAG, `open link failed, errCode: ${JSON.stringify(err.code)}, message: ${JSON.stringify(err.message)}`);
              });
            } catch (e) {
              hilog.error(DOMAIN, TAG, `open link failed, errCode: ${JSON.stringify(e.code)}, message: ${JSON.stringify(e.message)}`);
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
