# @ohos.application.uriPermissionManager

The **uriPermissionManager** module provides capabilities for granting the permission on a file to another application and revoking the granted permissions. The file is identified by a uniform resource identifier (URI).

**Since:** 10

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { uriPermissionManager } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [grantUriPermission](arkts-ability-uripermissionmanager-granturipermission-f-sys.md) | Grants the URI permission to an application. If the call is successful, the application obtains the permission to access the file specified by the URI. Once the application exits, the permission will be automatically revoked. For details about how to access the file based on the URI, see [Sharing an Application File](../../../file-management/share-app-file.md). This API uses an asynchronous callback to return the result. |
| [grantUriPermission](arkts-ability-uripermissionmanager-granturipermission-f-sys.md) | Grants the URI permission to an application. If the call is successful, the application obtains the permission to access the file specified by the URI. Once the application exits, the permission will be automatically revoked. For details about how to access the file based on the URI, see [Sharing an Application File](../../../file-management/share-app-file.md). This API uses a promise to return the result. |
| [grantUriPermission](arkts-ability-uripermissionmanager-granturipermission-f-sys.md) | Grants the URI permission to an application. If the call is successful, the application obtains the permission to access the file specified by the URI. Once the application exits, the permission will be automatically revoked. For details about how to access the file based on the URI, see [Sharing an Application File](../../../file-management/share-app-file.md). This API uses a promise to return the result. |
| [grantUriPermissionByKey](arkts-ability-uripermissionmanager-granturipermissionbykey-f-sys.md) | Grants the URI access permission of the current application to the target application through the unique key of the Unified Data Management Framework (UDMF) data. The permission will be revoked after the target application exits. This API uses a promise to return the result. This API can be properly called only on phones, 2-in-1 devices, and tablets. If it is called on other device types, error code 801 is returned. **System API**: This is a system API. |
| [grantUriPermissionByKeyAsCaller](arkts-ability-uripermissionmanager-granturipermissionbykeyascaller-f-sys.md) | Grants the URI access permission of the specified application to the target application through the unique key of the Unified Data Management Framework (UDMF) data. The permission will be revoked after the target application exits. This API uses a promise to return the result. This API can be properly called only on phones, 2-in-1 devices, and tablets. If it is called on other device types, error code 801 is returned. **System API**: This is a system API. |
| [revokeUriPermission](arkts-ability-uripermissionmanager-revokeuripermission-f-sys.md) | Revokes the URI permission from an application. This API uses an asynchronous callback to return the result. |
| [revokeUriPermission](arkts-ability-uripermissionmanager-revokeuripermission-f-sys.md) | Revokes the URI permission from an application. This API uses a promise to return the result. |
| [revokeUriPermission](arkts-ability-uripermissionmanager-revokeuripermission-f-sys.md) | Revokes the URI permission from an application. This API uses a promise to return the result. |
<!--DelEnd-->
