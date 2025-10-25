# getContext
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

The **getContext** API enables you to obtain the context of the ability (either [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) or [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)) on the current page.

> **NOTE**
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use [getHostContext](arkts-apis-uicontext-uicontext.md#gethostcontext12) in [UIContext](arkts-apis-uicontext-uicontext.md) instead.
> - This API applies only to the stage model.

## getContext<sup>(deprecated)</sup>

getContext(component?: Object):Context

Obtains the **Context** object associated with an ability on the page.

> **NOTE**
> 
> This API is deprecated since API version 18. You are advised to use [getHostContext](arkts-apis-uicontext-uicontext.md#gethostcontext12) in [UIContext](arkts-apis-uicontext-uicontext.md) instead.
>
> Since API version 12, you can use the [getHostContext](arkts-apis-uicontext-uicontext.md#gethostcontext12) API in [UIContext](arkts-apis-uicontext-uicontext.md), which ensures that the time picker dialog box is shown in the intended UI instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type         | Mandatory| Description                            |
| ------ | ----------- | ---- | ------------------------------- |
| component  | Object | No  | Ability instance. If no component is passed in or the passed-in parameter type is invalid, the default context is returned. The default context is the context obtained by tracing the call chain of the API. If this API is used in an asynchronous callback or not initially called on the current page, the context of the instance may fail to be traced. In this case, **undefined** is returned.            |

**Return value**

| Type| Description                            |
| ------ | ------------------------------- |
| [Context](#context)  | Context of the ability. The context type depends on the ability type. For example, if this API is called on a page of the UIAbility, the return value type is UIAbilityContext; if this API is called on a page of the ExtensionAbility, the return value type is ExtensionContext.   |

## Context

type Context = Context

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Type| Description                            |
| ------ | ------------------------------- |
| [Context](../../application-models/application-context-stage.md)  | Context of the ability. The context type depends on the ability type. For example, if this API is called on a page of the UIAbility, the return value type is UIAbilityContext; if this API is called on a page of the ExtensionAbility, the return value type is ExtensionContext.   |

> **NOTE**
> 
> Directly using **getContext** can lead to the issue of [ambiguous UI context](../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain a **UIContext** instance using **getUIContext()**, and then obtain the associated **Context** object using [getHostContext](arkts-apis-uicontext-uicontext.md#gethostcontext12).

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
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
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
In **Index.ets**, **getContext** is used to obtain the context. In this example, the return value type is UIAbilityContext.

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
            console.info("CacheDir:" + context.cacheDir);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
