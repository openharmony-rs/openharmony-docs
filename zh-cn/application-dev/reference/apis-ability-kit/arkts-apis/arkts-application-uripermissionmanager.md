# @ohos.application.uriPermissionManager

URI权限管理模块。用于应用A授权/撤销授权URI给应用B。

**起始版本：** 10

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[grantUriPermission](arkts-ability-uripermissionmanager-granturipermission-f-sys.md#grantUriPermission-1) | 授权URI给指定应用，授权成功后目标应用将获得该URI的文件访问权限，目标应用退出后权限将被回收。目标应用使用该URI的方法可以参考<br/>[应用文件分享](../../../../file-management/share-app-file.md)。使用callback异步回调。<br/>该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 当应用拥有ohos.permission.PROXY_AUTHORIZATION_URI权限时, 可以授权不属于自身但具有访问权限的URI。如果不具备该权限，则仅支持授权属于自身的URI。<br/>&gt;<br/>&gt; - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证<br/>&gt; 其功能。<br/> |
| <!--DelRow-->[grantUriPermission](arkts-ability-uripermissionmanager-granturipermission-f-sys.md#grantUriPermission-2) | 授权URI给指定应用，授权成功后目标应用将获得该URI的文件访问权限，目标应用退出后权限将被回收。目标应用使用该URI的方法可以参考<br/>[应用文件分享](../../../../file-management/share-app-file.md)。使用Promise异步回调。<br/>该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 当应用拥有ohos.permission.PROXY_AUTHORIZATION_URI权限时, 可以授权不属于自身但具有访问权限的URI。如果不具备该权限，则仅支持授权属于自身的URI。<br/>&gt;<br/>&gt; - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证<br/>&gt; 其功能。<br/> |
| <!--DelRow-->[grantUriPermission](arkts-ability-uripermissionmanager-granturipermission-f-sys.md#grantUriPermission-3) | 授权URI给指定应用，授权成功后目标应用将获得该URI的文件访问权限，目标应用退出后权限将被回收。目标应用使用该URI的方法可以参考<br/>[应用文件分享](../../../../file-management/share-app-file.md)。使用Promise异步回调。<br/>该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 当应用拥有ohos.permission.PROXY_AUTHORIZATION_URI权限时, 可以授权不属于自身但具有访问权限的URI。如果不具备该权限，则仅支持授权属于自身的URI。<br/>&gt;<br/>&gt; - 该接口支持给分身应用授权，需要指定目标应用的应用包名和分身索引。<br/>&gt;<br/>&gt; - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证<br/>&gt; 其功能。<br/> |
| <!--DelRow-->[grantUriPermissionByKey](arkts-ability-uripermissionmanager-granturipermissionbykey-f-sys.md#grantUriPermissionByKey-1) | 通过UDMF数据唯一标识key，将当前应用的文件URI访问权限授权给目标应用，权限将在目标应用退出后回收。使用Promise异步回调。<br/>该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备中返回801错误码。<br/>**系统接口**：此接口为系统接口。<br/> |
| <!--DelRow-->[grantUriPermissionByKeyAsCaller](arkts-ability-uripermissionmanager-granturipermissionbykeyascaller-f-sys.md#grantUriPermissionByKeyAsCaller-1) | 通过UDMF数据唯一标识key，将指定应用的文件URI访问权限授权给目标应用，权限将在目标应用退出后回收。使用Promise异步回调。<br/>该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备中返回801错误码。<br/>**系统接口**：此接口为系统接口。<br/> |
| <!--DelRow-->[revokeUriPermission](arkts-ability-uripermissionmanager-revokeuripermission-f-sys.md#revokeUriPermission-1) | 撤销授权指定应用的URI。使用callback异步回调。<br/>该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 允许应用撤销自身获得的其他应用URI权限，或授权给其他应用的URI权限。<br/>&gt;<br/>&gt; - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证<br/>&gt; 其功能。<br/> |
| <!--DelRow-->[revokeUriPermission](arkts-ability-uripermissionmanager-revokeuripermission-f-sys.md#revokeUriPermission-2) | 撤销授权指定应用的URI。使用Promise异步回调。<br/>该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 允许应用撤销自身获得的其他应用URI权限，或授权给其他应用的URI权限。<br/>&gt;<br/>&gt; - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证<br/>&gt; 其功能。<br/> |
| <!--DelRow-->[revokeUriPermission](arkts-ability-uripermissionmanager-revokeuripermission-f-sys.md#revokeUriPermission-3) | 撤销授权指定应用的URI。使用Promise异步回调。<br/>该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 允许应用撤销自身获得的其他应用URI权限，或授权给其他应用的URI权限。<br/>&gt;<br/>&gt; - 该接口支持撤销授权给分身应用的URI权限，需要指定目标应用的应用包名和分身索引。<br/>&gt;<br/>&gt; - 因URI处理涉及编解码，传入的URI需要使用[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)接口获取。对于应用自行拼接的URI，系统无法保证<br/>&gt; 其功能。<br/> |

