# @ohos.dlpSetDlpFeature(设置数据防泄漏入口)

/*
 Copyright (c) 2026 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License"),
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace dlpSetDlpFeature--><!--Device-unnamed-declare namespace dlpSetDlpFeature-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [setDlpFeature](arkts-dataprotection-dlpsetdlpfeature-setdlpfeature-f-sys.md#setDlpFeature) | 设置DLP特性开关状态。使用Promise异步回调。调用成功后，DLP特性开关将设置为指定状态，系统将根据该状态启用或禁用DLP保护功能。 当特性开关处于开启状态时，右键单击支持加密的文件，右键菜单中会显示“加密保护”选项。可加密类型包括：.txt，.pdf，.xls，.xlsx，.ppt，.pptx，.doc，.docx。 企业策略开启或关闭数据防泄漏功能时使用此接口。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DLPFeatureInfo](arkts-dataprotection-dlpsetdlpfeature-dlpfeatureinfo-i-sys.md) | DLP特性开关的状态信息。 |
| [StatusInfoResult](arkts-dataprotection-dlpsetdlpfeature-statusinforesult-i-sys.md) | DLP特性开关状态设置的结果信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DlpFeatureStatus](arkts-dataprotection-dlpsetdlpfeature-dlpfeaturestatus-e-sys.md) | DLP特性开关状态的枚举。 |
<!--DelEnd-->

