# DownloadProfileResult（系统接口）

```TypeScript
export interface DownloadProfileResult
```

下载配置文件的结果。

**起始版本：** 18

<!--Device-eSIM-export interface DownloadProfileResult--><!--Device-eSIM-export interface DownloadProfileResult-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## cardId

```TypeScript
cardId: number
```

获取卡ID。

**类型：** number

**起始版本：** 18

<!--Device-DownloadProfileResult-cardId: int--><!--Device-DownloadProfileResult-cardId: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## responseResult

```TypeScript
responseResult: ResultCode
```

操作结果码。

**类型：** [ResultCode](arkts-telephony-esim-resultcode-e-sys.md)

**起始版本：** 18

<!--Device-DownloadProfileResult-responseResult: ResultCode--><!--Device-DownloadProfileResult-responseResult: ResultCode-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

## solvableErrors

```TypeScript
solvableErrors: SolvableErrors
```

可解决的错误。

**类型：** [SolvableErrors](arkts-telephony-esim-solvableerrors-e-sys.md)

**起始版本：** 18

<!--Device-DownloadProfileResult-solvableErrors: SolvableErrors--><!--Device-DownloadProfileResult-solvableErrors: SolvableErrors-End-->

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。
