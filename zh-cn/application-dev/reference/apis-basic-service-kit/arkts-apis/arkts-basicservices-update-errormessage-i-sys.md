# ErrorMessage（系统接口）

错误信息。

**起始版本：** 9

<!--Device-update-export interface ErrorMessage--><!--Device-update-export interface ErrorMessage-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## errorCode

```TypeScript
errorCode: number
```

错误码，用于标识具体的错误类型。通过errorCode可快速定位升级失败的原因（如权限错误201、参数错误401、IPC错误11500104等），从而采取针对性的处理措施。

使用场景：在升级失败事件(EVENT_UPGRADE_FAIL)回调中，通过errorCode判断失败原因，进行相应的错误处理或提示用户。建议结合errorMessage进行详细的错误分析和处理。

**类型：** number

**起始版本：** 9

<!--Device-ErrorMessage-errorCode: int--><!--Device-ErrorMessage-errorCode: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## errorMessage

```TypeScript
errorMessage: string
```

错误描述文本，用于提供错误的详细说明信息。errorMessage提供了错误的具体描述（如'Permission denied.、'Parameter verification failed'等），帮助开发者理解错误原因和进行调试。

使用场景：在错误处理时，可将errorMessage用于日志记录、错误提示展示或错误分析。建议结合errorCode一起使用，errorCode提供错误类型，errorMessage提供详细说明。

**类型：** string

**起始版本：** 9

<!--Device-ErrorMessage-errorMessage: string--><!--Device-ErrorMessage-errorMessage: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

