# AbilityStageContext

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T11:37:45.766Z pushedAt=2026-09-05T10:47:30.660Z -->

AbilityStageContext is the context environment of an ability stage and inherits from [Context](js-apis-inner-application-context.md). AbilityStageContext provides the capability to access resources specific to an ability stage. It is applicable to scenarios where module information and configuration need to be accessed during the ability stage lifecycle, helping developers quickly obtain module information and configuration.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version. 
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## Properties

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| currentHapModuleInfo | [HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md) | No | No | HapModuleInfo object corresponding to the AbilityStage, which can be used to obtain information such as the name and path of the current module. |
| config | [Configuration](js-apis-app-ability-configuration.md) | No | No | Configuration object. |
| launchElement<sup>24+</sup> | [ElementName](js-apis-bundleManager-elementName.md) | No | Yes | Element name information when the AbilityStage is created.<br>**Atomic service API**: Since API version 24, this API is supported in atomic services. |

**Example**

```ts
import { AbilityStage } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAbilityStage extends AbilityStage {
  onCreate() {
    // Obtain the AbilityStageContext context.
    let abilityStageContext = this.context;
    // Obtain the current module name.
    let name = abilityStageContext.currentHapModuleInfo.name;
    // Obtain the current language.
    let language = abilityStageContext.config.language;
    // Obtain the ElementName when the AbilityStage is created.
    let elementName = abilityStageContext.launchElement;
    if (elementName) {
      hilog.info(0x0000, 'testTag', 'bundleName: %{public}s', elementName.bundleName);
      hilog.info(0x0000, 'testTag', 'moduleName: %{public}s', elementName.moduleName);
      hilog.info(0x0000, 'testTag', 'abilityName: %{public}s', elementName.abilityName);
    }
  }
}
```