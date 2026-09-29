# NetworkSearchRealTimeResult（系统接口）

```TypeScript
export interface NetworkSearchRealTimeResult
```

表示手动网络扫描的结果

**起始版本：** 23

<!--Device-radio-export interface NetworkSearchRealTimeResult--><!--Device-radio-export interface NetworkSearchRealTimeResult-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## isFinish

```TypeScript
isFinish: boolean
```

指示网络搜索是否已停止

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-NetworkSearchRealTimeResult-isFinish: boolean--><!--Device-NetworkSearchRealTimeResult-isFinish: boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## networkInfos

```TypeScript
networkInfos: Array<NetworkInformation>
```

网络搜索结果

**类型：** Array&lt;[NetworkInformation](arkts-telephony-radio-networkinformation-i-sys.md)&gt;

**起始版本：** 23

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-NetworkSearchRealTimeResult-networkInfos: Array<NetworkInformation>--><!--Device-NetworkSearchRealTimeResult-networkInfos: Array<NetworkInformation>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。
