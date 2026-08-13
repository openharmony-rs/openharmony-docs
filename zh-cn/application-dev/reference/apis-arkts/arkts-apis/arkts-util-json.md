# @ohos.util.json

/*
 Copyright (c) 2024 Huawei Device Co., Ltd.
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


**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare namespace json--><!--Device-unnamed-declare namespace json-End-->

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [has](arkts-arkts-json-has-f.md#has) | 检查ArkTS对象是否包含某种属性，可用于[JSON.parse](arkts-arkts-json-parse-f.md#parse)解析JSON字符串之后。 has接口仅支持最外层为字典形式（即大括号而非中括号包围）的合法JSON串，传入非字典形式的对象时无法正确判断属性是否存在。 |
| [parse](arkts-arkts-json-parse-f.md#parse) | 解析JSON字符串生成ArkTS对象或null。解析过程中，每个键值对按从最内层到最外层的顺序依次经过reviver函数处理，返回值替换原始值； 当传入ParseOptions指定BigIntMode时，符合条件的整数将被解析为BigInt；当入参字符串为'null'时返回null。 |
| [remove](arkts-arkts-json-remove-f.md#remove) | 从ArkTS对象中删除某种属性，可用于[JSON.parse](arkts-arkts-json-parse-f.md#parse)解析JSON字符串之后，如清理敏感字段、移除冗余数据等场景。 JSON.remove接口仅支持最外层为字典形式（即大括号而非中括号包围）的合法JSON串。 |
| [stringify](arkts-arkts-json-stringify-f.md#stringify) | 该方法将一个ArkTS对象或数组转换为JSON字符串，支持线性容器的转换，不支持非线性容器（传入非线性容器时无法正确序列化）。 |
| [stringify](arkts-arkts-json-stringify-f.md#stringify) | 该方法将一个ArkTS对象或数组转换为JSON字符串，支持线性容器的转换，不支持非线性容器。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ParseOptions](arkts-arkts-json-parseoptions-i.md) | 解析的选项，可定义处理BigInt的模式。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BigIntMode](arkts-arkts-json-bigintmode-e.md) | 定义处理BigInt的模式。由于JSON规范不支持BigInt类型，且Number精度范围为-(2^53-1)到(2^53-1)，本模块提供三种模式以适配不同场景的整数精度需求。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Transformer](arkts-arkts-json-transformer-t.md) | 用于转换结果的函数类型。 作为[JSON.parse](arkts-arkts-json-parse-f.md#parse)函数的参数时，解析结果中的每个键值对按深度优先顺序（从最内层节点开始，逐层向外）依次调用此函数， this指向当前键值对所属的对象，返回值替换原始值，若返回undefined则该属性将被删除。 作为[JSON.stringify](arkts-arkts-json-stringify-f.md#stringify)函数的参数时， 序列化引擎会按从外到内的顺序对每个属性调用该函数处理，this指向当前属性所属的对象，返回值作为序列化结果。 |

