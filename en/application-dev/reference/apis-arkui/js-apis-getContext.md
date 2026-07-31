# getContext
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

To obtain the current Ability's Context within a page, call the **getContext** API to obtain the [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) or [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md) associated with the current page.

> **NOTE**
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This API applies only to the stage model.

## getContext<sup>(deprecated)</sup>

getContext(component?: Object):Context

Obtains the **Context** object associated with an ability on the page.

> **NOTE**
> 
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [getHostContext](arkts-apis-uicontext-uicontext.md#gethostcontext12) instead. [getHostContext](arkts-apis-uicontext-uicontext.md#gethostcontext12) can be called only after a [UIContext](arkts-apis-uicontext-uicontext.md) instance is obtained using **getUIContext()**.


**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type         | Mandatory| Description                            |
| ------ | ----------- | ---- | ------------------------------- |
| component  | Object | No  | Ability instance. To obtain the context associated with a specified custom component, pass the component instance. If no component is passed in or the passed-in parameter type is invalid, the default context is returned. The default context is the context obtained by tracing the call chain of the API. If a component is passed in, the context associated with the component is returned. If no component is passed in, the default context traced by the current API call chain is returned.            |

**Return value**

| Type| Description                            |
| ------ | ------------------------------- |
| [Context](#context)  | Context of the ability. The context type depends on the ability type. For example, if this API is called on a page of the UIAbility (user UI ability), the return value type is UIAbilityContext. If this API is called on a page of the ExtensionAbility, the return value type is ExtensionContext.   |

## Context

type Context = import('../api/application/Context').default

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Type| Description                            |
| ------ | ------------------------------- |
| import('../api/application/[Context](../../application-models/application-context-stage.md)').default  | [Context](../../application-models/application-context-stage.md) of the ability where the current component is located. The specific type of the context is the context object associated with the current ability. For example, if this API is called on a page of the UIAbility, the return value type is UIAbilityContext; if this API is called on a page of the ExtensionAbility, the return value type is ExtensionContext.   |

> **NOTE**
> 
> Directly using **getContext** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain a [UIContext](arkts-apis-uicontext-uicontext.md) instance using **getUIContext()**, and then obtain the associated **Context** object using [getHostContext](arkts-apis-uicontext-uicontext.md#gethostcontext12).

**Example**

Load a page by calling **windowStage.loadContent** in the UIAbility.

```ts
// EntryAbility.ets
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
  }

  onDestroy() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }

  onWindowStageDestroy() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
  }

  onForeground() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onBackground() {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
  }
}
```
In the **Index.ets** file, you can use the **getContext** API to obtain the context. In this example, the returned context type is **UIAbilityContext**.

<!--deprecated_code_no_check-->
```ts
//pages/Index.ets
@Entry
@Component
struct Index {
  @State message: string = 'Hello World'

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            // You are advised to use this.getUIContext().getHostContext().
            let context: Context = getContext(this) as Context;
            console.info('CacheDir:' + context.cacheDir);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
