# 数据共享错误码
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @woodenarow-->
<!--Designer: @woodenarow; @xuelei3-->
<!--Tester: @chenwan188; @logic42-->
<!--Adviser: @ge-yafang-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

##  15700000 内部错误

**错误信息**

Inner error.

**错误描述**

内部错误。

**可能原因**

优先查看错误日志，通过日志可以详细了解错误原因，主要有以下几种：
1. 内部状态异常。
2. 错误地使用接口。
3. 权限配置错误。
4. 系统错误，如空指针、内存不足、数据服务异常重启、I/O错误、IPC异常、JS引擎异常等。

**处理步骤**

1. 开发者排查是否存在对象关闭后再使用。
2. 开发者排查是否按接口文档正确使用接口。
3. 开发者排查权限配置是否正确。
4. 尝试重试，如果依然无法解决，可以提示用户重启应用、升级应用或升级设备版本。

## 15700010 创建DataShareHelper异常

**错误信息**

The DataShareHelper fails to be initialized.

**错误描述**

创建DataShareHelper工具类异常时，系统会产生此错误码。

**可能原因**

1. 创建DataShareHelper时，接口createDataHelper的入参uri不正确。
2. 创建DataShareHelper时，接口createDataHelper的入参context不正确。
3. 创建DataShareHelper时，客户端从后台拉起DataShareExtension时，未配置后台拉起权限。

**处理步骤**

1. 咨询DataShare服务端提供者，获取正确的uri路径。
2. DataShare仅支持Stage模型，检查context是否为Stage模型的context。
3. 检查客户端是否有数据的读或者写权限，具体步骤如下：<br/>
    (1) 找到数据提供者包名，在uri的path里面找，例如：uri = "datashareproxy://com.acts.ohos.data.datasharetest/test"。<br/>
    (2) 根据包名找到配置，例如：bm dump --bundle-name com.acts.ohos.data.datasharetest，在里面找到DataShareExtension的配置，确认数据访问者是否有readPermission或writePermission中配置的权限。

## 15700011 uri不存在

**错误信息**

The URI does not exist.

**错误描述**

添加/删除模板异常或者开启/关闭静默访问传入的uri格式或者路径错误时，系统会产生此错误码。

**可能原因**

1. 入参uri路径不正确。
2. 入参uri格式不正确。

**处理步骤**

咨询DataShare服务端提供者，获取正确的uri路径。

## 15700012 数据区不存在

**错误信息**

The data area does not exist.

**错误描述**

数据更新异常时，系统会产生此错误码。

**可能原因**

数据更新异常时，接口publish的入参bundleName不正确。

**处理步骤**

咨询DataShare服务端提供者，获取正确的bundleName。

## 15700013 DataShareHelper实例被关闭

**错误信息**

The DataShareHelper instance is already closed.

**错误描述**

DataShareHelper实例被关闭后，继续使用该实例会产生此错误码。

**可能原因**

调用close接口关闭了DataShareHelper实例后，继续使用该实例。

**处理步骤**

重新创建DataShareHelper实例，再进行使用。

## 15700014 配置共享参数错误

**错误信息**

The parameter format is incorrect or the value range is invalid.

**错误描述**

1. 参数格式错误。

2. 参数值超出取值范围。

**可能原因**

1. URI长度超过256字节。

2. proxyData的value长度超过4096字节。

3. 接口传入的URI数组长度超过32。

4. 接口传入的proxyData数组长度超过32。

5. URI格式校验失败。

**处理步骤**

1. 检查接口传入的URI数组或者proxyData数组中是否有URI的长度超过256字节。

2. 检查接口传入的proxyData数组中是否有proxyData的value长度超过4096字节。

3. 检查接口传入的URI数组的长度是否超过32。

4. 检查接口传入的proxyData数组的长度是否超过32。

5. 检查接口传入的URI数组或者proxyData数组中的URI是否满足格式校验：<br/>
    URI的固定格式为`"datashareproxy://{bundleName}/{path}"`，其中bundleName为配置发布方应用的bundleName，path可随意填写。