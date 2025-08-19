# HUKS错误码

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 12000001 该子功能不支持（特性）

**错误信息**

The ``${messageInfo}`` is not supported.

**可能原因**

支持API，但是不支持API内部某些子特性（功能），如算法参数。

**处理步骤**

调整API参数，使用可替代可支持的参数。

## 12000002 缺少密钥算法参数
**错误信息**

Failed to obtain the ``${messageInfo}``. It is not set in ParamSet.

**可能原因**

使用密钥时缺少相关参数。

**处理步骤**

1. 查看errorMessage确认缺少的密钥参数。
2. 添加对应的正确的密钥参数。

## 12000003 无效的密钥算法参数

**错误信息**

Invalid ``${messageInfo}``.

**可能原因**

使用密钥时无效相关参数。

**处理步骤**

1. 查看errorMessage确认无效的密钥参数名。
2. 修改对应的密钥参数。

## 12000004 文件错误

**错误信息**

可能为以下的其中一种：

- Insufficient storage space.
- Invalid file size.
- Failed to ``${messageInfo}``.


**可能原因**

文件操作错误。

**处理步骤**

1. 查看是否磁盘空间已经写满、文件系统是否有其他异常。
2. 清理磁盘。

## 12000005 进程通信错误

**错误信息**

可能为以下的其中一种：

- Failed to get messages from IPC.
- IPC ``${messageInfo}``.

**可能原因**

进程通信错误。

**处理步骤**

查看错误信息，排查是否进程IPC通信问题。

## 12000006 算法库操作失败

**错误信息**

Crypto engine error.

**可能原因**

该错误码表示算法库操作失败，可能原因如下。

1. 算法库加解密错误，可能是密文数据不对。
2. 密钥参数不正确。

**处理步骤**

1. 排查密文数据是否正确。
2. 排查加解密参数是否正确。

## 12000007 密钥访问失败 - 密钥已失效

**错误信息**

This credential is invalidated permanently.

**可能原因**

该错误码表示密钥访问失败 - 密钥已失效，可能原因如下。

1. 该密钥设置了清除密码失效的用户认证访问控制属性，清除过设备密钥导致密钥失效。
2. 该密钥设置了新录入生物特征失效的用户认证访问控制属性，由于录入过新的指纹或人脸导致该密钥失败。

**处理步骤**

1. 确认日志是哪种方式导致的认证不通过。
2. 如果使用了正确参数，但是失效控制导致认证不通过，则该密钥已经无法使用。

## 12000008 密钥访问失败 - 密钥认证失败

**错误信息**

The authentication token verification failed.

**可能原因**

该密钥设置了用户认证访问控制属性，由于challenge参数不正确导致无法通过认证。

**处理步骤**

1. 检查userIAM认证的challenge参数组装是否正确。
2. 如果是challenge参数不正确导致，则修改正确的组装方式，使用huks生成challenge组装，并传入userIAM重新认证。

## 12000009 密钥访问失败 - 密钥访问超时

**错误信息**

This authentication token timed out.

**可能原因**

该密钥设置了用户认证访问控制属性，由于使用时间窗timeout导致无法通过认证。

**处理步骤**

如果是timeout导致不正确，则重新触发密钥init并重新认证，使得认证时间和密钥init时间小于设置的timeout时间。

## 12000010 密钥操作会话数已达上限

**错误信息**

The number of key operation sessions has reached the limit.

**可能原因**

同时使用huks进行密钥会话操作的调用方（同应用或者跨应用）过多，已经达到上限（15个）。

**处理步骤**

1. 检查同应用内部是否同时存在多个密钥会话操作（init)，存在则修改避免同时调用。
2. 如不存在上述情形，则可能是其它应用同时调用多个会话，通过等待其它应用释放会话后再使用。

## 12000011 目标对象不存在

**错误信息**

The entity does not exist.

**可能原因**

该别名对应的密钥不存在。

**处理步骤**

1. 检查密钥别名是否拼写错误。
2. 检查改密钥别名对应的密钥是否生成成功。

## 12000012 外部错误

**错误信息**

Device environment or input parameter abnormal.

**可能原因**

外部的硬件出错，文件错误等。

**处理步骤**

拿错误码与日志在社区反馈。

## 12000013 密钥设置生物访问控制时，待绑定的凭据不存在

**错误信息**

The credential does not exist.

**可能原因**

密钥绑定PIN、指纹、人脸时，未录入相关凭据。

**处理步骤**

录入相关凭据，或更改绑定凭据类型。

## 12000014 内存不足

**错误信息**

可能为以下的其中一种：

- Insufficient memory.
- Malloc failed.

**可能原因**

系统内存不足，或出参缓存太小。

**处理步骤**

1. 开发者释放部分内存或重启。
2. 检查传入的出参缓存大小。

## 12000015 调用其他系统服务失败

**错误信息**

Failed to obtain the ``${messageInfo}`` information via UserIAM.

**可能原因**

其他系统服务未启动。

**处理步骤**

开发者等待一段时间后尝试再次触发调用。

## 12000017 同名密钥已存在

**错误信息**

The key with same alias is already exist.

**可能原因**

指定了不覆写同名密钥，但同名密钥已存在。

**处理步骤**

请根据业务需要检查是否应该覆写同名密钥。

## 12000018 输入参数非法

**错误信息**

The input parameter is invalid.

**可能原因**

1. 必选参数没有传入。

2. 参数类型错误（Type Error）。

3. 空参数错误（Null Argument Error）。

4. 参数值范围错误（Value Range Error）。

**处理步骤**

请检查必选参数是否传入，或者传入的参数类型是否错误。对于参数校验失败原因，请阅读参数规格约束，按照可能原因进行排查。

