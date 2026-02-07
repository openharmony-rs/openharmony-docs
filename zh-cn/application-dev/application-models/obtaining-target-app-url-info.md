# 获取被拉起方应用的URL信息

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

## 场景介绍

开发者在使用[openLink](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)接口拉起系统应用或三方应用时，需要明确目标应用的信息。本文将介绍如何获取目标应用的URL信息，并提供完整的拉起示例。

## 环境要求

在使用本工具前，开发者需要先获取hdc工具，执行hdc shell。

## 操作步骤

1. 获取当前设备上已安装应用的bundleName。

使用hdc命令行工具，可以获取设备上已安装应用的详细配置信息，包括bundleName、abilityName以及支持的URL Scheme等。这是获取三方应用URL信息最直接有效的方法。


通过以下命令查看设备上已安装的所有应用列表，找到目标应用的包名：

```bash
hdc shell bm dump -a
```

该命令会列出设备上所有已安装应用的基本信息，包括应用名称和bundleName。例如查找应用市场应用：

```bash
# 执行命令查看所有应用
hdc shell bm dump -a

# 输出示例（部分）：
# ...
# BundleName: com.huawei.hmsapp.appgallery
# ...
```

从输出中找到目标应用的bundleName，例如设置应用的bundleName为 `com.huawei.hmsapp.appgallery`。

2. 获取应用的详细配置信息。

```bash
hdc shell bm dump -n com.huawei.hmsapp.appgallery
```

该命令会输出应用的完整配置信息，包括abilities、skills、uris等配置。

在输出中查找 `skills` 部分，可以看到该应用支持的URL Scheme配置：

```json5
# 输出示例（skills部分）：
{
  "skills": [
    {
      "actions": [
        "action.system.home",
        "ohos.want.action.viewData",
        "ohos.want.action.appdetail"
      ],
      "domainVerify": false,
      "entities": [
        "entity.system.home"
      ],
      "permissions": [],
      "uris": [
        {
          "host": "appgallery.huawei.com",
          "linkFeature": "",
          "maxFileSupported": 0,
          "path": "",
          "pathRegex": "",
          "pathStartWith": "",
          "port": "",
          "scheme": "store",
          "type": "",
          "utd": ""
        }
      ]
    }
  ]
}
```

从配置信息中可以提取出：
- **scheme**: `store`
- **host**: `appgallery.huawei.com`
- **path**: ``

3. 将scheme、host和path拼接生成URL信息。

根据获取到的配置信息，按照URL格式拼接应用链接：

```
scheme://host:port/path
```

以应用市场为例：
```
store://appgallery.huawei.com
```

完整的拼接示例：

| 配置项 | 值 |
|--------|---|
| scheme | `store` |
| host | `appgallery.huawei.com` |
| port | 未指定（可选） |
| path | 未指定（可选） |
| **拼接结果** | `store://appgallery.huawei.com` |


其他常用应用示例

使用相同的方法，可以获取其他应用的URL配置信息：

```bash
# 获取视频应用配置
hdc shell bm dump -n com.huawei.hmsapp.himovie
# 输出为：himovie://com.huawei.hmsapp.himovie

# 获取联系人应用配置
hdc shell bm dump -n com.ohos.contacts
# 输出为：tel://
```

> **说明：**
> - 不同应用的bundleName和URL配置可能因版本不同而有所变化
> - 建议在实际使用前，通过hdc命令确认目标应用的最新配置信息
> - 如果应用未配置skills中的uris字段，则不支持通过Deep Linking方式拉起


4. 调试验证

使用[openLink](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)接口拉起应用的基本步骤如下：

以下为通过openLink接口拉起应用市场的完整示例。在实现时请注意：

- **URL配置验证**：在使用目标应用的URL之前，务必验证其正确性，避免因URL错误导致拉起失败。
- **应用安装检测**：在拉起目标应用前，建议先检测应用是否已安装。

**Index.ets示例代码如下：**
```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { GlobalContext } from '../common/GlobalContext';

@Entry
@Component
struct Index {
  build() {
    Button('start link', { type: ButtonType.Capsule, stateEffect: true })
      .width('87%')
      .height('5%')
      .margin({ bottom: '12vp' })
      .onClick(() => {
        let context = GlobalContext.getContext();
        let link: string = "store://appgallery.huawei.com";

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
- [openLink接口文档](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)
- [OpenLinkOptions接口文档](../reference/apis-ability-kit/js-apis-app-ability-openLinkOptions.md)
