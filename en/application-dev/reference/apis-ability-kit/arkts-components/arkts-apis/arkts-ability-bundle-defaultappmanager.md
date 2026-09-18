# @ohos.bundle.defaultAppManager

The module provides APIs to query whether the current application is the default application of a specific type.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.DefaultApp

## Modules to Import

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [isDefaultApplication](arkts-ability-defaultappmanager-isdefaultapplication-f.md) | Checks whether this application is the default application of a system-defined application type or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses an asynchronous callback to return the result. |
| [isDefaultApplication](arkts-ability-defaultappmanager-isdefaultapplication-f.md) | Checks whether this application is the default application of a system-defined application type or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses a promise to return the result. |
| [isDefaultApplicationSync](arkts-ability-defaultappmanager-isdefaultapplicationsync-f.md) | Checks whether this application is the default application of a system-defined application type or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API returns the result synchronously. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getDefaultApplication](arkts-ability-defaultappmanager-getdefaultapplication-f-sys.md) | Obtains the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses an asynchronous callback to return the result. |
| [getDefaultApplication](arkts-ability-defaultappmanager-getdefaultapplication-f-sys.md) | Obtains the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses an asynchronous callback to return the result. |
| [getDefaultApplication](arkts-ability-defaultappmanager-getdefaultapplication-f-sys.md) | Obtains the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses a promise to return the result. |
| [getDefaultApplicationCandidates](arkts-ability-defaultappmanager-getdefaultapplicationcandidates-f-sys.md) | Obtains the list of applications that can be set as the default application of the specified type. Currently, only the **BROWSER** type is supported. Applications that have not been granted the ohos.permission.DEFAULT_WEB_BROWSER permission are excluded from the result. |
| [getDefaultApplicationSync](arkts-ability-defaultappmanager-getdefaultapplicationsync-f-sys.md) | Obtains the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API returns the result synchronously. |
| [resetDefaultApplication](arkts-ability-defaultappmanager-resetdefaultapplication-f-sys.md) | Resets the default application for a user based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses an asynchronous callback to return the result. |
| [resetDefaultApplication](arkts-ability-defaultappmanager-resetdefaultapplication-f-sys.md) | Resets the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses an asynchronous callback to return the result. |
| [resetDefaultApplication](arkts-ability-defaultappmanager-resetdefaultapplication-f-sys.md) | Resets the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses a promise to return the result. |
| [resetDefaultApplicationSync](arkts-ability-defaultappmanager-resetdefaultapplicationsync-f-sys.md) | Resets the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API returns the result synchronously. |
| [setDefaultApplication](arkts-ability-defaultappmanager-setdefaultapplication-f-sys.md) | Sets the default application for a user based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses an asynchronous callback to return the result. To set an application as the default browser, the target application must have been granted the ohos.permission.DEFAULT_WEB_BROWSER permission. Otherwise, error 18000001 is returned. [since 26.1.0] |
| [setDefaultApplication](arkts-ability-defaultappmanager-setdefaultapplication-f-sys.md) | Sets the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses an asynchronous callback to return the result. To set an application as the default browser, the target application must have been granted the ohos.permission.DEFAULT_WEB_BROWSER permission. Otherwise, error 18000001 is returned. [since 26.1.0] |
| [setDefaultApplication](arkts-ability-defaultappmanager-setdefaultapplication-f-sys.md) | Sets the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API uses a promise to return the result. To set an application as the default browser, the target application must have been granted the ohos.permission.DEFAULT_WEB_BROWSER permission. Otherwise, error 18000001 is returned. [since 26.1.0] |
| [setDefaultApplicationForAppClone](arkts-ability-defaultappmanager-setdefaultapplicationforappclone-f-sys.md) | Sets an application clone as the default application of the specified type. This API returns the result synchronously. To set an application as the default browser, the target application must have been granted the ohos.permission.DEFAULT_WEB_BROWSER permission. Otherwise, error 18000001 is returned. [since 26.1.0] |
| [setDefaultApplicationSync](arkts-ability-defaultappmanager-setdefaultapplicationsync-f-sys.md) | Sets the default application based on a system-defined application type, a file type that complies with the media type format (either specified by **type** or **subtype**), or a [uniform data type](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md). This API returns the result synchronously. To set an application as the default browser, the target application must have been granted the ohos.permission.DEFAULT_WEB_BROWSER permission. Otherwise, error 18000001 is returned. [since 26.1.0] |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md) | Enumerates the default application types. |
