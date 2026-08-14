# @ohos.convertxml

/*
 Copyright (c) 2021-2022 Huawei Device Co., Ltd.
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


**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-unnamed-declare namespace xml--><!--Device-unnamed-declare namespace xml-End-->

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ConvertXML](arkts-arkts-xml-convertxml-c.md) | ConvertXML类提供将XML文本转换为JavaScript对象的能力。 推荐使用[fastConvertToJSObject&lt;sup&gt;14+&lt;/sup&gt;](arkts-arkts-xml-convertxml-c.md#fastConvertToJSObject)进行常规XML文本解析， 当单元素文本内容超过10M时推荐使用[largeConvertToJSObject&lt;sup&gt;23+&lt;/sup&gt;](arkts-arkts-xml-convertxml-c.md#largeConvertToJSObject)。 已废弃的[convertToJSObject](arkts-arkts-xml-convertxml-c.md#convertToJSObject)和[convert](arkts-arkts-xml-convertxml-c.md#convert)方法不再维护， 建议使用[fastConvertToJSObject&lt;sup&gt;14+&lt;/sup&gt;](arkts-arkts-xml-convertxml-c.md#fastConvertToJSObject)替代。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConvertOptions](arkts-arkts-xml-convertoptions-i.md) | 转换选项，用于自定义XML到JavaScript对象的转换行为，如控制是否修剪空白字符、是否忽略特定组件（声明、指令、属性、注释、CDATA、Doctype和文本等）， 以及指定输出对象中各类型组件的属性键名称。 |

