# 音频模板错误码

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/errorcode-universal.md)。

## 35000001 音频模板创建失败

**错误信息**

Failed to create the AVMusicTemplate.

**错误描述**

音频模板创建失败。

**可能原因**

1. 媒体增强服务连接失败。

**处理步骤**

1. 可以尝试重启设备。

## 35000002 音频模板控制器创建失败

**错误信息**

Failed to create the AVMusicTemplate controller.

**错误描述**

音频模板控制器创建失败。

**可能原因**

1. 创建controller的参数sessionId不合法。

**处理步骤**

1. 检查sessionId是否为空或者是否有创建过该sessionId对应的AVMusicTemplate的应用。

## 35000003 模板监听未注册

**错误信息**

Template listener not registered.

**错误描述**

模板监听未注册。

**可能原因**

1. template listener 注册失败。

**处理步骤**

1. 检查应用是否正常创建AVMusicTemplate实例。
2. 检查应用内其他业务是否出现了异常。

## 35000004 未注册模板控制器回调

**错误信息**

Controller callback not registered.

**错误描述**

未注册模板控制器回调。

**可能原因**

1. controller callback 注册失败。

**处理步骤**

1. 检查应用是否正常创建AVMusicTemplateController实例。
2. 检查应用内其他业务是否出现了异常。

## 35000005 未注册模板控制器回调

**错误信息**

Controller callback not registered.

**错误描述**

未注册模板控制器回调。

**可能原因**

1. AVMusicTemplate不存在。

**处理步骤**

1. 检查应用是否正常创建AVMusicTemplate实例。
2. 检查应用内其他业务是否出现了异常。

## 35000006 模板控制器不存在

**错误信息**

AVMusicTemplateController does not exist.

**错误描述**

模板控制器不存在。

**可能原因**

1. AVMusicTemplateController不存在。

**处理步骤**

1. 检查应用是否正常创建AVMusicTemplateController实例。
2. 检查应用内其他业务是否出现了异常。

## 35000007 模板控制器已经存在

**错误信息**

AVMusicTemplateController already exists.

**错误描述**

模板控制器已经存在。

**可能原因**

1. AVMusicTemplateController已存在，不需要重复创建

**处理步骤**

1. 在一个应用进程内，一个sessionId对应一个AVMusicTemplateController，不需要重复创建

## 35000008 音频模板管理服务不存在

**错误信息**

AVMusicTemplate Manager services do not exist.

**错误描述**

音频模板管理服务不存在。

**可能原因**

1. 媒体增强服务启动失败。

**处理步骤**

1. 可以尝试重启设备。

## 35000009 音频模板管理服务异常

**错误信息**

AVMusicTemplate Manager services exception.

**错误描述**

音频模板管理服务异常。

**可能原因**

1. 媒体增强服务通信出现异常。

**处理步骤**

1. 检查应用内其他业务是否出现了异常。
2. 可以尝试重启设备。

## 350000010 数据超过了允许的最大传输容量

**错误信息**

The data exceeds the maximum allowable transmission capacity.

**错误描述**

数据超过了允许的最大传输容量。

**可能原因**

1. 传输的数据超过允许传输的最大容量。

**处理步骤**

1. 针对数据量大的数据采用分批传输。

## 350000011 写数据失败，数据不可用

**错误信息**

The data write error, data is invalid.

**错误描述**

写数据失败，数据不可用。

**可能原因**

1. 数据写入失败。

**处理步骤**

1. 检查待传输的数据是否存在不合法的属性或者值。

## 350000012 音频模板错误

**错误信息**

AVMusicTemplate error.

**错误描述**

音频模板错误。

**可能原因**

1. 媒体增强服务内容错误。

**处理步骤**

1. 检查应用是否正常接入api。
2. 检查应用内其他业务是否出现了异常。

