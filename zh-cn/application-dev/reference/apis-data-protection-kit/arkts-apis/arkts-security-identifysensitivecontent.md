# @ohos.security.identifySensitiveContent(Identify sensitive file)

/*
 Copyright (c) 2025 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

<!--Device-unnamed-declare namespace identifySensitiveContent--><!--Device-unnamed-declare namespace identifySensitiveContent-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [scanFile](arkts-dataprotection-identifysensitivecontent-scanfile-f.md#scanFile) | 根据设置的策略，识别指定文件中的敏感内容，返回识别的结果数组，包含匹配的敏感标签、匹配内容及匹配数量。使用Promise异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [MatchResult](arkts-dataprotection-identifysensitivecontent-matchresult-i.md) | 表示敏感内容的识别结果。 |
| [Policy](arkts-dataprotection-identifysensitivecontent-policy-i.md) | 定义敏感内容识别策略。 单个策略内，关键字与正则表达式为顺序组合关系，实行两级匹配：首先进行关键字匹配，若命中，则仅在该关键字匹配位置的前后50字节窗口内，进行正则表达式匹配。 若只设置关键字，则仅进行关键字匹配。若只设置正则表达式，则仅进行正则表达式匹配。 多个Policy策略之间独立，扫描时会分别应用每个策略。 sensitiveLabel用于标记匹配结果，便于识别具体匹配的策略。 |

