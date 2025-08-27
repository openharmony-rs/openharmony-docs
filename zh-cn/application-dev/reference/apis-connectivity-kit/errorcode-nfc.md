# NFC错误码

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 3100101 开关NFC异常

**错误信息**

The NFC state is abnormal in the service.

**错误描述**

NFC服务内部执行NFC打开或关闭异常。

**可能原因**

1. 和NFC服务建立通信异常。
2. NFC芯片通信异常。

**处理步骤**

重新执行打开或关闭NFC或重启设备尝试。

## 3100201 NFC服务读写Tag错误

**错误信息**

The tag running state is abnormal in the service.

**错误描述**

NFC服务执行Tag业务逻辑遇到错误。

**可能原因**
1. Tag参数值和实际调用函数要求不匹配。
2. Tag操作时，NFC状态是关闭的。
3. Tag操作前，已经处在断开状态。
4. Tag芯片返回错误状态或响应超时。
5. 和NFC服务没有建立绑定关系，无法调用接口。

**处理步骤**
1. 检查NFC参数是否和所调用接口匹配。
2. 判断NFC是关闭状态时，提示打开NFC。
3. 先调用连接，再执行读写操作。
4. 重新触碰读取卡片。
5. 退出应用后，重新读取卡片。

## 3100202 应用状态错误

**错误信息**

The element state is invalid.

**错误描述**

接口调用时，所属应用读卡的页面状态错误，页面不在前台。

**可能原因**
所属应用读卡的页面状态错误，页面不在前台。

**处理步骤**
只允许进入应用前台的页面调用该接口。

## 3100203 接口调用顺序错误

**错误信息**

The off() API can be called only when the on() has been called.

**错误描述**

必须在接口on()已经被调用之后，才允许调用接口off()。

**可能原因**
应用程序的前台页面没有调用on()接口，就直接调用off()接口。

**处理步骤**
应用程序的前台页面先执行on()接口，在页面退出时调用off()接口。

## 3100204 NFC芯片I/O异常

**错误信息**

The tag I/O operation failed.

**错误描述**

NFC Tag I/O操作失败。

**可能原因**
NFC Tag不支持所执行的读写操作。

**处理步骤**
应用程序根据业务场景进行异常处理或提示。

## 3100205 NFC标签状态异常

**错误信息**

The tag leaves the field.

**错误描述**

NFC标签已经离场。

**可能原因**
NFC标签已离开nfc设备感应范围。

**处理步骤**
重新将标签靠近nfc读卡设备。

## 3100301 NFC卡模拟状态异常

**错误信息**

Card emulation running state is abnormal in service.

**错误描述**

NFC服务执行卡模拟业务逻辑遇到错误。

**可能原因**
1. 卡模拟时NFC状态是关闭的。
2. NFC芯片返回错误状态或响应超时。

**处理步骤**
1. 判断NFC是关闭状态时，提示打开NFC。
2. 提示关开NFC，重新初始化硬件。

## 3200101 有源NFC标签状态异常

**错误信息**

Connected NFC tag running state is abnormal in service.

**错误描述**

执行有源NFC Tag业务逻辑遇到错误。

**可能原因**
1. 有源NFC Tag参数值和实际调用函数要求不匹配。
2. 有源NFC Tag芯片返回错误状态或响应超时。

**处理步骤**
1. 检查有源NFC Tag参数是否和所调用接口匹配。
2. 重新触碰读取卡片。
