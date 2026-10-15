# HydrateProgressState（系统接口）

```TypeScript
enum HydrateProgressState
```

枚举进度的状态。

**起始版本：** 26.0.1

<!--Device-cloudDiskManager-enum HydrateProgressState--><!--Device-cloudDiskManager-enum HydrateProgressState-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## CANCELLED

```TypeScript
CANCELLED = 3
```

由用户取消，崩溃，或应用程序放弃。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HydrateProgressState-CANCELLED = 3--><!--Device-HydrateProgressState-CANCELLED = 3-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## COMPLETED

```TypeScript
COMPLETED = 2
```

水合作用完成。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HydrateProgressState-COMPLETED = 2--><!--Device-HydrateProgressState-COMPLETED = 2-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## IN_PROGRESS

```TypeScript
IN_PROGRESS = 1
```

水合物正在进行中。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HydrateProgressState-IN_PROGRESS = 1--><!--Device-HydrateProgressState-IN_PROGRESS = 1-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## PENDING

```TypeScript
PENDING = 0
```

已经创建了任务，但是FFRT worker还没有被调度。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HydrateProgressState-PENDING = 0--><!--Device-HydrateProgressState-PENDING = 0-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。
