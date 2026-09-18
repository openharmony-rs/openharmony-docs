# PhotoPermissionType (System API)

Enumerates the types of permissions for accessing media assets.

The permissions include temporary read permission and persistent read permission. The temporary read permission will be removed when the application is dead, while the persistent read permission will not.

For the same media asset and application, the persistent read permission overwrites the temporary read permission. The temporary read permission does not overwrite the persistent read permission.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## TEMPORARY_READ_IMAGEVIDEO

```TypeScript
TEMPORARY_READ_IMAGEVIDEO = 0
```

Temporary read permission.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## PERSISTENT_READ_IMAGEVIDEO

```TypeScript
PERSISTENT_READ_IMAGEVIDEO = 1
```

Persistent read permission.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
