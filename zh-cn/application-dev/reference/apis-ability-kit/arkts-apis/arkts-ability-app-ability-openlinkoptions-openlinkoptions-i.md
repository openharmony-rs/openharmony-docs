# OpenLinkOptions

OpenLinkOptions可以作为[openLink()](arkts-ability-uiabilitycontext-c.md#openlink)的入参，用于标识是否仅打开 AppLinking和传递键值对可选参数。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { OpenLinkOptions } from '@kit.AbilityKit';
```

## appLinkingOnly

```TypeScript
appLinkingOnly?: boolean
```

表示是否必须以<!--RP1-->[AppLinking](../../../application-models/app-linking-startup.md)<!--RP1End-->的方式启动UIAbility。  
- 取值为true时，如果不存在与AppLinking相匹配的UIAbility，直接返回。  
- 取值为false时，如果不存在与AppLinking相匹配的UIAbility，AppLinking会退化为  
[DeepLinking](../../../application-models/deep-linking-startup.md)。默认值为false。aa命令隐式拉起Ability时可以通过设置"--pb appLinkingOnly true/false"以AppLinking的方式进行启动。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## completionHandler

```TypeScript
completionHandler?: CompletionHandler
```

拉起应用结果的操作类，用于处理拉起应用的结果。

**类型：** [CompletionHandler](arkts-ability-app-ability-completionhandler-completionhandler-c.md)

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## hideFailureTipDialog

```TypeScript
hideFailureTipDialog?: boolean
```

表示[Deep Linking](../../../application-models/deep-linking-startup.md)找不到应用时是否显示“暂无可用打开方式”的弹窗。  
- 取值为true时，不显示“暂无可用打开方式”的弹窗。  
- 取值为false时，显示“暂无可用打开方式”的弹窗。默认值为false。  
**说明：**appLinkingOnly字段为true时不会触发Deep Linking流程，该字段不会生效。

**类型：** boolean

**默认值：** { false }

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, Object>
```

表示WantParams参数。  
**说明：**具体使用规则请参考[want](arkts-ability-app-ability-want-want-c.md)中的parameters属性。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

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
            // 获取UIAbilityContext
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
              // hideFailureTipDialog字段需要在appLinkingOnly字段是false时才生效
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
              // 用openLink接口拉起目标应用。
              context.openLink(
                link,
                openLinkOptions,
                // 结果回调：err为错误信息，result包含返回码resultCode和want参数。
                (err, result) => {
                  if (err) {
                    hilog.error(DOMAIN, TAG, `openLink callback error.code: ${JSON.stringify(err.code)}, message: ${JSON.stringify(err.message)}`); 
                    return;
                  }
                  hilog.info(DOMAIN, TAG, `openLink callback result: ${JSON.stringify(result.resultCode)}`);
                  hilog.info(DOMAIN, TAG, `openLink callback result data: ${JSON.stringify(result.want)}`);
                }
              // 调用成功打印日志，调用失败捕获错误。
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
