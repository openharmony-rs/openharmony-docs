# Before You Start
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

An application needs to obtain a PhotoAccessHelper instance before accessing or modifying the media data in an album. User personal data is involved in the PhotoAccessHelper module. Therefore, the application must also apply for the read and write permissions from the user. Unless otherwise specified, the APIs of the PhotoAccessHelper module are used in **pages/index.ets** of the project or other customized .ets files.

## Obtaining a PhotoAccessHelper Instance

The application must use the [Context](../../application-models/application-context-stage.md) and the [getPhotoAccessHelper](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper) API to obtain a PhotoAccessHelper instance for accessing and modifying media data in albums, such as images and videos.

**How to Develop**

1. Import the photoAccessHelper module.
2. Call **getUIContext().getHostContext()** to obtain the application context.
3. Obtain a PhotoAccessHelper instance.

<!-- @[photo_access_helper_preparation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MediaLibraryKit/ResourceUsageSample/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { common } from '@kit.AbilityKit';

// The photoAccessHelper instance obtained here is a global object. Unless otherwise specified, the object obtained here is used in subsequent operations in this document. If an undefined error is reported, add the code snippet here.
// Obtain the context from the component and ensure that the return value of this.getUiContext().getHostContext() is UIAbilityContext.
@Entry
@Component
struct Index {
  @State outputText: string = 'Supported formats:\n';

  build() {
    Row() {
      Button('example').onClick(async () => {
        let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
        let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
      }).width('100%')
    }
    .height('90%')
  }
}
```

## Requesting Permissions

Before requesting the permissions for the PhotoAccessHelper module, ensure that the [basic principles for using permissions](../../security/AccessToken/app-permission-mgmt-overview.md#basic-principles-for-using-permissions) are met. The following permissions are required.

| Permission                        | Description                                      | Authorization Mode  |
| ------------------------------ | ------------------------------------------ | ---------- |
| ohos.permission.READ_IMAGEVIDEO     | Allows an application to read images and videos in the media library.| user_grant |
| ohos.permission.WRITE_IMAGEVIDEO    | Allows an application to read and write images and videos in the media library.| user_grant |
| ohos.permission.MEDIA_LOCATION    | Allows an application to access geographical locations in the user's media file.| user_grant |

All of the preceding permissions use the user_grant authorization mode, which means that after the corresponding permissions are configured in the [module.json5 configuration file](../../../application-dev/quick-start/module-configuration-file.md), the application must use the [abilityAccessCtrl.requestPermissionsFromUser](../../reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#requestpermissionsfromuser9) API to check whether the current user has granted the permissions. If yes, the application can access and manipulate the data. Otherwise, display a dialog box to request user authorization.

**How to Develop**
<!--RP1-->
1. The **ohos.permission.READ_IMAGEVIDEO** and **ohos.permission.WRITE_IMAGEVIDEO** permissions are restricted permissions. Before using them, you must additionally declare the required permissions in the Access Control List (ACL). For details, see [Requesting Restricted Permissions](../../security/AccessToken/declare-permissions-in-acl.md).
2. [Declare the required permissions in the **module.json5** file](../../security/AccessToken/declare-permissions.md).
3. [Request user authorization](../../security/AccessToken/request-user-authorization.md).
<!--RP1End-->

> **NOTE**
>
> Even if the user has granted the permission, the permission will still be checked before an API protected by the permission is called. The permission granted status should not be persisted, because the user can revoke the permission through the system application **Settings**.
