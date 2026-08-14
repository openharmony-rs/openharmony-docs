# @ohos.fontManager

/*
 Copyright (c) 2025 Huawei Device Co., Ltd.
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


**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace fontManager--><!--Device-unnamed-declare namespace fontManager-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [dataMigration](arkts-localization-fontmanager-datamigration-f-sys.md#dataMigration) | 设备升级时使用的数据迁移接口，用于启动迁移任务，通过回调函数实时反馈迁移进度和结果。 |
| [installFont](arkts-localization-fontmanager-installfont-f-sys.md#installFont) | 将指定路径下的字体文件安装到系统字体库中。使用Promise异步回调。 安装成功后，应用可以通过字体名称使用该字体。 |
| [uninstallFont](arkts-localization-fontmanager-uninstallfont-f-sys.md#uninstallFont) | 根据字体名称从系统字体库中卸载已安装的字体文件。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataMigrationCallback](arkts-localization-fontmanager-datamigrationcallback-i-sys.md) | 数据迁移时使用的回调接口类型，定义了数据迁移过程中的回调方法。开发者需实现该接口的所有方法，以接收迁移过程中的心跳通知、进度更新和最终结果。 |
| [DataMigrationProgress](arkts-localization-fontmanager-datamigrationprogress-i-sys.md) | 描述数据迁移的进度信息，包含进度百分比和预估剩余时间。该接口为数据迁移回调onProgress方法的参数类型。 |
<!--DelEnd-->

