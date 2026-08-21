# 媒体库错误码
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

<!--Del-->
## 23800107 context为空或者无效

**错误信息**

Context is invalid.

**错误描述**

上下文对象不存在或者为空时，方法会返回错误码。

**可能原因**

上下文对象不存在。

**处理步骤**

请检查上下文对象是否可用。
<!--DelEnd-->

## 23800301 系统内部错误

**错误信息**

MediaLibrary inner fail.

**错误描述**

媒体库内部错误。

**可能原因**

1. 创建构造函数引用失败（Failed to create reference）。

2. 实例创建失败（Failed to create instance）。

3. 无法获取undefined值（Failed to get undefined value）。

4. 回调信息获取失败（Failed to get callback info）。

5. 无法将原生对象绑定到JS对象（Failed to bind native object to JavaScript object）。

6. 原生对象解包失败（Failed to unwrap native object）。

7. 布尔值创建失败（Failed to create Boolean value）。

8. int32值获取失败（Failed to get int32 value）。

9. 返回数据初始化失败（Failed to initialize data field）。

10. 返回错误信息初始化失败（Failed to initialize error field）。

11. 获取参数类型失败（Failed to get argument type）。

12. 参数类型校验失败（Failed to check argument type）。

13. 创建PhotoAlbumNapi失败（Failed to create PhotoAlbumNapi）。

14. JS对象添加属性失败（Failed to add property）。

15. 无法获取提取选项（Failed to get fetch option）。

16. 无效的相册列（Invalid fetch columns）。

17. 数组类型校验失败（Failed to check array type）。

18. 获取数组长度失败（Failed to get array length）。

19. 获取数组元素失败（Failed to get array element）。

**处理步骤**

清理后台或重启设备。


## 23800302 打开文件失败

**错误信息**

Failed to open the file.

**错误描述**

媒体库打开文件失败。

**可能原因**

1. 因网络连接问题，无法访问云图库资产（Unable to access cloud images due to network connectivity issues）。

2. 文件系统异常（File system malfunction）。

**处理步骤**

检查网络或文件访问路径。

## 23800151 场景参数校验不通过

**错误信息**

Invalid parameter.

**错误描述**

参数异常。

**可能原因**

1. 必选参数范围不满足要求。

2. 传入的记录已存在。

3. 传入的记录数量超过最大数量。

**处理步骤**

检查参数赋值或者参数长度。

## 23800104 传入参数校验不通过

**错误信息**

Invalid input parameter.

**错误描述**

参数异常。

**可能原因**

参数不在PhotoKeys枚举范围之内。


**处理步骤**

检查传入参数是否在PhotoKeys枚举范围之内。

<!--Del-->
## 23800201 不支持的操作类型

**错误信息**

Unsupported operation type.

**错误描述**

不支持的操作类型。

**可能原因**

1. 当前相册不支持设置传入的AlbumAttribute。

2. 当前AlbumAttribute不支持传入的AlbumOperationType。

3. 存在其他限制。

**处理步骤**

检查设置相册属性的类型及其适用场景，并结合日志定位具体原因。
<!--DelEnd-->

## 23800202 非法场景调用错误

**错误信息**

Invalid call context. Possible causes: 1. The API is called outside the photo browsing scenario. 2. The API is called when isMovingPhotoBadgeShown is already set to true.

**错误描述**

非法场景调用错误。

**可能原因**

1. 在非全图浏览场景下调用该接口。

2. 在已经配置BaseSelectOptions.isMovingPhotoBadgeShown为true的情况下调用该接口。

**处理步骤**

检查接口setMovingPhotoState的使用场景。

<!--Del-->
## 23800203 设备温度过高

**错误信息**

Asset analysis failed due to high temperature.

**错误描述**

设备温度过高导致资产分析失败。

**可能原因**

资产分析会加速设备温度升高，设备温度过高导致资产分析失败。


**处理步骤**

待设备温度恢复正常后再次触发。
<!--DelEnd-->

<!--Del-->
## 23800204 设备电量过低

**错误信息**

Asset analysis failed due to low battery.

**错误描述**

设备电量低导致资产分析失败。

**可能原因**

资产分析会加速设备电量消耗，设备电量低导致资产分析失败。

**处理步骤**

等待设备电量恢复正常后再次触发。
<!--DelEnd-->

<!--Del-->
## 23800205 存储空间不足

**错误信息**

Asset analysis failed due to insufficient storage.

**错误描述**

设备存储空间不足导致资产分析失败。

**可能原因**

资产分析会加速设备存储空间消耗，设备存储空间不足时导致资产分析失败。

**处理步骤**

等待设备存储空间恢复正常后再次触发。
<!--DelEnd-->

<!--Del-->
## 23800206 省电模式已开启

**错误信息**

Asset analysis failed because power saving mode is enabled.

**错误描述**

设备省电模式打开导致资产分析失败。

**可能原因**

资产分析会消耗大量设备电量，当设备处于省电模式时无法进行资产分析。

**处理步骤**

等待用户关闭设备省电模式后再尝试。
<!--DelEnd-->

<!--Del-->
## 23800207 智慧分析服务正在运行

**错误信息**

Asset analysis failed because analysis service is running.

**错误描述**

智慧分析服务正在运行导致资产分析失败。

**可能原因**

媒体智慧分析服务正在运行。

**处理步骤**

等待媒体智慧分析服务运行结束再尝试调用。
<!--DelEnd-->

<!--Del-->
## 23800208 智慧分析开关已关闭

**错误信息**

Asset analysis failed because media analysis is disabled.

**错误描述**

设备智慧分析开关关闭导致资产分析失败。

**可能原因**

设备智慧分析开关关闭，无法进行资产分析。

**处理步骤**

提示用户打开设备智慧分析开关，待用户打开设备智慧分析开关后再重试。
<!--DelEnd-->

<!--Del-->
## 23800209 其他原因导致资产分析失败

**错误信息**

Asset analysis failed due to other reasons.

**错误描述**

其他原因导致资产分析失败。

**可能原因**

1. 任务后台运行冲突。
2. 任务运行超时。

**处理步骤**

等待一段时间后再次触发智慧分析任务。
<!--DelEnd-->
