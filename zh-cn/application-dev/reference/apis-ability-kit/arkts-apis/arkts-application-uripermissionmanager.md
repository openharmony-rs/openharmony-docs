# @ohos.application.uriPermissionManager

URI权限管理模块。用于应用A授权/撤销授权URI给应用B。

**起始版本：** 10

<!--Device-unnamed-declare namespace uriPermissionManager--><!--Device-unnamed-declare namespace uriPermissionManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { uriPermissionManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [grantUriPermission](arkts-ability-uripermissionmanager-granturipermission-f-sys.md#granturipermission) | 授权URI给指定应用，授权成功后目标应用将获得该URI的文件访问权限，目标应用退出后权限将被回收。目标应用使用该URI的方法可以参考[应用文件分享](docroot://file-management/share-app-file.md)。使用callback异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。 |
| [grantUriPermission](arkts-ability-uripermissionmanager-granturipermission-f-sys.md#granturipermission-1) | 授权URI给指定应用，授权成功后目标应用将获得该URI的文件访问权限，目标应用退出后权限将被回收。目标应用使用该URI的方法可以参考[应用文件分享](docroot://file-management/share-app-file.md)。使用Promise异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。 |
| [grantUriPermission](arkts-ability-uripermissionmanager-granturipermission-f-sys.md#granturipermission-2) | 授权URI给指定应用，授权成功后目标应用将获得该URI的文件访问权限，目标应用退出后权限将被回收。目标应用使用该URI的方法可以参考[应用文件分享](docroot://file-management/share-app-file.md)。使用Promise异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。 |
| [grantUriPermissionByKey](arkts-ability-uripermissionmanager-granturipermissionbykey-f-sys.md#granturipermissionbykey) | 通过UDMF数据唯一标识key，将当前应用的文件URI访问权限授权给目标应用，权限将在目标应用退出后回收。使用Promise异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备中返回801错误码。**系统接口**：此接口为系统接口。 |
| [grantUriPermissionByKeyAsCaller](arkts-ability-uripermissionmanager-granturipermissionbykeyascaller-f-sys.md#granturipermissionbykeyascaller) | 通过UDMF数据唯一标识key，将指定应用的文件URI访问权限授权给目标应用，权限将在目标应用退出后回收。使用Promise异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备中返回801错误码。**系统接口**：此接口为系统接口。 |
| [revokeUriPermission](arkts-ability-uripermissionmanager-revokeuripermission-f-sys.md#revokeuripermission) | 撤销授权指定应用的URI。使用callback异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。 |
| [revokeUriPermission](arkts-ability-uripermissionmanager-revokeuripermission-f-sys.md#revokeuripermission-1) | 撤销授权指定应用的URI。使用Promise异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。 |
| [revokeUriPermission](arkts-ability-uripermissionmanager-revokeuripermission-f-sys.md#revokeuripermission-2) | 撤销授权指定应用的URI。使用Promise异步回调。该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备可以调用但是不生效。 |
<!--DelEnd-->

