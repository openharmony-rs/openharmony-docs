# @ohos.data.uniformTypeDescriptor(标准化数据定义与描述)

本模块对标准化数据类型进行了抽象定义与描述，用于统一表示和管理各类数据类型的层级与归属关系（如JPEG归属于IMAGE、IMAGE归属于MEDIA等），便于跨模块/跨应用的一致化数据交互。详细设计原理参见 [UTD预置列表](../../../database/uniform-data-type-list.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace uniformTypeDescriptor--><!--Device-unnamed-declare namespace uniformTypeDescriptor-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformTypeDescriptor } from '@kit.ArkData';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getTypeDescriptor(标准化数据定义与描述)](arkts-arkdata-uniformtypedescriptor-gettypedescriptor-f.md) | 按给定的标准化数据类型ID查询并返回对应的标准化数据类型描述类对象。 |
| [getTypeDescriptor(标准化数据定义与描述)](arkts-arkdata-uniformtypedescriptor-gettypedescriptor-f.md) | 按给定的标准化数据类型ID查询并返回对应的标准化数据类型描述类对象。 |
| [getUniformDataTypeByFilenameExtension(标准化数据定义与描述)](arkts-arkdata-uniformtypedescriptor-getuniformdatatypebyfilenameextension-f.md) | 根据给定的文件后缀名和所归属的标准化数据类型查询标准化数据类型ID，若有多个符合条件的标准化数据类型ID，则返回第一个。 |
| [getUniformDataTypeByMIMEType(标准化数据定义与描述)](arkts-arkdata-uniformtypedescriptor-getuniformdatatypebymimetype-f.md) | 根据给定的MIME类型和所归属的标准化数据类型查询标准化数据类型ID，若有多个符合条件的标准化数据类型ID，则返回第一个。 |
| [getUniformDataTypesByFilenameExtension(标准化数据定义与描述)](arkts-arkdata-uniformtypedescriptor-getuniformdatatypesbyfilenameextension-f.md) | 根据给定的文件后缀名和所归属的标准化数据类型查询标准化数据类型ID列表。 |
| [getUniformDataTypesByMIMEType(标准化数据定义与描述)](arkts-arkdata-uniformtypedescriptor-getuniformdatatypesbymimetype-f.md) | 根据给定的MIME类型和所归属的标准化数据类型查询标准化数据类型ID列表。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [registerTypeDescriptors(标准化数据定义与描述)](arkts-arkdata-uniformtypedescriptor-registertypedescriptors-f-sys.md) | 注册一组标准化数据类型到系统中。使用Promise异步回调。注册成功后，标准化数据类型将被系统管理，可通过UDMF框架在其他应用或设备间共享和识别。 |
| [unregisterTypeDescriptors(标准化数据定义与描述)](arkts-arkdata-uniformtypedescriptor-unregistertypedescriptors-f-sys.md) | 从系统中注销一个或多个标准化数据类型。使用Promise异步回调。注销后，该数据类型将不再被系统识别，依赖该数据类型的数据可能无法正常处理，请确保在注销前已清理相关数据依赖。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [TypeDescriptor(标准化数据定义与描述)](arkts-arkdata-uniformtypedescriptor-typedescriptor-c.md) | 标准化数据类型的描述类，它包含了一些属性和方法用于描述标准化数据类型自身以及和其他标准化数据类型之间的归属与层级关系，例如通过typeId与belongingToTypes维护类型映射关系，并提供层级判断等方法。详细属性与方法参见 下文说明。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [UniformDataType(标准化数据定义与描述)](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md) | 标准化数据类型之间存在归属关系，例如JPEG图片类型归属于IMAGE类型。更多预置数据类型参考[UTD预置列表](../../../database/uniform-data-type-list.md)。 下表以枚举形式，列举了常用的标准化数据类型定义。 |

