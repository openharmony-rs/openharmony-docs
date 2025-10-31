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

## 20400002 标准化数据类型描述符格式错误

**错误信息**

The format of one or more type descriptors are invalid.

**错误描述**

标准化数据类型描述符的格式不符合要求。

**可能原因**

调用[registerTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#registerTypeDescriptors)注册标准化数据类型时，传入的参数格式错误，具体可能原因包括：

1. ​​typeId​​为空、长度超过127，或包含非字母、数字、中划线（-）、点号（.）字符。

2. ​​belongingToTypes​​为空、长度超过50，或其中包含空字符串、或单个元素长度超过127。

3. description​​、​​referenceURL​​ 或 ​​iconFile​​ 长度超过255。

4. filenameExtensions或mimeTypes长度超过50，或其中包含空字符串、或单个元素长度超过127。

5. filenameExtensions中单个元素首字母不是点号。

**处理步骤**

请检查传入的参数格式是否错误。对于参数格式校验失败，阅读参数规格约束，按照可能原因进行排查。

## 20400003 标准化数据类型描述符内容错误

**错误信息**

The content of one or more type descriptors are invalid.

**错误描述**

标准化数据类型描述符内容错误。

**可能原因**

调用[registerTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#registerTypeDescriptors)注册标准化数据类型时，参数内容错误，具体可能原因有：

1. ​​typeId​​不是唯一的，与已注册的类型ID冲突。

2. typeId​​的前缀与当前应用的包名不匹配。

3. belongingToTypes​​中包含不存在的标准化数据类型ID。

4. 存在循环依赖关系。

**处理步骤**

请检查传入的参数内容是否满足业务逻辑要求。针对内容校验失败的情况，请参考相关参数的规格约束，逐一排查上述可能原因。

## 20400004 标准化数据类型ID列表错误。

**错误信息**

One or more typeIds are invalid or do not exist.

**错误描述**

待注销的标准化数据类型ID列表中包含无效或不存在的类型ID。

**可能原因**

调用[unregisterTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#unregisterTypeDescriptors)注销标准化数据类型时，传入的参数存在以下问题：

1. typeId对应的标准化数据类型不存在。

2. typeId的前缀与当前应用的包名不匹配。

3. typeId对应的标准化数据类型不是由接口[registerTypeDescriptors](js-apis-data-uniformTypeDescriptor-sys.md#registerTypeDescriptors)注册的。

**处理步骤**

请检查传入的待注销类型ID列表，确保所有 typeId 均为有效且已注册的类型。
