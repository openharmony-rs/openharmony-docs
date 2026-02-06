# 通过openLink拉起系统应用/三方应用

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

## 场景介绍

开发者在使用[openLink](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)接口拉起系统应用或三方应用时，常常遇到不知道目标应用URL（应用链接）配置信息的问题。本文档将介绍如何获取目标应用的URL信息，并提供完整的拉起示例。

## 获取目标应用的URL信息

使用hdc（HarmonyOS Device Connector）命令行工具，可以获取设备上已安装应用的详细配置信息，包括bundleName、abilityName以及支持的URL Scheme等。这是获取三方应用URL信息最直接有效的方法。

### 步骤1：获取应用的bundleName

通过以下命令查看设备上已安装的所有应用列表，找到目标应用的包名：

```bash
hdc shell bm dump -a
```

该命令会列出设备上所有已安装应用的基本信息，包括应用名称和bundleName。例如查找钉钉应用：

```bash
# 执行命令查看所有应用
hdc shell bm dump -a

# 输出示例（部分）：
# ...
# AppLabel: 钉钉
# BundleName: com.dingtalk.hmos
# ...
```

从输出中找到目标应用的bundleName，例如钉钉应用的bundleName为 `com.dingtalk.hmos`。

### 步骤2：获取应用的详细配置信息

使用获取到的bundleName，查看该应用的详细配置信息：

```bash
hdc shell bm dump -n com.dingtalk.hmos
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
        "dingtalk.want.action.dingtalk",
      ],
      "domainVerify": false,
      "entities": [
        "entity.system.home"
      ],
      "permissions": [],
      "uris": [
        {
          "host": "dingtalkclient",
          "linkFeature": "",
          "path": "page/link",
          "maxFileSupported": 0,
          "path": "",
          "pathRegex": "(?!(page/videoConfFromSystemCalendar)).+",
          "pathStartWith": "",
          "port": "",
          "scheme": "dingtalk",
          "type": "",
          "utd": ""
        }
      ]
    }
  ]
}
```

从配置信息中可以提取出：
- **scheme**: `dingtalk`
- **host**: `dingtalkclient`
- **path**: `page/videoConfFromSystemCalendar`

### 步骤3：拼接应用链接

根据获取到的配置信息，按照URL格式拼接应用链接：

```
scheme://host:port/path
```

以钉钉应用为例：
```
dingtalk://dingtalkclient/page/videoConfFromSystemCalendar
```

完整的拼接示例：

| 配置项 | 值 |
|--------|---|
| scheme | `dingtalk` |
| host | `dingtalkclient` |
| port | 未指定（可选） |
| path | `page/videoConfFromSystemCalendar` |
| **拼接结果** | `dingtalk://dingtalkclient/page/videoConfFromSystemCalendar` |


### 其他常用应用示例

使用相同的方法，可以获取其他三方应用的URL配置信息：

```bash
# 获取微信应用配置
hdc shell bm dump -n com.tencent.wechat
# 输出为：weixin://

# 获取支付宝应用配置
hdc shell bm dump -n com.alipay.mobile.client
# 输出为：alipays://
```

> **说明：**
> - 不同应用的bundleName和URL配置可能因版本不同而有所变化
> - 建议在实际使用前，通过hdc命令确认目标应用的最新配置信息
> - 如果应用未配置skills中的uris字段，则不支持通过Deep Linking方式拉起


## 通过openLink拉起应用

### 基本用法

使用[openLink](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)接口拉起应用的基本步骤如下：


#### 拉起三方应用

以下是一个完整的示例，演示如何通过openLink接口拉起钉钉应用。

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
        let link: string = "dingtalk://dingtalkclient/page/videoConfFromSystemCalendar";

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

## 常见错误码

| 错误码 | 说明 | 解决方案 |
|--------|------|----------|
| 16000001 | 应用未安装 | 提示用户安装目标应用 |
| 16000007 | URI格式错误 | 检查URL格式是否正确 |
| 16000050 | 系统内部错误 | 重试或检查系统状态 |

## 注意事项

1. **URL配置验证**：在使用三方应用的URL之前，务必验证其正确性，避免因URL错误导致拉起失败。

2. **应用安装检测**：在拉起三方应用前，建议先检测应用是否已安装。

3. **appLinkingOnly参数**：
   - 设置为`false`（默认）：优先使用App Linking，失败时降级到Deep Linking
   - 设置为`true`：仅使用App Linking，适用于需要严格域名校验的场景

## 相关文档

- [使用Deep Linking实现应用间跳转](deep-linking-startup.md)
- [应用链接说明](app-uri-config.md)
- [openLink接口文档](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)
- [OpenLinkOptions接口文档](../reference/apis-ability-kit/js-apis-app-ability-openLinkOptions.md)
