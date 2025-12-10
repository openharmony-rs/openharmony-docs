# 统一数据管理框架错误码
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 20400001 设置已存在，若要重新配置请删除现有的共享选项

**错误信息**

Settings already exist. To reconfigure, remove the existing sharing options.

**错误描述**

应用程序设置拖拽通道数据可使用的范围时，将要设置的信息在数据库中已存在。

**可能原因**

调用[setAppShareOptions](js-apis-data-unifiedDataChannel.md#unifieddatachannelsetappshareoptions14)重复设置拖拽通道数据可使用的范围时，系统会产生此错误码。

**处理步骤**

先调用[removeAppShareOptions](js-apis-data-unifiedDataChannel.md#unifieddatachannelremoveappshareoptions14)清除当前拖拽通道数据可使用的范围后，再调用[setAppShareOptions](js-apis-data-unifiedDataChannel.md#unifieddatachannelsetappshareoptions14)重新设置。

<!--Del-->
## 20400002 标准化数据类型描述符格式错误

**错误信息**

The format of one or more type descriptors are invalid.

**错误描述**

标准化数据类型描述符列表的格式错误。

**可能原因**

调用[registerTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#uniformtypedescriptorregistertypedescriptors22)时，传入的标准化数据类型描述符列表格式错误，具体可能原因包括：

1. 标准化数据类型描述符列表为空、其中元素个数超过50，或当前应用注册的标准化数据类型描述符数量总计超过200。

2. 任意一个标准化数据类型描述符格式错误，具体可能原因包括：

    - typeId为空字符串、长度超过127，或包含非字母、数字、中划线（-）、点号（.）字符。
    
    - belongingToTypes为空列表、其中元素个数超过50，或其中包含空字符串、或任意元素长度超过127。

    - description、referenceURL或iconFile长度超过255。

    - filenameExtensions的元素个数超过50，或包含空字符串，或任意元素长度超过127，或任意元素首字符不是点号。

    - mimeTypes的元素个数超过50，或包含空字符串，或任意元素长度超过127。

**处理步骤**

请检查传入的标准化数据类型描述符列表，确保格式正确，参考上文可能原因里对应的规格约束进行排查修改。

## 20400003 标准化数据类型描述符内容错误

**错误信息**

The content of one or more type descriptors are invalid.

**错误描述**

标准化数据类型描述符列表的内容错误。

**可能原因**

[registerTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#uniformtypedescriptorregistertypedescriptors22)传入的标准化数据类型描述符内容错误，可能原因有：

1. 任意一个标准化数据类型描述符中，typeId与已注册的类型ID重复。

2. 任意一个标准化数据类型描述符中，typeId不是以当前应用的包名开头。

3. 任意一个标准化数据类型描述符中，belongingToTypes包含不属于[预置数据类型](../../database/uniform-data-type-list.md)或本次注册的其他标准化数据类型的typeId。

4. 标准化数据类型之间存在循环依赖关系，belongingToTypes内容错误。

**处理步骤**

请检查传入的标准化数据类型描述符列表，确保内容正确，参考上文可能原因里对应的规格约束进行排查修改。

## 20400004 标准化数据类型ID列表错误

**错误信息**
 
One or more typeIds are invalid or do not exist.

**错误描述**

待注销的标准化数据类型ID列表包含无效的ID。

**可能原因**

调用[unregisterTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#uniformtypedescriptorunregistertypedescriptors22)时，传入的标准化数据类型ID列表错误，具体可能原因有：

1. 标准化数据类型ID列表为空、或其中元素个数超过50。

2. 任意一个标准化数据类型ID无效，具体可能原因包括：

    - 标准化数据类型ID对应的标准化数据类型在系统中未注册。

    - 标准化数据类型ID不是以当前应用的包名开头。

    - 标准化数据类型ID对应的标准化数据类型未通过接口[registerTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#uniformtypedescriptorregistertypedescriptors22)注册。

**处理步骤**

请检查传入的标准化数据类型ID列表，参考上文可能原因里对应的规格约束进行排查修改。
<!--DelEnd-->