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

1. 弹窗发生内部错误，请重试（Internal error in dialog, please retry）。

2. 弹窗返回结果缺少必要参数，系统内部错误（Dialog result missing required parameters, system internal error）。

3. 参数不是数组类型（Parameter is not an array type）。

4. 数组无效或不是数组类型（Failed to get array length）。

5. 服务端内部错误（Server returned an invalid argument error）。

6. 回调处理失败，系统内部错误，可能原因：1. 数据库异常；2. 文件系统异常；3. IPC 通信超时，请重试（Callback processing failed, system internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs）。

7. 数据服务初始化失败，可能原因：1. 数据库异常；2. IPC 通信超时，请检查 context 是否正确初始化并重试（Data service initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please check if the context is properly initialized and retry）。

8. 系统内部错误，可能原因：1. 数据库异常；2. 文件系统异常；3. IPC 通信超时，请重试并检查日志（System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs）。

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

1. 参数不是数组类型（The parameter is not an array）。

2. indexSet 参数为 undefined（IndexSet is null or undefined）。

3. 索引超出对象范围，必须在 [0, count) 范围内（The index is out of range, must be within [0, count)）。

4. 不支持的结果集类型，必须为有效的 FetchResType 枚举值（The FetchResType is not supported, must be a valid FetchResType enum value）。

5. 场景参数验证失败（Scenario parameter verification failed）。

6. 需要一个或两个参数（One or two parameters are required）。

7. 第一个参数不是对象类型或第二个参数不是函数类型（The first parameter is not an object or the second parameter is not a function）。

8. 对象不是有效对象（The object is not a valid instance to get asset object）。

9. PhotoAsset 不是有效的 PhotoAsset 对象（The The PhotoAsset is not a valid PhotoAsset object）。

10. 检查是否为隐藏或回收资源（Check whether it is a hidden or recycled album）。

11. 检查是否不是图片或视频类型（Check whether it is not a MEDIA_TYPE_IMAGE or MEDIA_TYPE_VIDEO）。

12. 普通资源无效（Ordinary assets invalid）。

13. 注册已达上限（Registration has reached the limit）。

14. 为 callback 创建引用失败（Failed to create a reference for the callback）。

15. 同一 callback 已注册过该资源的监听（The listener for this resource has been registered with the same callback）。

16. 从照片资源获取 fileId 失败（Failed to get fileId from photo asset）。

17. 单个资源监听数已达上限（≥ 200）（Failed to get file asset instance）。

18. 对象无效（The object is not a valid instance）。

19. 参数类型无效（The parameter type is invalid）。

20. album 参数无效，传入的 Album 不是通过 photoAccessHelper.getAlbums() 或 createAlbum() 获取的有效实例（Album object is not a valid object）。

21. 普通相册无效（Ordinary album invalid）。

22. 创建 callback 引用失败（Failed to create callback reference）。

23. 从未注册过任何观察者（No observer has ever been registered）。

24. 观察者列表为空（Observer list is empty）。

25. 参数数量不正确，应为 1 或 2 个参数（The number of parameters is invalid, expected 1 or 2 parameters）。

26. bundleName 参数必须是有效的非空 string 类型（The bundleName parameter must be a non-empty string）。

27. config 参数必须是 object 类型（The config parameter must be an object）。

28. supportedHighResolution 属性必须是 boolean 类型（The supportedHighResolution attribute must be a boolean）。

29. supportedMimeType 属性必须是 string 数组类型（The supportedMimeType attribute must be an array of strings）。

30. 数组包含不支持的 MIME 类型，仅支持 image/jpeg 和 image/png（The supportedMimeType array contains unsupported MIME types, only image/jpeg and image/png are supported）。

31. supportedMimeTypes 数组大小超过限制（去重后最多 2 个）（The supportedMimeTypes array size exceeds the limit (max 2 after deduplication)）。

32. 系统内部错误，可能原因：1. 数据库异常；2. 文件系统异常；3. IPC 通信超时，请重试并检查日志（System internal error, possible causes: 1. Database exception; 2. File system exception; 3. IPC timeout. Please retry and check logs.）。

**处理步骤**

检查参数赋值或者参数长度。

## 23800101 文件不存在

**错误信息**

File Real Path isn't existed.

**错误描述**

文件不存在。

**可能原因**

1. fileUri指向的文件不存在。

2. fileUri指向的文件已删除。

3. URI格式无法解析到有效真实路径。

## 23800102 显示名称无效

**错误信息**

Invalid display name.

**错误描述**

显示名称无效。

**可能原因**

1. 显示名称包含非法字符。

2. 显示名称长度超出限制。

3. 显示名称为空。

**处理步骤**

请检查显示名称是否符合规格要求。

## 23800103 资产uri无效

**错误信息**

Invalid asset URI.

**错误描述**

资产uri无效。

**可能原因**

1. 资产uri格式不正确。

2. 资产uri指向的资产不存在。

3. 资产uri已被删除或失效。

**处理步骤**

请检查资产uri是否有效，确保通过合法接口获取uri。

## 23800104 传入参数校验不通过

**错误信息**

Invalid input parameter. Possible causes:<br>1. The provided member must be a property name of PhotoKey.

**错误描述**

参数异常。

**可能原因**

参数不在[PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys)枚举范围之内。


**处理步骤**

检查传入参数是否在PhotoKeys枚举范围之内。

<!--Del-->
## 23800201 不支持的操作类型

**错误信息**

Unsupported operation type. Possible causes:<br>1. Repeatedly started;<br>2. System is busy, please try again later;<br>3. Unsupported AlbumAttribute for the album;<br>4. Unsupported AlbumOperationType for the AlbumAttribute;<br>5. Other operation limit.

**错误描述**

不支持的操作类型。

**可能原因**

1. 当前相册不支持设置传入的[AlbumAttribute](js-apis-photoAccessHelper-sys.md#albumattribute)。

2. 当前[AlbumAttribute](js-apis-photoAccessHelper-sys.md#albumattribute)不支持传入的[AlbumOperationType](js-apis-photoAccessHelper-sys.md#albumoperationtype)。

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

2. 在已经配置[BaseSelectOptions.isMovingPhotoBadgeShown](arkts-apis-photoAccessHelper-class.md#baseselectoptions)为true的情况下调用该接口。

**处理步骤**

检查接口[setMovingPhotoState](ohos-file-PhotoPickerComponent.md#setmovingphotostate23)的使用场景。

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
