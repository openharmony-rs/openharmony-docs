# ExtBundleStats（系统接口）

系统应用或系统服务的空间占用详情。

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## businessName

```TypeScript
businessName: string
```

系统应用包名或系统服务名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## flag

```TypeScript
flag: boolean
```

系统应用或系统服务的空间占用是否需要在“设置-存储”界面单独展示。true表示单独显示，false表示不单独显示。
该值为false时，空间占用会被归并到businessName指定的应用中。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: number
```

系统应用或系统服务的空间占用大小，单位Byte。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

