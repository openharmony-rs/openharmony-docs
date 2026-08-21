# StartAbilityParameter

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

StartAbilityParameter定义启动Ability的参数，可以作为入参调用[startAbility](js-apis-ability-featureAbility.md#featureabilitystartability)启动指定的Ability。其中，want用于指定启动目标，abilityStartSettings用于配置窗口模式、显示ID、abilityBounds等特殊启动属性。

> **说明：**
>
> 本模块仅支持ArkTS-Dyn。
>
> 本接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 此接口仅可在FA模型下使用。

## 导入模块

```ts
import ability from '@ohos.ability.ability';
```

## 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

| 名称               |   类型   | 只读  | 可选   | 说明                                 |
| ----------------- | -------- | ---- | ---- | -------------------------------------- |
| want                | [Want](js-apis-app-ability-want.md)| 否  | 否  | 启动Ability的want信息。<br>**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。<br>**ArkTS-Dyn起始版本：** 6 |
| abilityStartSetting | { [key: string]: any } | 否  | 是  | 启动Ability的特殊属性，用于配置窗口显示等相关参数。不配置时不应用特殊启动属性。支持abilityBounds、windowMode、displayId等配置项。<br>**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。<br/>**ArkTS-Dyn起始版本：** 6 |
| abilityStartSettings<sup>11+<sup> | Record\<string, Object> | 否  | 是  | 启动Ability的特殊属性（如abilityBounds、windowMode、displayId等）。不配置时不应用特殊启动属性。推荐使用该属性替代abilityStartSetting，设置该属性后，abilityStartSetting不再生效。<br>**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。<br/>**ArkTS-Dyn起始版本：** 11 |

**示例：**

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
    // 启动指定的Ability
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