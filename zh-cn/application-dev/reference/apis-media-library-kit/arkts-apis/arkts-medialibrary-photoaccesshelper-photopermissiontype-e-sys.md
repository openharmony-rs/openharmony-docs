# PhotoPermissionType（系统接口）

枚举，应用对媒体资源不同访问权限的类型。 包括临时读权限和永久读权限，临时读权限会随着应用的死亡而删除，永久读权限不会。 同一个应用对同一个媒体资源的权限覆盖规则：永久读会覆盖临时读，而临时读不会覆盖永久读。

**起始版本：** 23

<!--Device-photoAccessHelper-enum PhotoPermissionType--><!--Device-photoAccessHelper-enum PhotoPermissionType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## TEMPORARY_READ_IMAGEVIDEO

```TypeScript
TEMPORARY_READ_IMAGEVIDEO = 0
```

临时读权限类型。

**起始版本：** 23

<!--Device-PhotoPermissionType-TEMPORARY_READ_IMAGEVIDEO = 0--><!--Device-PhotoPermissionType-TEMPORARY_READ_IMAGEVIDEO = 0-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## PERSISTENT_READ_IMAGEVIDEO

```TypeScript
PERSISTENT_READ_IMAGEVIDEO = 1
```

永久读权限类型。

**起始版本：** 23

<!--Device-PhotoPermissionType-PERSISTENT_READ_IMAGEVIDEO = 1--><!--Device-PhotoPermissionType-PERSISTENT_READ_IMAGEVIDEO = 1-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

