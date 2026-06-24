# TransferProgress（系统接口）

��Ǩ����Ľ�����Ϣ��

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## failedCount

```TypeScript
failedCount: number
```

��Ǩʧ�ܵ��ļ�������ȡֵ��Χ[0, INT32_MAX]����λ�����������쳣ʱ����-1��

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: TransferState
```

��Ǩ�����״̬��

**类型：** TransferState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## stopReason

```TypeScript
stopReason: TransferStopReason
```

��Ǩֹͣ��ԭ��

**类型：** TransferStopReason

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## successfulCount

```TypeScript
successfulCount: number
```

�Ѱ�Ǩ���ļ�������ȡֵ��Χ[0, INT32_MAX]����λ�����������쳣ʱ����-1��

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## totalCount

```TypeScript
totalCount: number
```

����Ǩ�ļ��ܸ�����ȡֵ��Χ[0, INT32_MAX]����λ�����������쳣ʱ����-1��

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## totalSize

```TypeScript
totalSize: number
```

��Ҫ��Ǩ���ļ��ܴ�С��ȡֵ��Χ[0, INT64_MAX)����λ��Byte�������쳣ʱ����INT64_MAX��

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## transferredSize

```TypeScript
transferredSize: number
```

�Ѱ�Ǩ�����ݴ�С��ȡֵ��Χ[0, INT64_MAX)����λ��Byte�������쳣ʱ����INT64_MAX��

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

