# ErrorType

端云同步失败类型，为枚举类型。

- 当前阶段，同步过程中，当开启无限量使用移动数据网络，移动数据网络和WIFI均不可用时，才会返回NETWORK_UNAVAILABLE；开启无限量使用移动数据网络，若有一种类型网络可用，则能正常同步。  
- 同步过程中，非充电场景下，电量低于10%，完成当前批上行同步后停止同步，返回低电量；  
- 触发同步时，非充电场景下，若电量低于10%，则不允许同步  
- 上行时，若云端空间不足，则文件上行失败，云端无该文件记录。

**起始版本：** 12

<!--Device-cloudSync-enum ErrorType--><!--Device-cloudSync-enum ErrorType-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## RESPONSE_TIME_OUT

```TypeScript
RESPONSE_TIME_OUT = 9
```

云服务超时。

26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ErrorType-RESPONSE_TIME_OUT = 9--><!--Device-ErrorType-RESPONSE_TIME_OUT = 9-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## UNKNOWN_ERROR

```TypeScript
UNKNOWN_ERROR = 10
```

未知错误。

26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ErrorType-UNKNOWN_ERROR = 10--><!--Device-ErrorType-UNKNOWN_ERROR = 10-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

