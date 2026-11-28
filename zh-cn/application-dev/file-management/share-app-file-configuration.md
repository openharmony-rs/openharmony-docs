# 应用可授权沙箱目录范围配置
<!--Kit: Core File Kit-->
<!--Subsystem: Security-->
<!--Owner: @renzehua-->
<!--Designer: @renzehua; @huangjieliang; @zhanganxiang-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

## 配置沙箱分享范围

从API版本23开始，系统支持配置沙箱分享范围。开发者配置后，在应用[将文件授权给其他应用访问](share-app-file.md)时（含用户分享场景和应用自身发起的授权场景），都将与配置范围进行比对，仅配置范围内的文件授权会被允许，防止应用敏感数据泄露。该配置在应用安装时写入系统，仅在手机（Phone）、平板（Tablet）上生效。

> **说明：**
>
> 从API版本26.0.0开始，可配置的分享范围扩大，请开发者按照最新范围进行配置，下述配置指导配套版本为26.0.0。
>
> 若未配置分享范围（scopes），系统将不进行范围比对，默认允许对应文件URI的分享。
>
> 即使应用不需要分享文件，也建议配置分享范围——配置后默认行为从"全放开"变为"仅配置范围内可分享"，可配置一个不对应实际分享路径的符合格式要求的路径来生效限制，使所有分享行为被拦截，起到防护作用。

1. 在应用模块级配置文件[src/main/module.json5](../quick-start/module-configuration-file.md)的module标签中添加shareFiles标签：

   **shareFiles标签**

   ``` JSON5
   {
     "module": {
       // ...
       "shareFiles": "$profile:share_files", // 资源配置，指向profile下面定义的配置文件share_files.json
       // ...
     }
   }
   ```

2. 在开发视图的resources/base/profile目录中定义资源配置文件（文件名默认share_files.json，可改为符合系统命名规则的其他名称，但需与shareFiles标签配置的文件名一致），在scopes标签中配置分享路径及权限。

scopes标签的字段说明：

| 属性名称 | 含义 | 数据类型 | 必填 |
| -------- | -------- | -------- | -------- |
| path | 分享路径配置，路径第一级支持el1~el5级别加密目录，第二级仅支持下列目录：<br/>- `base`<br/>- `distributedfiles`<br/>- `cloud`<br/>详细限制见[路径限制说明](#路径限制说明)。<br/>**起始版本：** 26.0.0  | string | scopes存在时必填 |
| permission | 分享路径权限。支持的取值如下：<br/>- `r`：只读。<br/>- `r+w`：读写。<br/>**起始版本：** 23 | string | scopes存在时必填 |

### 路径限制说明

1. 路径深度限制：
   - 单路径最浅需配置2级，如/el2/base。
   - 单路径最深可配置10级，如/el2/base/files/level4/level5/level6/level7/level8/level9/level10。

2. 路径数量限制：
   - 配置的路径不可重复，最多可配置20条路径。

3. 路径格式限制：
   - 必须以/开头，不允许有'.'、'..'、'\0'字符，不允许以'/'结尾。

4. 父子目录限制：
   - 若某路径已配置，则不允许再配置其子目录。
   - 如已配置/el2/base/files，则不允许再配置/el2/base/files/documents（已配置路径的子目录），允许配置/el2/base/cache（与已配置路径无父子关系）。

配置分享范围的share_files.json示例：

``` json
{
  "share_files": {
    "scopes": [
      {
        "path": "/el2/base/files",
        "permission": "r+w"
      },
      {
        "path": "/el3/distributedfiles/files/tmp",
        "permission": "r+w"
      }
    ]
  }
}
```

> **说明：**
>
> 应用更新时如涉及配置变更，将依据新配置进行管控，已持久化的授权不满足新配置时将无法被激活，已分享的临时授权不受影响。

### 错误定位

当分享行为与预期不符时，可按以下阶段排查配置问题。

**开发、打包阶段**

DevEco Studio与打包工具会对scopes的格式与取值进行静态校验（路径层级、数量、父子目录、字符限制等）。校验不通过时构建直接报错，请根据构建报错信息修正配置文件后重试。

**运行阶段**

分享配置在应用安装或更新时由系统载入。为保持与旧版本系统的兼容性，任一路径不符合路径限制时，系统会自动清除该应用的全部已配置路径，分享行为回到未配置状态。如果分享行为被拦截或者拦截不生效，可通过hdc过滤沙箱管理服务的系统日志，确认具体失败原因：

``` bash
hdc shell hilog | grep SandboxManagerShare
```

| 日志关键字 | 原因及处理建议 |
| ---------- | ---------- |
| TransAndSetToMapInner failed for bundle xxx, invalid path: yyy | 配置中的某条路径不合法，日志中会指明具体不合法的路径，请修正配置后重新打包安装，否则该应用全部已配置路径将失效，不具备拦截作用。 |
| TransAndSetToMapInner failed for bundle xxx, exceeds limit | 路径数超过20条上限，请精简配置。 |
| json parse error | json格式不合法，检查语法（多余逗号、引号缺失等）。 |
| json size exceeds limit | 配置超过大小限制（5MB），精简。 |
| scopes is not an array / path is not a string / permission is not a string | scopes结构或字段类型错误，检查share_files.json格式。 |
| path not allowed to set policy | 分享请求被拦截（路径不在scopes范围内或权限超出）。日志中路径被脱敏，请对照应用分享请求与scopes配置进行判断，调整分享路径或扩大scopes范围及权限。 |
