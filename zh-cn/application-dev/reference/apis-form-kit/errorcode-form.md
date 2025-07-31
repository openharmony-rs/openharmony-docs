# 卡片错误码

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 16500050 进程间通信失败

**错误信息**

IPC connection error.

**错误描述**

系统内为执行当前请求进行必要进程间通信时出错，系统会报此错误码。

**可能原因**

当调用接口传入的入参过大时，进程间通信对数据校验失败。

**处理步骤**

确认入参是否过长。

## 16500060 连接服务失败

**错误信息**

Service connection error.

**错误描述**

系统内为执行当前请求连接必要服务完成请求时出错，系统会报此错误码。

**可能原因**

当前服务繁忙，或服务出现异常。

**处理步骤**

待服务重启后重试。

## 16500100 获取卡片配置信息失败

**错误信息**

Failed to obtain configuration information.

**错误描述**

系统内为执行当前请求获取卡片相关配置信息时出错，系统会报此错误码。

**可能原因**

卡片相关配置信息字段缺失或非法。

**处理步骤**

确认并验证卡片配置信息正确性。

## 16501000 内部功能错误

**错误信息**

An internal functional error occurred.

**错误描述**

系统内为执行当前请求时发生内部错误，系统会报此错误码。

**可能原因**

系统业务内部执行异常。

**处理步骤**

待系统重启后重试。

## 16501001 卡片ID不存在

**错误信息**

The ID of the form to be operated does not exist.

**错误描述**

当请求所指定的卡片ID未找到或不存在时，系统会报此错误码。

**可能原因**

指定卡片ID不存在，或传入无效卡片ID。

**处理步骤**

检查卡片ID的有效性。

## 16501002 卡片数量达到上限

**错误信息**

The number of forms exceeds the maximum allowed.

**错误描述**

当卡片数量已达到上限时继续请求添加卡片，系统会报此错误码。

**可能原因**

当前卡片数量已达到上限，但仍继续请求添加卡片。

**处理步骤**

删除不必要卡片后再请求添加。

## 16501003 无法操作指定卡片

**错误信息**

The form cannot be operated by the current application.

**错误描述**

当前应用无法对指定卡片进行操作时，系统会报此错误码。

**可能原因**

指定的卡片非当前应用所有。

**处理步骤**

1. 检查传入卡片ID所有权。
2. 升级权限为SystemApp。

## 16501006 卡片渲染服务连接失败

**错误信息**

FormRenderService is stopped. Connect to the service again.

**错误描述**

无法连接卡片渲染服务时，系统会报此错误码。

**可能原因**

服务繁忙。

**处理步骤**

服务繁忙，请稍后重试。

## 16501007 卡片不可信

**错误信息**

Form is not trust.

**错误描述**

卡片不受信任。

**可能原因**

卡片代码存在死循环、内存泄漏等问题导致系统异常。

**处理步骤**

检查卡片代码的死循环、内存泄漏等问题。

<!--Del-->
## 16501008 等待卡片加桌超时

**错误信息**

Waiting for the form addition to the desktop timed out.

**错误描述**

发送卡片加桌请求后，等待卡片加桌超时，系统会报此错误码。

**可能原因**

服务繁忙。

**处理步骤**

服务繁忙，请稍后重试。
<!--DelEnd-->

## 16501010 设置互动卡片背景图失败

**错误信息**

Failed to set the live form background image.

**错误描述**

设置互动卡片背景图时，传入背景图资源无效，系统会报此错误码。

**可能原因**

背景图资源无效。

**处理步骤**

检查传入的背景图资源是否有效。

## 16501011 卡片不支持调用当前接口

**错误信息**

The form can not support this operation.

**错误描述**

卡片不支持调用当前接口，系统会报此错误码。

**可能原因**

普通卡片发起互动卡片动效请求，或者当前互动卡片配置错误。

**处理步骤**

检查当前卡片对应[互动卡片配置项sceneAnimationParams](../../form/arkts-ui-widget-configuration.md#sceneanimationparams标签)是否正确。

## 16501012 卡片尺寸信息错误

**错误信息**

The form host uses an incorrect dimension.

**错误描述**

卡片使用方传入错误的卡片尺寸。

**可能原因**

指定卡片尺寸未配置，或传入无效卡片尺寸。

**处理步骤**

检查入参卡片尺寸是否在[FormDimension](js-apis-app-form-formInfo.md#formdimension)和[supportDimensions](../../form/arkts-ui-widget-configuration.md#配置文件字段说明)配置列表。

## 2293761 内部服务错误

**错误信息**

Some internal server error occurs.

**错误描述**

系统执行当前请求时发生内部错误。

**可能原因**

系统业务内部执行异常。

**处理步骤**

1. 重启系统后重试。
2. 重启后仍旧失败，请提[在线工单](https://developer.huawei.com/consumer/cn/support/feedback/#)获取帮助。

## 2293766 包管理获取请求的应用包名不存在

**错误信息**

The requested bundle name does not exist.

**错误描述**

系统执行获取请求的应用包名不存在，该错误属于内部错误。

**可能原因**

包管理获取请求方的bundleName时出错，属于系统业务内部执行异常。

**处理步骤**

1. 重启系统后重试。
2. 重启后仍旧失败，请提[在线工单](https://developer.huawei.com/consumer/cn/support/feedback/#)获取帮助。

## 2293767 无效参数

**错误信息**

Invalid params received on operating form.

**错误描述**

接口调用时存在无效入参。

**可能原因**

1. 未传入必选参数。
2. 参数类型错误。
3. 参数数量错误。
4. 空参数错误，比如传入空字符串（''）。
5. 参数格式错误。
6. 参数值错误。输入参数与[app.json5](../../quick-start/app-configuration-file.md)、[配置卡片的配置文件](../../form/arkts-ui-widget-configuration.md)的对应配置需要保持一致。

**处理步骤**

按照可能原因进行排查，确认必选参数是否传入、传入的参数类型是否错误等。

## 2293795 获取包管理服务失败

**错误信息**

Get bms rpc failed.

**错误描述**

获取包管理服务失败。

**可能原因**

系统业务内部执行异常。

**处理步骤**

1. 重启系统后重试。
2. 重启后仍旧失败，请提[在线工单](https://developer.huawei.com/consumer/cn/support/feedback/#)获取帮助。

## 2293798 获取卡片管理服务失败

**错误信息**

Get fms rpc failed.

**错误描述**

获取卡片管理服务失败。

**可能原因**

系统业务内部执行异常。

**处理步骤**

1. 重启系统后重试。
2. 重启后仍旧失败，请提[在线工单](https://developer.huawei.com/consumer/cn/support/feedback/#)获取帮助。

## 2293802 获取系统能力管理服务失败

**错误信息**

Get system manager service failed.

**错误描述**

获取系统能力管理服务失败。

**可能原因**

系统业务内部执行异常。

**处理步骤**

1. 重启系统后重试。
2. 重启后仍旧失败，请提[在线工单](https://developer.huawei.com/consumer/cn/support/feedback/#)获取帮助。
