# @ohos.bluetooth.opp(蓝牙opp模块)

OPP模块提供了使用蓝牙传输文件的功能，包括发送文件、接收文件和获取文件传输进度等。

当前页面仅包含本模块的系统接口。

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { opp } from '@kit.ConnectivityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createOppServerProfile](arkts-connectivity-opp-createoppserverprofile-f-sys.md) | 创建oppServer profile实例。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FileHolder](arkts-connectivity-opp-fileholder-i-sys.md) | 描述发送的文件信息。 |
| [OppServerProfile](arkts-connectivity-opp-oppserverprofile-i-sys.md) | Profile类，使用opp方法之前需要创建该类的实例进行操作，通过[createOppServerProfile()](arkts-connectivity-opp-createoppserverprofile-f-sys.md)方法构造此实例。 |
| [OppTransferInformation](arkts-connectivity-opp-opptransferinformation-i-sys.md) | 描述文件的传输信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DirectionType](arkts-connectivity-opp-directiontype-e-sys.md) | 枚举，文件传输方向。 |
| [TransferResult](arkts-connectivity-opp-transferresult-e-sys.md) | 枚举，文件传输结果。 |
| [TransferStatus](arkts-connectivity-opp-transferstatus-e-sys.md) | 枚举，文件传输状态。 |
<!--DelEnd-->
