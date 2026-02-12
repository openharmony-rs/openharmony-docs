# 获取目标应用的URL信息

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

## 场景介绍

开发者在使用[uiAbilityContext.openLink](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)接口拉起目标应用时，需要传入目标应用的URL信息。本章节主要介绍如何获取目标应用的URL信息。

假设目标应用的UIAbility的[module.json5](../quick-start/app-configuration-file.md)配置信息如下：

    ```JSON5
    {
      "name": "EntryAbility",
      "srcEntry": "./ets/entryability/EntryAbility.ets",
      "icon": "$media:layered_image",
      "label": "$string:EntryAbility_label",
      // ···
      "skills": [
          "uris": [
            {
              "scheme": "demo",
              "host": "www.example.com",
              "path": "path1"
              // ...
            }
          ],
          "domainVerify": false,
          // ...
        ]
      }
    ``` 

## 环境要求

开发者需要先获取[hdc工具](../dfx/hdc.md)，执行hdc shell。

## 操作步骤

1. 使用bm工具，获取目标应用的bundleName。

  （1）获取当前设备上所有已安装应用的bundleName，保存结果。
    ```bash
    hdc shell bm dump -a
    ```

  （2）安装目标应用。

  （3）再次获取当前设备上所有已安装应用的bundleName，并与之前保存的结果进行对比。新增的bundleName即为`com.example.myapplication`。

2. 根据bundleName，获取应用的uris信息。

  （1）使用bm工具，获取应用的完整配置信息，包括abilities、skills、uris等配置。
    
    ```bash
    hdc shell bm dump -n com.example.myapplication
    ```

  （2）通过查看输出中的`skills`部分，获取应用支持的URL Scheme配置。

    ```json5
    // 输出示例（skills部分）：
    {
      "skills": [
        {
          "actions": [
            "ohos.want.action.viewData"
          ],
          "domainVerify": false,
          "entities": [
            "entity.system.browsable"
          ],
          "permissions": [],
          "uris": [
            {
              "host": "www.example.com",
              "linkFeature": "",
              "maxFileSupported": 0,
              "path": "path1",
              "pathRegex": "",
              "pathStartWith": "",
              "port": "",
              "scheme": "demo",
              "type": "",
              "utd": ""
            }
          ]
        }
      ]
    }
    ```

3. 将scheme、host和path拼接生成URL信息。

    根据获取到的配置信息，按照URL格式拼接应用链接：

    ```
    scheme://host:port/path
    ```

    以目标应用为例：
    ```
    demo://www.example.com/path1
    ```

    完整的拼接示例：

    | 配置项 | 值 |
    |--------|---|
    | scheme | `demo` |
    | host | `www.example.com` |
    | port | 未指定（可选） |
    | path | `path1` |
    | 拼接结果 | `demo://www.example.com/path1` |


    > **说明：**
    >
    > - 不同应用的bundleName和URL配置可能因版本不同而有所变化。
    > - 建议在实际使用前，通过hdc命令确认目标应用的最新配置信息。
    > - 如果应用未配置skills中的uris字段，则不支持通过Deep Linking方式拉起。

4. 使用Deep Linking方式拉起目标应用

    以下为通过[uiAbilityContext.openLink](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)接口拉起目标应用的完整示例。在实现时请注意：

    - URL配置验证：在使用目标应用的URL之前，务必验证其正确性，避免因URL错误导致拉起失败。
    - 应用安装检测：在拉起目标应用前，建议先检测应用是否已安装。

    <!-- @[start Deep Linking](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/    ObtainingTargetAppUrlInfo/entry/src/main/ets/pages/Index.ets) -->

    ```ts
    // Index.ets示例代码如下：
    import { common } from '@kit.AbilityKit'
    import { hilog } from '@kit.PerformanceAnalysisKit';
    import { BusinessError } from '@kit.BasicServicesKit';

    @Entry
    @Component
    struct Index {
      build() {
        Button('openLink', { type: ButtonType.Capsule, stateEffect: true })
          .width('87%')
          .height('5%')
          .margin({ bottom: '12vp' })
          .onClick(() => {
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let link: string = 'demo://www.example.com/path1';

            context.openLink(link, { appLinkingOnly: false })
              .then(() => {
                hilog.info(0x0000, 'testTag', `Succeeded in opening link.`);
              })
              .catch((error: BusinessError) => {
                hilog.error(0x0000, 'testTag', `Failed to open link, code: ${error.code}, message: ${error.message}`);
              });
          })
      }
    }
    ```

## 相关文档

- [使用Deep Linking实现应用间跳转](deep-linking-startup.md)
- [应用链接说明](app-uri-config.md)
- [OpenLinkOptions接口文档](../reference/apis-ability-kit/js-apis-app-ability-openLinkOptions.md)
