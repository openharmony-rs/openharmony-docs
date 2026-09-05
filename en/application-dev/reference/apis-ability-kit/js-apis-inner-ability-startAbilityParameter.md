# StartAbilityParameter

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9b45198dbdb6f53f8bf0896d62425626f2442690 translatedAt=2026-09-03T11:30:47.176Z pushedAt=2026-09-05T10:47:30.634Z -->

StartAbilityParameter defines the parameters for starting an ability. It can be used as an input parameter of [startAbility](js-apis-ability-featureAbility.md#featureabilitystartability) to start the specified ability. Among them, **want** specifies the target to start, and **abilityStartSettings** configures special startup attributes such as the window mode, display ID, and abilityBounds.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> The APIs of this module can be used only in the FA model.

## Modules to Import

```ts
import ability from '@ohos.ability.ability';
```

## Attributes

**System capability**: SystemCapability.Ability.AbilityRuntime.FAModel

| Name              |   Type  | Read-Only | Optional  | Description                                |
| ----------------- | -------- | ---- | ---- | -------------------------------------- |
| want                | [Want](js-apis-app-ability-want.md)| No | No | Want information about the target ability.                    |
| abilityStartSetting | { [key: string]: any } | No  | Yes  | Special attributes for starting an Ability, used to configure window display and other related parameters. If not configured, no special startup attributes are applied. Supports configuration items such as abilityBounds, windowMode, and displayId. |
| abilityStartSettings<sup>11+</sup> | Record\<string, Object> | No  | Yes  | Special attributes for starting an Ability (such as abilityBounds, windowMode, and displayId). If not configured, no special startup attributes are applied. It is recommended to use this attribute instead of abilityStartSetting. After this attribute is set, abilityStartSetting no longer takes effect. |

**Example**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import Want from '@ohos.app.ability.Want';

let want: Want = {
    bundleName: 'com.example.abilityStartSettingApp2',
    abilityName: 'com.example.abilityStartSettingApp.EntryAbility',
};

let startAbilityParameter: ability.StartAbilityParameter = {
    want : want,
    abilityStartSettings : {
        abilityBounds : [100,200,300,400],
        windowMode :
        featureAbility.AbilityWindowConfiguration.WINDOW_MODE_UNDEFINED,
        displayId : 1,
    }
};

try {
    // Start the specified ability.
    featureAbility.startAbility(startAbilityParameter, (error, data) => {
        if (error && error.code !== 0) {
            console.error(`startAbility fail, error: ${JSON.stringify(error)}`);
        } else {
            console.info(`startAbility success, data: ${JSON.stringify(data)}`);
        }
    });
} catch(error) {
    console.error(`startAbility error: ${JSON.stringify(error)}`);
}
```