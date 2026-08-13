# @ohos.data.uniformTypeDescriptor(标准化数据定义与描述)

/*
 Copyright (c) 2023-2026 Huawei Device Co., Ltd.
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

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace uniformTypeDescriptor--><!--Device-unnamed-declare namespace uniformTypeDescriptor-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getTypeDescriptor](arkts-arkdata-uniformtypedescriptor-gettypedescriptor-f.md#getTypeDescriptor) | 按给定的标准化数据类型ID查询并返回对应的标准化数据类型描述类对象。 |
| [getTypeDescriptor](arkts-arkdata-uniformtypedescriptor-gettypedescriptor-f.md#getTypeDescriptor) | 按给定的标准化数据类型ID查询并返回对应的标准化数据类型描述类对象。 |
| [getUniformDataTypeByFilenameExtension](arkts-arkdata-uniformtypedescriptor-getuniformdatatypebyfilenameextension-f.md#getUniformDataTypeByFilenameExtension) | 根据给定的文件后缀名和所归属的标准化数据类型查询标准化数据类型ID，若有多个符合条件的标准化数据类型ID，则返回第一个。 |
| [getUniformDataTypeByMIMEType](arkts-arkdata-uniformtypedescriptor-getuniformdatatypebymimetype-f.md#getUniformDataTypeByMIMEType) | 根据给定的MIME类型和所归属的标准化数据类型查询标准化数据类型ID，若有多个符合条件的标准化数据类型ID，则返回第一个。 |
| [getUniformDataTypesByFilenameExtension](arkts-arkdata-uniformtypedescriptor-getuniformdatatypesbyfilenameextension-f.md#getUniformDataTypesByFilenameExtension) | 根据给定的文件后缀名和所归属的标准化数据类型查询标准化数据类型ID列表。 |
| [getUniformDataTypesByMIMEType](arkts-arkdata-uniformtypedescriptor-getuniformdatatypesbymimetype-f.md#getUniformDataTypesByMIMEType) | 根据给定的MIME类型和所归属的标准化数据类型查询标准化数据类型ID列表。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [registerTypeDescriptors](arkts-arkdata-uniformtypedescriptor-registertypedescriptors-f-sys.md#registerTypeDescriptors) | 注册一组标准化数据类型到系统中。使用Promise异步回调。注册成功后，标准化数据类型将被系统管理，可通过UDMF框架在其他应用或设备间共享和识别。 |
| [unregisterTypeDescriptors](arkts-arkdata-uniformtypedescriptor-unregistertypedescriptors-f-sys.md#unregisterTypeDescriptors) | 从系统中注销一个或多个标准化数据类型。使用Promise异步回调。注销后，该数据类型将不再被系统识别，依赖该数据类型的数据可能无法正常处理，请确保在注销前已清理相关数据依赖。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [TypeDescriptor](arkts-arkdata-uniformtypedescriptor-typedescriptor-c.md) | 标准化数据类型的描述类，它包含了一些属性和方法用于描述标准化数据类型自身以及和其他标准化数据类型之间的归属与层级关系，例如通过typeId与belongingToTypes维护类型映射关系，并提供层级判断等方法。详细属性与方法参见 下文说明。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md) | 标准化数据类型之间存在归属关系，例如JPEG图片类型归属于IMAGE类型。更多预置数据类型参考[UTD预置列表](../../../database/uniform-data-type-list.md)。 下表以枚举形式，列举了常用的标准化数据类型定义。 |

