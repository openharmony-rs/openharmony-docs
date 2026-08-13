# @ohos.data.commonType

/*
 Copyright (c) 2023 Huawei Device Co., Ltd.
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


**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace commonType--><!--Device-unnamed-declare namespace commonType-End-->

**系统能力：** SystemCapability.DistributedDataManager.CommonType

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [Asset](arkts-arkdata-commontype-asset-i.md) | 记录资产附件（文件、图片、视频等类型文件）的相关信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AssetStatus](arkts-arkdata-commontype-assetstatus-e.md) | 描述资产附件的状态枚举。请使用枚举名称而非枚举值。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Assets](arkts-arkdata-commontype-assets-t.md) | 表示Asset类型的数组。 |
| [ValueType](arkts-arkdata-commontype-valuetype-t.md) | 用于表示允许的数据字段类型，接口参数具体类型根据其功能而定。。 |
| [ValuesBucket](arkts-arkdata-commontype-valuesbucket-t.md) | 用于存储键值对的类型。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。 |

